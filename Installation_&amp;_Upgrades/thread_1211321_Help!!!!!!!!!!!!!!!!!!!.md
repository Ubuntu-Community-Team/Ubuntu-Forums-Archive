---
title: "Help!!!!!!!!!!!!!!!!!!!"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by kikueno on 2009-07-12
Solved.

---

### Post by merlinus on 2009-07-12
If you install windows using your entire hdd there will be no more grub.

---

### Post by khelben1979 on 2009-07-12
For more wisdom on the matter, [check out Grub on Wiki]("http://en.wikipedia.org/wiki/GNU_GRUB").

---

### Post by kikueno on 2009-07-12
> **merlinus said:**
> If you install windows using your entire hdd there will be no more grub.
So does that mean that if i format the whole pc there will be no more grub? can anyone tell me a link explaining this in detail. like boot the cd, windows setup bla bla bla...

---

### Post by raymondh on 2009-07-12
> **kikueno said:**
> So does that mean that if i format the whole pc there will be no more grub? can anyone tell me a link explaining this in detail. like boot the cd, windows setup bla bla bla...


[http://support.microsoft.com/kb/316941](http://support.microsoft.com/kb/316941)

Look at method 1.  Though this is for XP, the site is a MS support site so just browsing around will lead you to the appropriate version you wish to install.

Good luck.

---

### Post by kikueno on 2009-07-12
> **raymondhenson said:**
> [http://support.microsoft.com/kb/316941](http://support.microsoft.com/kb/316941)

Look at method 1.  Though this is for XP, the site is a MS support site so just browsing around will lead you to the appropriate version you wish to install.

Good luck.

thanks and then to remove grub? i go to recovery console and type what first? FIXBOOT or FIXMBR?

---

### Post by raymondh on 2009-07-12
> **kikueno said:**
> thanks and then to remove grub? i go to recovery console and type what first? FIXBOOT or FIXMBR?

From the link and method 1

Method 1: Perform a clean install of Windows XP
Use this method for a clean installation of Windows XP. A clean installation **removes all data** from your hard disk **by** repartitioning and **reformatting** your hard disk **and reinstalling the operating system and programs to an empty (clean) hard disk.**

.... including the windows bootloader.

---

### Post by issih on 2009-07-12
In other words..you stick windows cd in,  boot computer, tell windows to install to and format the whole disk, and everything linux will be gone forever, including grub.

Hope that helps

---

