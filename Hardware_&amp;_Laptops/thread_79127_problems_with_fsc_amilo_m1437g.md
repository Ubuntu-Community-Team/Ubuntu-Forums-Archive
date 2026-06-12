---
title: "problems with fsc amilo m1437g"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by andi135 on 2005-10-19
Hi! I bought the Notebook some day ago and have the following problem:

The System crashes at starting hot-plug system...

Can anybody help me?
best regards

---

### Post by petit baby on 2005-10-19
Hi

Just type M1437G in search bar. You will find a way to solve the poblem with hotplug. You just have to press ctrl C during boot, and then add 2 lines in blacklist.

But  A new problem appeared after that: I have got an error with Xserver. (I assume it has to do with the graphic card (ATI X700 128mo))

Does anbody know how to solve that?

thanks 

Arnaud

---

### Post by altair2020 on 2006-05-01
Hey I actually used Ubuntu 6.06 Dapper Drake, its the only distro ive managed to get to work on that stupid laptop, Fujitsu better get thier fingers out thier arses.

Get Ubuntu installed, let xfail, login as root at command line.

Download drivers with:

$ sudo apt-get install xorg-driver-fglrx 

Then edit the xorg.conf file...

$ sudo nano /etc/X11/xorg.conf 

few pages down you'll find:

Section "Device"Change Driver "ati" under that to Driver "fglrx"

save changes with CTRL-X, Y, ENTER and restart the xorg server with

$ sudo /etc/init.d/gdm restart 
At this point ubuntu starts the desktop with correct screen resolution and 2nd monitor support.

If you want to enable second desktop on external monitor, you need to make more changes to xorg.conf

---

### Post by goncoloz on 2006-05-02
Hi
I am using Dapper on the same laptop.. everything goes fine but i couldn t get mic to work en tv out is Black&White (but it is tlike that on windows also :))..

an suggestions... specially on mic...  thanks

---

### Post by amartires on 2006-10-25
I have this laptop too, and with FSC, I don't seem to have sound enabled...
Any sugestions?

---

### Post by altair2020 on 2006-11-29
Other than getting the graphics to work to linux.

There is no other problems with the laptop, sound and mic work fine in both linux and windows.

:-k

---

