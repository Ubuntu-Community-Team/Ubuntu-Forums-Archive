---
title: "Please Help - Monitor Blank On Restart"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by vorsia on 2006-01-15
Hi all,

I am using a Toshiba Satellite A100 notebook with a 15" TFT widescreen display.
I'm in a spot of trouble here... i installed Ubuntu 5.10 and all seemed to go well until the first login... it asks for my username and password, which i enter. Then the x windows fails to start and i get "Fatal Error" or something. When i restart the system my monitor is black although i believe that the computer is still working.

I had a similar problem before with a Knoppix install. I fixed that using an external monitor, however i can't seem to get that to work this time. Any help would be appreciated.

James.

---

### Post by Luke on 2006-01-16
what type of video card do you have?

i have an ati radeon xpress 200 and i had a similar problem.
to fix it, i went into "/etc/X11/xorg.conf" and changed the video driver from "ati" to "vesa".

you can try selecting recovery mode from the grub menu. this will bring you to a root prompt where you can check/edit your xorg.conf file 
```
nano /etc/X11/xorg.conf
```
be sure to make a copy first.
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by vorsia on 2006-01-16
thanks for the reply!

I believe that that would work...however sadly i can see nothing on the monitor at any time. Not even the boot up screen when the machine starts, no bios, no grub...just blackness... :( 

I believe that flashing the vga bios may fix the problem however it is so hard to find the tools to do this and i am not exactly sure of my video specs. I'm not sure if this risks damaging the card either...

---

### Post by Luke on 2006-01-16
sorry, didn't realize how severe your problem was.
did you trying throwing a live cd in there? (if you have one)
does it behave any differently?

---

### Post by vorsia on 2006-01-17
yeah, i tried that...

sadly nothing... I am quite certain that this problem is related to the video bios. i'm sure the actual hardware is fine. I think flashing the vbios would work but frankly i can't be bothered. I'm going to get a different model on warranty, hopefully the new machine is better supported by ubuntu.

I would still like to know if anyone knows of a solution to this problem.

---

### Post by nik4july on 2006-02-26
hi there I have recently had a similar problem, on restart only but not from start up. It seems your system is going to s-video output mode on restart. If you select fn f5 you may get your display back. I'm sorry but I don't know the fix to this problem

---

