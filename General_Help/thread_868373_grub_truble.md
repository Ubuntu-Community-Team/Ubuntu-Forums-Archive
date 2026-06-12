---
title: "grub truble"
date: 2008-07-23
forum: General Help
---

### Post by bobie on 2008-07-23
I originally installed ubuntu as a dualboot-dual hard drive setup. I was impressed with ubuntu so I'm srapping my XP hard drive, but that's where grub was. I got Super Grub Disk to restore grub on my Ubuntu drive (now standalone), but the problem is that it's the grub that was in place before my changes.

 I've tried a bunch of stuff from Ubuntuguides.org and a couple things I found from Google. But they didn't work. THis must be an easy fix, but I can't figure it out. I could just reinstall Ubuntu, but I would rather learn how this works rather than throw in the towel and reinstall everytime something goes wrong.

Thanks.

---

### Post by bobie on 2008-07-23
I figured I would include my fdisk.
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

---

### Post by logos34 on 2008-07-24
Boot into ubuntu with SGD and edit your /boot/grub/menu.lst so the 'root' (and 'groot') lines read (hd**0**,**0**). 

then run

sudo grub-install /dev/sda

---

### Post by bobie on 2008-07-24
The problem is. I never had any luck getting SGD to let me into Ubuntu

---

### Post by bobie on 2008-07-24
I can either get it to give me my old, bad Grub menu list... or I get it to a point where it looks like it loads some drivers, but gets to "B HID core driver" and pauses. Hitting enter just moves the cursor down one line

---

### Post by logos34 on 2008-07-24
> **bobie said:**
> I can either get it to give me my old, bad Grub menu list... 

ok, then select ubuntu and press 'e', then a second time on 'root' line and change to (hd0,0).  'b' to boot.  try that

---

### Post by bobie on 2008-07-24
Ok. I'm in Ubuntu. But when i try to edit menu.lst and save it. I get an error telling me I don't have permissions necessary to save it......

---

### Post by bobie on 2008-07-24
Ok. I got it. I did sudo chown... then saved. booting into ubuntu now. 
Thanks.

---

### Post by logos34 on 2008-07-24
not chown...for admin privileges you use 

**gksudo** gedit /boot/grub/menu.lst

or

**sudo nano** /boot/grub/menu.lst

chown it back to **root:root**

---

