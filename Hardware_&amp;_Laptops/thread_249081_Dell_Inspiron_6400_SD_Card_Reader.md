---
title: "Dell Inspiron 6400 SD Card Reader"
date: 2006-09-02
forum: Hardware &amp; Laptops
---

### Post by thedogcow on 2006-09-02
I have an inspiron 6400 with a built in Ricoh card reader. Out of the box, it appears to work fine with small (64mb) SD cards, however it will not work with a 1GB card nor a 4GB card, or a 128MB MMC card ot a 32MB MS card. Recently now it freezes the whole system when a large card is inserted (and forces me to turn it off by holding down the power button). Any ideas please?

---

### Post by knubbe on 2006-09-27
> **thedogcow said:**
> I have an inspiron 6400 with a built in Ricoh card reader. Out of the box, it appears to work fine with small (64mb) SD cards, however it will not work with a 1GB card nor a 4GB card, or a 128MB MMC card ot a 32MB MS card. Recently now it freezes the whole system when a large card is inserted (and forces me to turn it off by holding down the power button). Any ideas please?

I have an inspiron 6000. 64mb card works fine, but with my 2gb it doesnt. It often makes my system freeze too.

---

### Post by mcglnx on 2006-11-04
I have a 6400, and the card reader does not work under Edgy.
As a side notes, there is a known issue for cards of more than 2Gb.

---

### Post by PhrankDaChickenGeek on 2006-11-25
Anyone?

My system (Dell e1705 laptop) freezes as well when a 2GB SD card is inserted. 
When is a fix coming?

---

### Post by knubbe on 2006-11-25
> **PhrankDaChickenGeek said:**
> Anyone?

My system (Dell e1705 laptop) freezes as well when a 2GB SD card is inserted. 
When is a fix coming?

From what I've read this is fixed in linux kernel 2.6.18. Edgy Eft use kernel 2.6.17. 

If you want kernel 2.6.18 you'll have to [compile 2.6.18 yourself]("http://ubuntuforums.org/showthread.php?t=217657") or wait for [the next version of Ubuntu]("http://www.ubuntuforums.org/forumdisplay.php?f=179").

---

### Post by MarkRobert on 2006-12-20
Odd. My 6400 now *does* read my 2 GB sd card. I reformatted it in windows recently, think I tried fat 16 to see if any difference.

---

### Post by knubbe on 2006-12-20
> **MarkRobert said:**
> Odd. My 6400 now *does* read my 2 GB sd card. I reformatted it in windows recently, think I tried fat 16 to see if any difference.

This issue was solved in edgy after upgrading to kernel 2.6.17-10, released in december 2006 in the repository.

This bug is now fixed on launchpad ([https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/61758]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/61758")).

---

### Post by MarkRobert on 2006-12-20
That explains that then, thanks.

---

