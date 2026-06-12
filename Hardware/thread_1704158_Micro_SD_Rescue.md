---
title: "Micro SD Rescue"
date: 2011-03-10
forum: Hardware
---

### Post by Groover20 on 2011-03-10
I recently bought a 32Gb Micro Sd.  The intent was to use one for my new HTC Desire HD, to replace the 8Gb coming with the phone.

I copied the data from the old card to my hard-drive, and then copied back to the new card.  I put it in my phone, and everything was fine, except maybe that some big files were not showing up, even though the space taken was correct.

Anyhow, when I picked up my phone this morning, it said that the card was empty or using an unrecognized file system.  I was unable to format it from the phone, and tried with my laptop.  It didn't even show in the "Computer" view.

Is there something that can be done?  Can I rescue the card, and reformat it?

Thanks in advance,
Groover

---

### Post by Grenage on 2011-03-10
You can try reformatting it; do you have an SD drive or adapter for a PC?  Failing that, you could ask for a refund.

---

### Post by Groover20 on 2011-03-10
I have the adapter...Unfortunately, when I tried to reformat it from my Ubuntu Laptop, it doesn't even show up as a media!

---

### Post by Grenage on 2011-03-11
Does it show up under fdisk?

```
sudo fdisk -l
```

---

### Post by Groover20 on 2011-03-13
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1fc9562d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29298   235336153+  83  Linux
/dev/sda2           29299       30401     8859847+   5  Extended
/dev/sda5           29299       30401     8859816   82  Linux swap / Solaris

Disk /dev/sdb: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders
Units = cylinders of 16 * 512 = 8192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by Grenage on 2011-03-13
Te be honest, that looks like a fake card; there are a lot of them going around.

When I say fake, they basically take a small card, and alter it to look like a much larger one.  Ask for your money back and/or leave bad feedback if it was an ebay item; these sellers always know what they're moving.

---

### Post by lindsay7 on 2011-03-13
Look for an HP utility program for reformatting or re-setting up an flash drive or sd card.  It is free and is a windows program. It should run under wine.

---

