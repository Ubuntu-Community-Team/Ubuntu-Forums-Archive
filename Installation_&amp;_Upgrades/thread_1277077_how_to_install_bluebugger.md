---
title: "how to install bluebugger"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by ramazani on 2009-09-27
hi i was wondering if anyone could explain this to me 

CC 		= gcc
FLAGS 		= -O2
D_FLAGS         = -g -Wall # -pedantic #-DDEBUG
LIBS		= -lbluetooth
PROG		= bluebugger
SOURCES		= bb.c bt.c at.c wrap.c debug.c

.PHONY:		default clean
.c.o:
		${CC} ${FLAGS} ${D_FLAGS} -c $< 

default:	${SOURCES}
		${CC} ${FLAGS} ${D_FLAGS} -o ${PROG} ${SOURCES} ${LIBS}

clean:
		rm -f ${PROG} *.o *~

how should i understand this

---

