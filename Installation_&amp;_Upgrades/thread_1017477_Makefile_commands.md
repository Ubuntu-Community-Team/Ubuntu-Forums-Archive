---
title: "Makefile commands"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by reldon on 2008-12-21
Can somebody please help me understand how this makefile command works?..

all: $(TARGETS)

%.d: %.c
	set -e; $(CC) -I. -M $(CPPFLAGS) $< \
	| sed 's/\($*\)\.o[ :]*/\1.o $@ : /g' > $@; \
	[ -s $@ ] || rm -f $@
ifneq ($(MAKECMDGOALS),clean)
include $(SRCS:.c=.d)
endif

Thanks,

Rel

---

