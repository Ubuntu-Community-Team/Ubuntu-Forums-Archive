---
title: "Unable to Copy 4GB+ files to ext4 USB drive"
date: 2011-04-06
forum: Hardware
---

### Post by shadysamir on 2011-04-06
I have a WD My Book 2TB USB drive that's formatted as an ext4 volume. I cannot copy files larger than 4GB to it. The files are located on the system's ext4 hard drive. Both Nautilus and shell fail to continue copying the file when it reaches the 4GB mark. I find that weird!

---

### Post by coffeecat on 2011-04-06
Weird, indeed. I'm sure you must have checked this, but have you connected the drive and run:

```
sudo fdisk -lu
```

... to be sure that something didn't go wring with the formatting somehow and that you ended up with a FAT32 partition?

---

### Post by shadysamir on 2011-04-06
fdisk reports HPFS/NTFS, which is double weird because: a) I formatted it as ext4, and b) if that's the case then still 4GB+ wont be a problem!

---

### Post by coffeecat on 2011-04-06
Fdisk reports what the partition table tells it, not the actual filesystem in the partition. It's just possible - but weird as you say - that the filesystem is FAT32, but that the code for NTFS has got itself recorded in the partition table. I do remember a bug from some time ago affecting HFS+ formatted partitions which were recorded as being ext3 in the partition table. Not relevant to your situation, but it shows that it can happen.

I'm not sure what to suggest. You need a utility which reads the fileystem, not the partition table. Try:

```
sudo parted -l
```You'll need parted installed if not already. Or install Gparted and see what that tells you.

In the meantime I'll have a dig around. There must be something that can identify a filesystem without relying on what the partition table says.

**EDIT**: by the way, what did you use to format the partition as ext4?

---

### Post by shadysamir on 2011-04-06
parted reports ext4. will try to remove the partition completely instead of just formatting it. thanks for your help. tell me if you find out anything more

---

### Post by shadysamir on 2011-04-06
Interesting finding: when i fdisk into the drive it gives this info

```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xf8774db7.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

```

when I try (w) it gives:

```
WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.
```

I will try to reboot now

---

### Post by coffeecat on 2011-04-06
Will do if I find anything, but with fdisk reporting NTFS and parted ext4, there's obviously something strange going on and you're wise starting over.

I have  a suggestion. In Gparted, from the Device menu, create a new partition table. Then create your ext4 partition. At least then you'll, hopefully, have a clean partition table.

**EDIT**: OK I was posting just as you posted your last post, which I've seen now. Interesting to see what happens when you reboot, but it sounds as though a new partition table is in order.

---

### Post by shadysamir on 2011-04-06
Nothing changed, reports same info after reboot. I guess I will use gparted when I go home. I'm in the office now and using ssh into the home computer which has the problem

---

### Post by shadysamir on 2011-04-19
I kinda fixed this by using rsync instead of cp this way I was able to copy all files regardless of size. Seems like a problem with cp. And the error message was about reading the file not writing it. And it stops at exactly 4GB in any file larger than 4GB

---

