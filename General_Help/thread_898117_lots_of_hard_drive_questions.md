---
title: "lots of hard drive questions"
date: 2008-08-22
forum: General Help
---

### Post by Ender305 on 2008-08-22
I just got a new 1TB external hard drive and I have a few questions about it:

1. how do I rename the default mount point(s); aka /media/SimpleDrive or D: SimpleDrive

2. what disklabel should I use that Windows supports, everything supports msdos, but I want to use GPT

3. what program can I use to make a bootable backup

4. how does I squashfs?

---

### Post by scouser73 on 2008-08-23
Hi Ender305, here is a link that shows you what you will need to label your 1TB HDD; [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

In answer to question 2, I have found that NTFS works best, but I guess it's upto the individuals preference.

Questions 3 & 4 I don't have a clue about.

---

### Post by Ender305 on 2008-08-25
in #2 I'm not talking about the format, I'm talking about the disklabel, msdos supports only 4 primary partitions but GPT supports 100+ primary partitions so I want to know if it works in Windows

---

### Post by WRDN on 2008-08-25
There is a guide [here]("http://www.sysresccd.org/news/2008/01/26/gpt-disklabel-support-guid-partition-table/"), for how to enable the GPT disk label.

---

### Post by Ender305 on 2008-08-26
I'm asking about GPT support in Window$, it doesn't matter that much, but I'd like to know

the only other big thing is making a bootable backup/making the disk bootable(GRUB etc.)

---

### Post by Ender305 on 2008-08-27
bump? also, I want to make an encrypted ext3 partition, anyone know how?

---

### Post by Ender305 on 2008-09-06
bump

---

### Post by mishaokami on 2008-09-17
[http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian](http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian)

It worked great for me under ubuntu.
Notes:
Forget steps 1 and 2 on ubuntu systems
On step 3 use the paranoid version or don't do the step at all.  His first suggestion provides no extra security and simply wastes time.
After 4  do a "sudo modprobe dm-crypt"

I think that is all... good luck.

---

