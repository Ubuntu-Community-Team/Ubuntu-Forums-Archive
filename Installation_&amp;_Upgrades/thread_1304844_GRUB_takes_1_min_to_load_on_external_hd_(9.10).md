---
title: "GRUB takes 1 min to load on external hd (9.10)"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by w4r3zh4ck™ on 2009-10-29
as title says
im booting windows 7 and ubuntu 9.10 on external drive and its so slow !!!!!!!!!!!

---

### Post by MrSnowmiss on 2009-10-29
and??

---

### Post by w4r3zh4ck™ on 2009-10-29
> **MrSnowmiss said:**
> and??

and what ??? u think i got time to wait it 1 min ? ubuntu 9.04's grub was taking 3 sec so wheres the difference ???

---

### Post by lovinglinux on 2009-10-29
I have the same issue on an internal drive, but mine loads in 23 seconds. This problem happens when the mbr is on a different drive than the grub installation files. I have two drives with one Karmic on each. When I use the grub from the installation on the same drive as the mbr it loads pretty fast.

There is already a bug report on launchpad, but I can't find it right now.

---

### Post by w4r3zh4ck™ on 2009-10-29
well lets hope there will be update to fix that bug

---

### Post by lovinglinux on 2009-10-29
> **w4r3zh4ck™ said:**
> well lets hope there will be update to fix that bug

You could try changing the boot order on BIOS, but that didn't work for me.

---

### Post by wilee-nilee on 2009-10-29
Also you have said external HD is it plugged into a usb and if so is it at the least usb2. When you post with very little information then complain people generally will not take you seriously.

---

