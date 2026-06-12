---
title: "nam-1.11 error MouseWheel"
date: 2008-09-29
forum: General Help
---

### Post by 7majko7 on 2008-09-29
Hi,
I have a problem with nam 1.11.
When I execute "nam" i have this result:

[root@localhost ns-allinone-2.29]# nam
nam:
[code omitted because of length]
: no event type or button # or keysym
    while executing
"bind Listbox <MouseWheel> {
%W yview scroll [expr {- (%D / 120) * 4}] units
}"
    invoked from within
"if {[string equal [tk windowingsystem] "classic"]
|| [string equal [tk windowingsystem] "aqua"]} {
bind Listbox <MouseWheel> {
%W yview scroll [expr {..."


I tried to solve it by following nam's official guide in the FAQ:

Problem: Tcl source code dump on various
platforms, the end of which complains about unknown event
"MouseWheel".

Solution:
This is because in macro LIB in nam's Makefile, -L/usr/lib -lz is
placed before -ltcl8.0, etc. Thus if there is an older version of
libtcl8.0.a or libtcl8.0.so in /usr/lib, nam is messed up.  Edit nam Makefile and put that -lz stuff at the end of the LIB macro.


but this is for nam-1.0a6.

How can I solve it?

Thank you
Maurizio

---

### Post by Joeb454 on 2008-09-30
Moved to General Help

---

### Post by 7majko7 on 2008-10-01
Nobody knows how can I solve it? :cry::cry:

---

