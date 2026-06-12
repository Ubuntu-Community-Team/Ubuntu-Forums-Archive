---
title: "Backup preinstalled Vista"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by 987poiuytrewq on 2009-04-30
Hi, I just got a new laptop that came with Vista preinstalled. I was dual-booting Intrepid and XP on my old laptop and I want to single-boot Jaunty on my new one. However, I would like the ability to install Vista at some point in the future, if I want to, considering I did (annoyingly) pay for it. I'm not going to go through the dance of possibly getting a refund, I just want to put the recovery partition on a DVD so I can reinstall it later if I want to. Would this work if I backup the recovery partition and keep the recovery CD that came with the laptop or do I need to do something else like make an image of the hard drive? If this question has already been answered here, could someone point me in the right direction. Thanks!

---

### Post by Mark Phelps on 2009-04-30
While what you want to do SHOULD work, it's hard to say for sure.  There's a possibility that the recovery partition has to be a specific size and or a specific location on the drive; not likely, but still possible.  These partitions are usually not very big, generally just large enough to store a compressed windows image file.  In other cases, these are not really partitions at all, just specially formatted files that LOOK like a partition.  If the latter is true in your case, you will not be able to put the "partition" back once you remove it.  If you really want to be guaranteed to be able to reload Vista, I would strongly recommend that you leave it alone.

---

### Post by 987poiuytrewq on 2009-05-01
Okay, thanks for your reply. If I use something like Partimage [http://www.partimage.org/Partimage-FAQ#If_I_make_an_image_file_of_a_partition.2C_can_I_restore_it_to_an_unpartitioned_hard_disk_.3F](http://www.partimage.org/Partimage-FAQ#If_I_make_an_image_file_of_a_partition.2C_can_I_restore_it_to_an_unpartitioned_hard_disk_.3F) to create an image of the C:\ partition AND the recovery partition if it is a real partition, and make a note of the partition sizes and locations, I could always restore my laptop's hard drive to exactly its original state couldn't I? Or is there something I haven't considered?

---

### Post by lisati on 2009-05-01
The Toshiba laptop I have which came with Vista preinstalled came with a tool to backup the recovery partition to a bootable DVD. Maybe this is an option.

---

### Post by mikechant on 2009-05-01
I'm not a Windows guru but I thought that if you had a seperate recovery disc that was all you needed - e.g. if your hard drive was wiped or failed so you haven't got a recovery partition, the supplied recovery disc was all you needed to reinstall. If that's the case you don't need to back up the recovery partition at all.

My understanding was that (if you are supplied with a seperate  recovery disc), the point of having the hard drive recovery partition as well was for speed/convenience or for if you lost your recovery disc.

Maybe someone can confirm this?

---

### Post by Tristan_F on 2009-05-01
I think it depends if you want to be able just to reinstall Vista or to reinstall the system as it was including all the apps preinstalled by the computer manufacturer (like Photoshop and so on...)

If you just want to get a Vista copy out of your computer there is two possibility : 

- your hard drive already has a recovery partition and then you can just wipe Vista install. You can reinstall it after provided you make a new partition and some space for it (on my VAIO it needs at least 50Gb :(). You will then have to tweak some things in GRUB so that the Vista install can be booted

- you don't have any recovery partition nor a DVD. You can try to use vlite which is an app to back up your vista install on a DVD. You can even choose the components you want to back up and the one you want to get rid off.

Hope this is clear

---

### Post by 987poiuytrewq on 2009-05-05
Thanks everybody for your replies, I did what lisati suggested and used the recovery disk supplied by the manufacturer to burn a seperate CD that will supposedly let me reinstall Vista even if I wipe my hard disk. Now I can use my whole hard disk for Ubuntu.

---

### Post by Mark Phelps on 2009-05-05
> **mikechant said:**
> I'm not a Windows guru but I thought that if you had a seperate recovery disc that was all you needed - e.g. if your hard drive was wiped or failed so you haven't got a recovery partition, the supplied recovery disc was all you needed to reinstall. If that's the case you don't need to back up the recovery partition at all.

My understanding was that (if you are supplied with a seperate  recovery disc), the point of having the hard drive recovery partition as well was for speed/convenience or for if you lost your recovery disc.

Maybe someone can confirm this?
It depends on the OEM and the machine.  In some cases, the recovery CD is nothing more than a boot CD that then accesses the recovery partition and uses it to do the full restore.  In other cases, the recovery CD is a compressed image that can be used standalone to completely restore the machine.  When in doubt, it's best to check with the machine supplier to find out for sure.   It's a little late, after you've wiped the partition, to find out that all you have is a boot CD.

---

