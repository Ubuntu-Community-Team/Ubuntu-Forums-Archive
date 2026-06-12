---
title: "extra hard drive"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by meekatron on 2008-01-04
i already have a second hard drive on my system mounted in /music, which means i have 200gb of space in there for saving my music. my question is would it be possible to install another 200gb hard drive and mount it in the same folder to give me 400gb of space for my music.

---

### Post by steeleyuk on 2008-01-04
The only real, proper way to do it is setting up striping (RAID 0) but if one drive dies all the files are lost. You can usually do that in the BIOS or with a PCI RAID card. Beware that if you do it, it may wipe the files on both drives before the RAID is setup.

---

### Post by meekatron on 2008-01-04
I have used software raid 5  before with my freenas drive before it died..
maybee will have to get a raid card. Would be cool if you could just mount it to the /music folder, so you can keep increasing the size without having to re format every time, and add extra space as you need it.

---

### Post by isaaca on 2008-01-04
yes, RAID 0 mode would do that, but you'd likely have to repartition drives (and find a place to put your files temporarily while you do) I would not recommend RAID 0 for a storage volume because as previously stated, if one drive dies, all your data is lost. This means the failure rate on the RAID 0 volume would be 2 times the failure rate of each individual drive. If you just add an extra drive, even if one drive fails, you still have half your data (and perhaps you backed up the important stuff to both drives). 

You can't mount two devices into the same folder. You could mount the second drive into a directory like /music/drive2 but you'd have to explicitly copy files into the /music/drive2 directory tree to use the space on the second drive.

---

### Post by linuxvacuum on 2008-03-21
Please look up LVM (Logical Volume Manager). It is so great ! :tongue:

---

