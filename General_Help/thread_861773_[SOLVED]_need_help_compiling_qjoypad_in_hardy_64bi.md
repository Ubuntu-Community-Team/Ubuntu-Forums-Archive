---
title: "[SOLVED] need help compiling qjoypad in hardy 64bit"
date: 2008-07-16
forum: General Help
---

### Post by tjwoosta on 2008-07-16
so im trying to install qjoypad on hardy 64bit (the qjoypad site only has a .deb for i386)

the problem is that i have never really had to compile anything before (theres basically a .deb for everything)

i downloaded the .tar.gz (first in the list) from here
[http://qjoypad.sourceforge.net/#download]("http://qjoypad.sourceforge.net/#download")

i did ./config and this is the message i get
> 
tj@tj-laptop:~/qjoypad-3.4.1/src$ ./config
./config: line 51: qmake: command not found

Configuring QJoyPad installation...
------------------------------------------------------------

Device directory: /dev/input
-- Devices will be looked for in:
     /dev/input/js0
     /dev/input/js1
     etc.

Prefix directory: /usr/local
-- Files to be installed in:
     /usr/local/bin
     /usr/local/doc
     /usr/local/share/pixmaps
	 
---------------------------------------------------------
If these settings are okay, go ahead and run 'make' and
then 'make install'.

To make changes, run ./config --help for details.

tj@tj-laptop:~/qjoypad-3.4.1/src$ 


then, this is what happens when i try to run "make"
> 
tj@tj-laptop:~/qjoypad-3.4.1/src$ make
make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.
tj@tj-laptop:~/qjoypad-3.4.1/src$ 


also i get the same exact message when i try "make install"

---

### Post by tjwoosta on 2008-07-17
the daily bump

(before i head off to work)

---

### Post by tjwoosta on 2008-07-18
bump

---

### Post by Potatoj316 on 2008-07-18
In a terminal type ```
sudo aptitude install build-essential
``` then compiling again

But thats probably not going to help, it looks like you already have that package installed.

---

### Post by tjwoosta on 2008-07-18
yup..

i did already have it


do you happen to know any other dependencies i might need?

---

### Post by easybake on 2008-09-11
> **tjwoosta said:**
> yup..

i did already have it


do you happen to know any other dependencies i might need?

I just came across this and to fix the problem you have all you have to do is open synaptic and install libqt3-mt-dev.

Make and make install should work after that. I had the same problem. But qjoypad ends up using almost 90% of my cpu.

---

