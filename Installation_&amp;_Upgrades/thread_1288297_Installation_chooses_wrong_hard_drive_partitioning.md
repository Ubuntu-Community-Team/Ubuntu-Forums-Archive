---
title: "Installation chooses wrong hard drive partitioning"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by RoBBS on 2009-10-11
Yesterday the boot drive of my workstation went to hardware heaven, so I thought it was time giving my computer an upgrade, and buy an SSD. below is what I did to it, and in what order.
- Installed the drive just as a normal HDD
- Created 1 primairy partition 35Gb in size NTFS
- Installed Windows XP 64bit (I find it easier then starting with ubuntu).
- Installed all upgrades/drivers for windows
- Rebooted with a freshly burned Ubuntu 9.04 DVD
- Install Ubuntu, and chose the partitioning option "Install them side by side"
- After the install, Everything worked, except the windows NTFS partition grew in size to 70 Gb, and I was left with a 2.5 Gb ubuntu install, which is not big enough to actually do something with.

I tried resizing the NTFS partition which failed and left me with a completely unbootable system. Reinstalling everything but entering my own partitioning scheme created what I wanted, A 50/50 split between windows and ubuntu.

Now I'm wondering, I can clearly remember this working on earlier installs, is this an SSD specific issue or some error in the installation? Should I file this as a bug or is there a logical explanation I don't see?

Below is my configuration
- MSI P45Neo
- Intel Q6600
- 4x 1Gb PC800 DDR2
- Previously samsung 160Gb drive, now Intel X25-M SSD
- LiteON DVD Burner
- Nvidia 8600GT

---

### Post by raymondh on 2009-10-12
> **RoBBS said:**
> 
- Install Ubuntu, and chose the partitioning option "Install them side by side"
- After the install, Everything worked, except the windows NTFS partition grew in size to 70 Gb, and I was left with a 2.5 Gb ubuntu install, which is not big enough to actually do something with.



Hey RoBBS,

Did you use the slider to allocate partition sizes?  See attached:

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

If not, it would have enlarged your XP and just given Ubuntu the 2,5GB default size.

Regards,

---

### Post by presence1960 on 2009-10-12
> **raymondhenson said:**
> Hey RoBBS,

Did you use the slider to allocate partition sizes?  See attached:

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

If not, it would have enlarged your XP and just given Ubuntu the 2,5GB default size.

Regards,

+1

This is a very common mistake that I will never understand. I always choose manual install because I set up my partitions beforehand. But if I were to choose the side by side install it would irk me that I never chose a size for each OS's partition. I would not proceed until I found out how to do that. It is only natural to have a choice there as everyone's needs and setup will vary.

---

