---
title: "GRUB problems with eSATA hard drive."
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by sgarman on 2007-10-11
I've fixed my share of GRUB problems, but this one's got me stumped. 

I just added an eSATA external hard drive to my system (it's a Western Digital My Book) along with an Addonics PCI eSATA card. 

Here was my initial setup:

BIOS boots to my single PATA drive (hda), which has GRUB installed on its boot sector. My GRUB config then points to an internal SATA drive that has a separate /boot partition (sda1). I have two internal SATA drives. This works with the following GRUB config section:

```
title           Ubuntu, kernel 2.6.20-16-386
root            (hd1,0)
kernel          /vmlinuz-2.6.20-16-386 root=/dev/md0 ro quiet splash
initrd          /initrd.img-2.6.20-16-386
quiet
savedefault
```

Now enter the eSATA drive. If I leave the drive turned off while my system boots, and then turn the drive on, it is detected as /dev/sdd. However, if I turn the drive on before my system boots, I get the following:

GRUB loading stage1.5
GRUB loading, please wait...
*(long pause of nearly a minute)*
Error 15

What's frustrating about this is I can't even get into the GRUB shell to test anything. So I've tried changing the root section to address different drive numbers (hd0, hd2, etc), assuming that the introduction of the eSATA drive to be messing up my drive order, but still no luck.

Can anyone give me any tips to figure this out?

Thanks,

Scott

---

### Post by dabl on 2007-10-11
Wild guess -- maybe the eSATA card is being recognized "in advance" of the internal SATA bus.  That would cause the internal /dev/sda SATA drive to be incremented to /dev/sdb, and /dev/sdb to become /dev/sdc, when the eSATA drive is powered on.  It would be an easy experiment to try setting your menu.lst boot line to (hd2,0) -- and your /etc/fstab file needs to match, by the way.  I dunno about your md0 RAID deal -- that's beyond me.  :)

---

### Post by sgarman on 2007-10-11
> **dabl said:**
> Wild guess -- maybe the eSATA card is being recognized "in advance" of the internal SATA bus.

This is true. After the BIOS POST, the eSATA card BIOS runs and I see it detect the external drive.

> That would cause the internal /dev/sda SATA drive to be incremented to /dev/sdb, and /dev/sdb to become /dev/sdc, when the eSATA drive is powered on.  It would be an easy experiment to try setting your menu.lst boot line to (hd2,0) -- and your /etc/fstab file needs to match, by the way.

Well, at least I'm thinking along the right lines. The change to (hd2,0) was the first thing I tried, with no luck.

My fstab file lists all partitions by UUID, so I'm presuming that is not impacted by the drive ordering change.

Thanks for the reply,

Scott

---

### Post by sgarman on 2007-10-11
> **sgarman said:**
> The change to (hd2,0) was the first thing I tried, with no luck.

One bit of information I guess I should mention is that when I switched my root line to (hd2,0) I had the same Error 15 from GRUB, but there was no delay before the error was displayed. Previously, there was a long delay of close to a minute before that error was printed to the screen.

Scott

---

### Post by dabl on 2007-10-11
I would try to set it up in /etc/fstab to mount by UUID.  You can get the UUID from your eSATA drive, when it is connected and running, with ```
blkid
```

Then use that UUID to set it up in fstab, along with your other drives.  I would think you could do the same in the /boot/grub/menu.lst file.  :)

---

