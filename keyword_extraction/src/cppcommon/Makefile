CC = g++
CCOPT = -Wall -c
LINK = g++
LINKOPT = 
PACK = ar
PACKOPT = rc
DOPACK = $(PACK) $(PACKOPT) $@ $?
DOLINK = $(LINK) $(LINKOPT) -o $@ $?

CMLIB = cmlib.a

%.o: %.cpp
	$(CC) $(CCOPT) $<


all: $(CMLIB)

$(CMLIB): file_functs.o io_functs.o str_functs.o vec_functs.o logger.o
	$(DOPACK) 
	
file_functs.test: file_functs.cpp file_functs.h
	g++ -o $@ $< -DTEST_FILE_FUNCTS
io_functs.test: io_functs.cpp io_functs.h
	g++ -o $@ $< -DTEST_IO_FUNCTS
str_functs.ut: str_functs.cpp str_functs.h
	g++ -o $@ $< -DTEST_STR_FUNCTS
vec_functs.test: vec_functs.cpp vec_functs.h vec_functs.tcc
	g++ -o $@ $< -DTEST_VEC_FUNCTS

logger.ut: logger.cpp logger.h file_functs.cpp file_functs.h
	g++ -o $@ $< file_functs.cpp -DUNIT_TEST

clean:
	rm -f *.test *.ut *.o $(CMLIB)
