---
title: "New hard drive recognized as 137gb"
date: 2009-07-26
forum: Hardware
---

### Post by Bluefrenzy on 2009-07-26
Hi guys

I've been using Ubuntu exclusively for the past month and love it.  Recently my old 80gb hard drive died so I went out and bought a new 250gb (IDE) yesterday.  Installed Ubuntu no problem except that the drive is only recognized as 137gb.  I realize this is the bios 48lba issue.  My laptop is Sony Vaio pcg-v505dx --> the bios is upto the latest one (2004).  When I go into the bios --> it recognizes it as 137gb and there is no option to turn on LBA or turn on/off autodetect.

I've read on the forum here that partitioning is the answer.  I tried partitioning the drive so that there is a /boot, /swap, and / but to no avail.  When I try boot straight from the LiveCD to check with partition editor, it too recognizes the drive as 137gb.  Fdisk output also says 137gb.  Isn't Ubuntu supposed to ignore what the bios says?

Can somebody guide me on how to partition properly?  I'd appreciate any help on how to get Ubuntu to recognize the full 250 of the drive.  Thanks!

---

### Post by Whiffle on 2009-07-26
What size partitions did you make?

---

### Post by Bluefrenzy on 2009-07-26
Thanks for the reply

The boot partition I put at the beginning of the hard drive at a size of 200mb
The swap partition is 1.5gb (my RAM is 512mb)
The rest of the partition is the remainder

Is there a sequence as to how to partition?  ie use Live CD to format and partition drive with GPartEd first, then install Ubuntu?  Or is it ok to use the installation partitioner?

---

### Post by Whiffle on 2009-07-26
You can use the installation partitioner.  If I remember correctly, for partitioning to work for getting around the 137 GB limit, each partition needs to be less than 137GB in size.  I'm not quite sure how you would want to divide that up though.  Maybe have an extra partition devoted to Media files or something.

---

### Post by Bluefrenzy on 2009-07-26
Ok will try again.  Maybe what I'll do this time for my 250gb drive is:
/boot - 200mb
/swap - 1.5 gb
/drive1 - 125gb
/drive2 - whatever the remainder is

---

### Post by Bluefrenzy on 2009-07-26
Hi again guys

I reinstalled Ubuntu and partitioned again as above, but the total that Ubuntu sees the drive as is still 137gb.  Any other thoughts and suggestions will be welcomed.  Is there a way to force Ubuntu to ignore what the bios tells it?  Thanks

---

### Post by Bluefrenzy on 2009-07-27
bump

---

