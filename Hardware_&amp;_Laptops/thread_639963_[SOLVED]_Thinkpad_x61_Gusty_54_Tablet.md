---
title: "[SOLVED] Thinkpad x61 Gusty 54 Tablet"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by aliencam on 2007-12-13
I just got my x61 tablet with ultrabase today, and the first thing i did was pop in the ubuntu cd and install the 64 bit version of Gutsy.  I deleted all of the partitions (my computer came with the recovery cds for some reason... seven of them) 

I cannot get the tablet to work.  

looking online, it seems that everyone says the tablet works "out of the box"  
however, things do seem to work for me that others say didn't work by themselves sound and wlan work perfectly for me. 


I don't see anything with "wacom" in the device manager

maybe i should have tested it in vista first. dangit. 

what steps should I take to get the tablet to work in x64 Gutsy.?

---

### Post by aliencam on 2007-12-13
Found it: 

[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

you do 

```
gksudo gedit /etc/X11/xorg.conf
```

and uncomment (remove the "#" from before) three lines at the bottom under the "uncomment this if you have a wacom tablet"

how to fix the pen buttons: 

[https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadX61T](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadX61T)

---

