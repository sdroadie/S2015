# Object files
objs := scanner.o parser.tab.o

# Libraries to link with executable calculator program
LDLIBS := -lfl

# Program to run instead of lex
LEX := flex

# Program to run instead of yacc
YACC := bison

# Flags to pass to YACC program
YFLAGS := -d

CXXFLAGS := -std=c++0x

# Link objects and build executable
Proj1: $(objs)
	$(CXX) $(CXXFLAGS) $(objs) $(LDLIBS) -o $@
	mv $@ ../
	cd ../

# Compile scanner to object file
scanner.o: scanner.cc parser.tab.hh

# Compile parser to object file
parser.tab.o: parser.tab.cc

# Build scanner implementation from flex file
scanner.cc: scanner.l
	$(LEX) -o $@ $<

# Build *.tab.* files from bison file
parser.tab.hh parser.tab.cc: parser.yy
	$(YACC) $(YFLAGS) $< 

# Remove compilation artifacts
.PHONY: clean
clean:
	-$(RM) *.o *.tab.* scanner.cc Proj1
