---
title: "Alps laptop mouse not working (Ubuntu 8.04)"
date: 2008-08-28
forum: General Help
---

### Post by djsbriscoe on 2008-08-28
Hi,
I have just installed Ubuntu 8.04.1 (kernel 2.6.24-19 generic) on a Clevo 2200t laptop computer.
On completion of the installation the mouse does not work at all.
The mouse pointer is stuck in the middle of the screen doing nothing.
The mouse is an Alps pointing device(touchpad).
On issuing the command 

$ sudo cat /proc/bus/input/devices

I get the following (shortened) output:

I:BUS=0017 VENDOR=0001 PRODUCT=0001 VERSION=0100
N:NAME="MACINTOSH MOUSE BUTTON EMULATION"
P:PHYS=
S:SYSFS=/DEVICES/VIRTUAL/INPUT/INPUT0
U:UNIQ=
H:HANDLERS=MOUSE0 EVENT0
B:EV=7
B:KEY=70000 0 0 0 0 0 0 0 0
B:REL=3

I would like to post my xorg.conf file but I don't know where to find it and how to copy it to a flppy disk using linux commands.

Could someone please give me instructions on how to do this and what I should be looking for. I can then edit any files I need to to get a generic mouse input working.
Any clues on what I can do next?
Thanks

David.

---

### Post by djsbriscoe on 2011-03-25
Hi,
I got the mouse working a while back but I can't remember how I did it. Can someone please help. There are a few guides on the ubuntu websites but I don tknow where to start.
Any help appreciated.

David

P.S I'm using Karmic now, but the problem still persists.

---

