# Makefile for echo client and server

CXX=			g++ $(CCFLAGS)

ECHO-SERVER=		server/echo-server.o server/inet-server.o server/server.o server/logger.o
ECHO-CLIENT=		client/echo-client.o client/inet-client.o client/client.o client/logger.o
OBJS =			$(ECHO-SERVER) $(ECHO-CLIENT)

LIBS=

CCFLAGS= -g

all:	echo-server echo-client

echo-server:$(ECHO-SERVER)
	$(CXX) -o server $(ECHO-SERVER) $(LIBS)

echo-client:$(ECHO-CLIENT)
	$(CXX) -o client $(ECHO-CLIENT) $(LIBS)

clean:
	rm -f $(OBJS) $(OBJS:.o=.d)

realclean:
	rm -f $(OBJS) $(OBJS:.o=.d) server client


# These lines ensure that dependencies are handled automatically.
%.d:	%.cc
	$(SHELL) -ec '$(CC) -M $(CPPFLAGS) $< \
		| sed '\''s/\($*\)\.o[ :]*/\1.o $@ : /g'\'' > $@; \
		[ -s $@ ] || rm -f $@'

include	$(OBJS:.o=.d)