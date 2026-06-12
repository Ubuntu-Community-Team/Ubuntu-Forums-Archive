---
title: "cannot kill xserver"
date: 2010-07-10
forum: Hardware
---

### Post by nu-ub on 2010-07-10
First, let me say that I am completely new at this- last week i did not even know Ubuntu existed.  I am trying to install a Nvidia driver on my Sony VAIO VPCL113FX (driver NVIDIA-Linux-x86-256.35.run).  The file is on my desktop and it is checked to run as executable.  I CTL-ALT-F1, change directory to Desktop and run command:

sudo /etc/init.d/gdm stop 

to kill the X server.

First it says tha tbecause it was converted tosomething that I should run command 

service gdm stop  or something.

That does not work because it says I cannot access org.gnome.DisplayManager because of security reasons.  If I try to run

sudo sh ./Nvidia...

anyway I get an blue screen error message saying that I am still running an X server.

Thus, it appears to me that my method of killing the X server is not working.  I have researched this for about 3 hours now and cannot find a solution.  Cansomeone please help kill the X server so that I can install the driver?  Thanks very much.

Nu-ub

---

### Post by md2406 on 2011-09-29
I ma having the exactly same problem with ubuntu 10.04 amd64 and non of the stuff I found on the forms work out for me.

---

