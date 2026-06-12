---
title: "&quot;Error 21: Cannot find Hard Disk&quot; when starting computer"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by dannytatom on 2008-12-14
I just did a fresh install from the netinstall iso, and it installed good.  No errors during install or anything, but when I restarted I get a "Error 21: Cannot find Hard Disk"

What went wrong, and how can I fix it? :(

---

### Post by gpsmikey on 2008-12-14
If you go into the BIOS, does it show the disk correctly ??

mikey

---

### Post by dannytatom on 2008-12-14
Yeah, it shows up in the boot order and everything.

---

### Post by gpsmikey on 2008-12-15
OK, so it looks like the disk is working and the BIOS can see it.  It appears that the "Error 21" is a GRUB error - a Google search for "grub error 21" turns up quite a few hits - you might look through those and see if any of them ring a bell for you (seems to be a number of different causes).  Assuming that error is from grub (which it looks like it is), your hard drive is actually being found (contrary to the message) since it is booting the first stage of grub from the disk (which then spits out the message) - then it gets lost.  Hope that helps.

mikey

---

### Post by Bucky Ball on 2008-12-15
Is it a dual boot and if so, is the windows partition booting? Are you getting a grub menu with all your kernels and OSs listed? If so, choose the kernel you want to use, and hit 'e' to edit. There will be a section that says:

```
root            (hd0,1)
```... or something like it. the 0=first physical drive, the 1=second partition (if you follow).

So, if your install is on the second physical disk and the second partition you would need to change this to:

```
root (hd1,1)
```Good luck.

If you scroll way down this page you will find a complete description of GRUB error 21:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This can be a problem if drives are physically removed or moved around, or partitioning changes somehow. (Changing the order in the BIOS may well effect the outcome also).

---

### Post by caljohnsmith on 2008-12-15
In order to get a clearer picture of your setup, how about booting your Live CD, download the attached "boot_info7.sh.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info7.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will help clarify your setup and what your problem might be.

---

