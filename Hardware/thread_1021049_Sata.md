---
title: "Sata"
date: 2008-12-24
forum: Hardware
---

### Post by theozzlives on 2008-12-24
I have a Dell Inspiron 1525 with a 160 GB SATA drive. a couple of weeks ago I installed Windows XP to run Transcender and uCertify. It went well but I had to change my BIOS to ATA for XP. I don't have a floppy so I can't install the SATA drivers. I'm just curious, how much performance am I losing?

---

### Post by logos34 on 2008-12-24
Unless you're doing a lot of multitasking, probably not much--assuming the hard drive even has NCQ (the feature which randomizes read/write commands for optimum disk performance).  

[http://en.wikipedia.org/wiki/Serial_ATA#Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Serial_ATA#Advanced_Host_Controller_Interface)
[http://expertester.wordpress.com/2008/07/24/ahci-vs-ide-%E2%80%93-benchmark-advantage/](http://expertester.wordpress.com/2008/07/24/ahci-vs-ide-%E2%80%93-benchmark-advantage/)

I don't see any info in the specs as to the model # of the HDD in your Inspiron, but you can find it with:

> sudo lshw -C disk | grep product

then google it

You would also lose any features supported by AHCI like hot-swap (not really an issue) and advanced power management features like this:

> SATA Aggressive Link Power Management
Several SATA controllers, that use the AHCI specification, have a feature called ALPM, which stands for Aggressive Link Power Management. ALPM is a technique where the SATA AHCI controller puts the SATA link to the disk into a very low power mode when there's no IO for awhile. The controller automatically puts the link back into active power state when there's real work to be done. This can save between 0.5 and 1.5 Watts of power.

[http://www.lesswatts.org/tips/disks.php](http://www.lesswatts.org/tips/disks.php)


> I don't have a floppy so I can't install the SATA drivers

This method doesn't require a floppy:
[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

---

### Post by theozzlives on 2008-12-25
Only problem is that requires re-installing and re-configuring.

---

### Post by logos34 on 2008-12-25
> **theozzlives said:**
> Only problem is that requires re-installing and re-configuring.

unfortunately.  I only know of one where you don't have to reinstall, but it's only for intel southbridges and frankly looks like a dirty hack [here]("http://www.msfn.org/board/enable-AHCI-Intel-ICH9-XP-t109450.html").

However, you might consider the method described [here]("http://www.maximumpc.com/article/howtos/how_to_slipstream_windows_xp_sp3_and_vista_sp1")--yes, it requires you to reinstall twice, but you're making a custom XP install CD image which includes EVERYTHING--the drivers, patches, ms updates, ie7, etc--so you'll never have to redownload and reinstall all of that stuff again

---

