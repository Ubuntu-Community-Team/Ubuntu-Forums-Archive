---
title: "weirdnesses in grep, sort, etc."
date: 2008-07-26
forum: General Help
---

### Post by vb@vsbe.com on 2008-07-26
I just intalled 8.04 on my laptop, I'm using gnome.

I notice that some tools I transferred from another linux installation don't quite work as expected. here are two most glaring examples:

The old system:

[COLOR="Blue"]mma-k: ~ 89 > cat sample
#

#
# Processor support
#
# CONFIG_6xx is not set
# CONFIG_PPC_85xx is not set
# CONFIG_PPC_8xx is not set
# CONFIG_40x is not set
CONFIG_44x=y
ma-k: ~ 90 > cat sample1
line3
line1
Line2

ma-k: ~ 91 > egrep -v '^(#|\S*$)' ~/sample
CONFIG_44x=y
ma-k: ~ 92 > cat sample1|sort

Line2
line1
line3
ma-k: ~ 93 > egrep -V
egrep (GNU grep) 2.5.1

Copyright 1988, 1992-1999, 2000, 2001 Free Software Foundation, Inc.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

ma-k: ~ 94 > sort --version
sort (GNU coreutils) 5.93
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.

Written by Mike Haertel and Paul Eggert.
[/COLOR]

The new system (8.04):

[COLOR="Green"]pl-p: ~ 188 > cat sample
#

#
# Processor support
#
# CONFIG_6xx is not set
# CONFIG_PPC_85xx is not set
# CONFIG_PPC_8xx is not set
# CONFIG_40x is not set
CONFIG_44x=y
pl-p: ~ 189 > cat sample1
line3
line1
Line2

pl-p: ~ 190 > egrep -v '^(#|\S*$)' ~/sample
pl-p: ~ 191 > cat sample1|sort

line1
Line2
line3
pl-p: ~ 192 > egrep -V
GNU grep 2.5.3

Copyright (C) 1988, 1992-2002, 2004, 2005  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

pl-p: ~ 193 > sort --version
sort (GNU coreutils) 6.10
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Mike Haertel and Paul Eggert.[/COLOR]


so, the sort on the new system is case insensitive, and regular expression syntax is different - what gives?!

Any hints will be highly appreciated,
tia
/vb

---

