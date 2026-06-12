---
title: "Is ext3 Journaling ON by default?"
date: 2008-09-12
forum: Hardware
---

### Post by mailforbiz on 2008-09-12
Hi

Need some help from the filesystem gurus. So if one uses ext3 filesystem on a partition, what is the default behavior as far as journaling is concerned? It seems the default mode is **ordered** which is not doing journaling of the data (just the metadata). Am I understanding this right? If one wants to use journaling, should I just set it up in fstab, or pass an option to mount command or use tune2fs in a startup script after the partition is mounted? Or are these equivalent? 

For context, we're using ext3 on an appliance which is amenable to sudden power shutdowns and want to investigate how we can reduce chances of a corrupted filesystem. In that vein, it would also be nice to know people's experiences with **other FS **besides ext3 especially wrt high robustness. In particular, our requirement is close to nil chances of filesystem corruption even with power outages and we can live with the tradeoff in performance. Our current system is on a flash drive.

Would appreciate feedback from folks.

TIA,
HT

---

### Post by sdennie on 2008-09-12
Yes, by default it's set to "ordered".  If you want to change it to "journal", you'll have to use both tune2fs and fstab (and, if it's the root partition /etc/grub/menu.lst).  ext3 is considered to be one of the more robust filesystems for handling power outages but, I'm not sure how much more robustness you get by switching from "ordered".  Regardless, here is a guide for switching to "writeback" (which, you don't want) but shows you the steps you need to take for switching the journal mode of a disk: [http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

---

### Post by IntuitiveNipple on 2008-09-12
> **mailforbiz said:**
> Hi

In particular, our requirement is close to nil chances of filesystem corruption even with power outages and we can live with the tradeoff in performance. Our current system is on a flash drive.

The solution in that case is a UPS or battery-power the device so if the mains power fails the device can either do an orderly shut-down or continue on battery power.

---

### Post by mailforbiz on 2008-09-17
Thanks for your responses. On doing some research, it seems that folks recommend using JFFS2 for Flash drives for maximum protection. However, that would mean changing the way our applications currently reads and writes and so this is off the table for now. We would like to maintain the abstraction provided by a high-level filesystem like ext3 for the time being. Using a UPS is also not possible because of the nature of the appliance.

On a related note, are there any effects of switching the Journaling level of ext3, besides possible performance hit?

---

### Post by bingoUV on 2008-09-17
I don't know how much it helps in flash storage, but for hard disks, switching on barriers with ext3 helps chances of data integrity. You will have to read the specification of the flash drive to check if it implements write cache, and supports filesystem barriers. If yes, enable barriers for your server thus:

By default barriers are off in Ubuntu. To enable them, add "barrier=1" to mount options in addition to the "data=journal" as specified in the link given by vor.

---

### Post by mailforbiz on 2008-09-23
Thanks, I'll try that out. 

> **bingoUV said:**
> I don't know how much it helps in flash storage, but for hard disks, switching on barriers with ext3 helps chances of data integrity. You will have to read the specification of the flash drive to check if it implements write cache, and supports filesystem barriers. If yes, enable barriers for your server thus:

By default barriers are off in Ubuntu. To enable them, add "barrier=1" to mount options in addition to the "data=journal" as specified in the link given by vor.

---

### Post by pwerner2 on 2008-10-15
Nevermind. My question has already been answered. Sorry.

---

