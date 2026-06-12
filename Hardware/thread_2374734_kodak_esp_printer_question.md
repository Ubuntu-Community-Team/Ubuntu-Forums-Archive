---
title: "kodak esp printer question"
date: 2017-10-18
forum: Hardware
---

### Post by William_Labbett on 2017-10-18
Hi, I'm trying to compile c2-esp27 so I can use my esp1.2 printer.

I'm getting undeefined references to functions in the C standard library.

It appears the linker isn't linking the C libraries to me with my limited knowledge.

The only things in the makefile I can find to do with linker flags are the lines

LDFLAGS = 
LIBOBJS = 
LIBS = -ljbig -lz -lcupsimage -lcupsfilters -lcups 

Does anyone have any good suggestions??

/* EDIT */

No it must a problem with the headers in the code or a problem with missing headers.

---

