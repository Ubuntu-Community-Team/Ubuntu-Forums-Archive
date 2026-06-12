---
title: "long gnome startup time"
date: 2009-07-24
forum: Hardware
---

### Post by toffifeemann on 2009-07-24
hey guys,

i know there has been a similar thread before, but i tried all the solutions offered and had no luck...
i have a brand new samsung n110 with 2gb ram...
so the thing is, that after i login, i get a blank screen for what feels like ages (at least 20s) and i can only see my mousecourser which im able to move
after that gnome starts
i did the cat /var/log/gdm/\:0.log command and this is what i get:

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux mimi 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
Build Date: 09 April 2009 02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 24 12:22:44 2009
(==) Using config file: "/etc/X11/xorg.conf"
get fences failed: -1
param: 6, val: 0
get fences failed: -1
param: 6, val: 0
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning: Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
> Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning: Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
> Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server


now i have no clue about what to do with it, so i was wondering if someone had an idea how to fix the problem
(of long startup time)

---

