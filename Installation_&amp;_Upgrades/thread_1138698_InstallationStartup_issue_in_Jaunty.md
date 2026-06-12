---
title: "Installation/Startup issue in Jaunty"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by TheSauce on 2009-04-26
I have WinXP and am installing Jaunty within Windows.  I have one DVD Burner (Master on IDE1), a 120GB WD HDD (Slave on IDE1), a 250GB Maxtor HDD (Master on IDE2), and a 200GB WD HDD (Slave on IDE2).  During the first part of the installation where it is quickly scrolling and showing you the different hardware, it hangs after it has detected my last hard drive (the 200GB WD HD).  Here are what the last two lines look like:

[2.354075] ata2.01: ATA-6: WDC WD2000JB-00GVA0, 08.02D08, max UDMA/100
[2.354136] ata2.01: 390721968 sectors, multi 16: LBA48

I decided to disconnect that last HDD and tried installing again and it installed fine.  Everything runs fine as long as that last drive is disconnected.  If I reconnect that drive and try to boot into Ubuntu then it hangs again.  If I boot using recovery mode I can see that it hangs at the same spot that it does when trying to install.

Anyone have any thoughts?  Is there a way to make Ubuntu just ignore that last drive on startup because when I'm in Ubuntu I don't need anything on it.

Thanks,
Jared

---

### Post by TheSauce on 2009-04-26
One thing I forgot to mention is that Ubuntu is installed on the first drive, if that makes a difference.

Thanks again for any thoughts,
Jared

---

### Post by TheSauce on 2009-04-27
I also just tried disabling the drive in my BIOS but for some reason it still recognizes the drive and hangs at the same spot.

Jared

---

