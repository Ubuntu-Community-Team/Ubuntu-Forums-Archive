---
title: "Can't format/mount RAID0 array"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by orbish on 2009-11-05
Greetings!  I am setting up a media center PC/file server with two 1.5 TB hard drives in a RAID0 array.  I want to format it using NTFS or ext4... at this point I don't care which.. I just want it to work.

The array was setup through the mobo utility.  Under Disk Utility, its shows up as 3001 GB HARD DISK.  When I create a partition it gives me this error:

```
One or more block devices are holding /dev/mapper/isw_dacfbagddg_Volume0
```

It's also showing the separate 1.5 TB drives which makes me think I'm in over my head.  Any Ideas?

---

### Post by punkybouy on 2009-11-05
Regardless of what distribution or OS you use you would still need a driver for the hardware. Since you created the array using the motherboard utility there is probably at least a Windows driver on a CD that came with it.  The driver would have to be slipstreamed into a Windows installation.  In Linux you would have to do the same thing assuming Ubuntu did not recognize during installation, the chipset manufacturer of the chip used for the array.  How that is done I don't know.  If you have the chipset manufacturer name you could try their website and see if they have a linux driver.

I have also heard that Linux can have issues recognizing SATA controllers which is why you get the /dev/mapper thing.  Is your RAID adapter SATA?

I could be wrong about the SATA controller.

---

### Post by orbish on 2009-11-05
Turns out onboard RAID is kinda full of it when it comes to linux...

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by punkybouy on 2009-11-07
It really depends on what you want to accomplish.  SATA RAID hardware controllers have come down in price and are only easy to use if they are recognized by the OS during installation.  The disk controller should have its own memory and bios.  You go into the controller bios and create your array and the controller then presents to the OS what appears to the OS as one or more drives depending on how you configured it...if the OS recognizes the controller and has a driver. You could do a web search for sata or even SCSI (much more expensive) RAID controllers that work well with Linux.  Buy a good one and it will last for years.  If you want performance you can do RAID 0 although if you lose one drive you lose the volume. With RAID 1 you can lose a drive, replace it with a new one and be on your way without skipping a beat.  If you really wanted to get fancy you could use hot swappable drive bays making the change out an activity that takes seconds.

---

