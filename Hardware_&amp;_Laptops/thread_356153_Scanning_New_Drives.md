---
title: "Scanning New Drives"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by NZ-Wanderer on 2007-02-08
I bought myself a new HDD today, and repartitioned all 4 drives including the new one (did this in Vista)

My question is: Is there any way of having Kubuntu rescan all my 4 hard drives and automatically pick up all the partitions like it did when I was originally installing it??

I have FAT32, EXT3 and NTFS partitions spread over the 4 drives)

---

### Post by terdon on 2007-02-08
what do you mean "pick up" ? You can always run f
disk /dev/<hard drive name> 
and then "p" to list the partitions. <hard drive name> should be hda for the first IDE drive, sda for scsi.

 Ubuntu has a graphical partition manager as well, I think it is called gparted.

---

### Post by NZ-Wanderer on 2007-02-08
What I meant was is there a way to have Kubuntu automatically realise that I had changed all my partitions around and set itself up to read the new partitions (just like it sets them up when you are installing Kubuntu for the first time.)

Last night in the end I had to go into "system settings/advanced/disk and file systems" and manually point the partition names to the correct partitions and then enable them one at a time.

It's a bit of a pity that Kubuntu can't just read and then display all partitions automatically without having to set things up manually every time partitions are moved around.

---

