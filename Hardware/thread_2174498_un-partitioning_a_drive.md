---
title: "un-partitioning a drive?"
date: 2013-09-14
forum: Hardware
---

### Post by mzimmers on 2013-09-14
Hi, all -

I have a system with a disk that hosts two OSs: ubuntu and Windows 7. I now want to add a second disk, to be my new boot disk for Windows. Once I transfer my Windows stuff to the new disk, I'd like to get the space on the old drive freed up by deleting the partition or whatever I have to do.

So:

1. (I realize this isn't an ubuntu question, but) does anyone have a recommended way to copy the Windows stuff from olddisk to newdisk?
2. Once #1 is finished, can someone tell me how to un-partition olddisk?
3. Do I need to do anything to make sure that I can choose which disk to boot from upon power-up? I'm currently running GRUB, and it asks me whether I want ubuntu or Windows from olddisk.

Thank you for any help.

---

### Post by stretch2 on 2013-09-14
Hiya,

Probably the best way to get your old windows onto your new hard drive would be to use a disk cloning tool such as Acronis or Ghost. If these aren't available to you, you could just install windows onto your second HDD, and copy everything over (Although you may have to re-install applications and drivers etc).

To expand a Linux partition, you may be able to use Partition Magic (Though don't hold me to that Lol) ... Or you can follow this guide: [http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

As for GRUB, just follow this guide: [http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order) ... Mine automatically detected my other OS's, so I've never had to use it :D

Also, just to plug a great bit of software, to make your life a little easier, get YUMI Multiboot from: [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/) ... I have found this to be very useful when playing about with multiple OS's, and is very easy to download tools and OS's, so if something goes really wrong, at least you can easily load a live linux or mini XP to fix things.

---

### Post by CatKiller on 2013-09-15
For #2, GParted will be fine. Delete the Windows partition and expand the other partition(s) into the free space. You can't change a mounted partition so you'll need to do it from a Live CD or similar. GParted is included on the Ubuntu install disc, or you can get an image from the GParted site.

---

### Post by mzimmers on 2013-09-15
Hey, guys -

Thanks for the response. I'm having a little trouble getting out of the blocks here. I tried the evaluation copy of [COLOR=#000000]Acronis, but it doesn't do cloning in eval mode. I installed ghost, but honestly, it was too large and complicated for me. I tried an image backup/restore using Windows' utility, but the restore failed due to some kind of perceived file system mismatch or something. I tried GParted, but can't find the clone feature. I did a copy/paste operation, which appeared to work, but the destination drive won't boot. So...I'm going to have to figure out what should be a very simple step before I can move on.

Thanks again.[/COLOR]

---

### Post by CatKiller on 2013-09-15
Yeah, no, GParted won't help you with the Windows side of things; Windows is too fragile. The only time I attempted to move Windows to another drive it broke, so I just deleted it. That's why I didn't offer you anything helpful with your #1.

TBH, since Windows users suggest periodic re-installation as a prophylactic measure anyway, I'd be tempted to just do that, as stretch2 suggested. Backup the useful data first, of course.

---

