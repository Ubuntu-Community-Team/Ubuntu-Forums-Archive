---
title: "LG Laptop freeze with all 2.26.* kernels"
date: 2008-06-18
forum: Hardware
---

### Post by kilgoretroutjr on 2008-06-18
Hi,

my LG LW75 laptop freezes with 2.26.* kernels. 2.6.22-14-generic runs flawlessly, so I'm stuck with that version now.
The freeze occurs with 2.26.16 as well as .17 .18 and .19.
The steps to reproduce the freeze:
- start up with any of the 2.26 kernels
- start gnome-terminal
- type "cd /usr/" and press TAB twice for autocomplete (works with any other directory)
- the system is hard frozen. No mouse, no Ctrl-Alt-BackSpace, no SysRq combinations, no answer on ping or ssh.

The above way is a reliable method to reproduce the freeze, but it happens often, even when not using gnome-terminal.

I've tried with and without compiz, no difference. What makes it even stranger (and leads me to think about kernel incompatibilities) the freeze occurs in recovery mode as well. If I boot up in recovery mode, and try to autocomplete a directory name with TAB, i usually end up with a frozen system.

Attached is my lspci and lshw output.

Thanks for any help.

---

