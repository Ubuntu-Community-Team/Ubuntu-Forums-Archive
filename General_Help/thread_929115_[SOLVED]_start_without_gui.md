---
title: "[SOLVED] start without gui"
date: 2008-09-24
forum: General Help
---

### Post by Woody1987 on 2008-09-24
I have ubuntu server 8.04 installed on my server. I currently administer it remotely through ssh and vnc. When i installed it i wasnt comfortable using only a terminal, so i installed gnome and used vnc. Now i have gotten to the point that i can do most of what i need through a terminal using ssh. I would like to be able to boot up my server and not have gnome start but leave it at the command line. I dont want to remove gnome as i may still need to vnc in to do the odd thing. How do i do this?

---

### Post by Sef on 2008-09-24
At the login screen, go into options.  There is an option for setting it to start without a gui.

---

### Post by sisco311 on 2008-09-24
to disable the graphical login:
```
sudo update-rc.d -f gdm remove
```
to enable it:
```
sudo update-rc.d gdm defaults 13 01
```

or:
```
sudo sysv-rc-conf
```
and disable gdm in runlevel 2, 3, 4 and 5.
use the arrow keys to move around, space to select/deselect and q to quit

to start the x session from the virtual terminal:
```
startx
```

---

### Post by DGortze380 on 2008-09-24
or just alt+f2 at the login screen (mine actually needs ctrl+alt+f2 wiht an apple keyboard, try it out).

---

### Post by Woody1987 on 2008-09-25
I did 
```
sudo update-rc.d -f gdm remove
```

That seemed to work, i can no longer use remote desktop but ssh is still working so im assuming its running at a low run level (1 maybe, i dont know), but when i type

```
startx
```

i get

```
X: user not authorized to run the X server, aborting.
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
```

So i tried sudo startx, thinking i need administrative permissions but i then get

```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Data 2.6.24-19-server #1 SMP Wed Aug 20 18:43:06 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 25 18:56:21 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ddc" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


xinit:  unexpected signal 2.
```


Whats happening?

---

### Post by sisco311 on 2008-09-25
try:
```
sudo /etc/init.d/gdm start
```

---

### Post by Woody1987 on 2008-09-25
> try:
Code:

sudo /etc/init.d/gdm start



That worked, thankyou

---

