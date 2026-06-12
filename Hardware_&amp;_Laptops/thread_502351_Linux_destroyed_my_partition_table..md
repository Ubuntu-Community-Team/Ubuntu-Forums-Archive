---
title: "Linux destroyed my partition table."
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by u-slayer on 2007-07-16
Today I go to plug in my external usb hard drive and I find that it appears to be unformatted! It used to be formatted entirely as NTFS and now it appears blank! So I boot into windows to confirm and it seems that for some strange reason linux has copied my partition table from my laptop hard drive to my external drive. WTF? So now the drive looks like this when viewed with disk manager...

<NTFS>
<EXT3>
<unformatted>

when it should just be one big NTFS partition. Of course, the external drive is not the same size as the laptop hard drive, so when viewed with My computer it appears unformatted. Disk Manager shows the 3 partitions on the external drive, which are exactly the same as my laptops hard drive. Strange...:confused:

Is there a way to fix the partition table in linux or just simply recover my data?

---

### Post by u-slayer on 2007-07-17
I used a windows :( tool to recover my data. The large files were corrupted, but the small files were fine.

---

