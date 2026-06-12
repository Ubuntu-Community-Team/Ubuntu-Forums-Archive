---
title: "How do I get Ubuntu to see my other drives?"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by ivanjs on 2005-10-21
I have 3 hard drives, a CD burner and a DVD burner. Ubuntu sees the CD burner/player and the main hard drive that it is installed on. How do I get it to see the other drives? The system sees them when I boot up (shows all of them), but Ubuntu only sees those mentioned.

I was able to show the 2nd partition on the main drive using techniques shown in one of the guides here, but not a separate drive.
J.

---

### Post by dbott67 on 2005-10-21
[quote=ivanjs]I have 3 hard drives, a CD burner and a DVD burner. Ubuntu sees the CD burner/player and the main hard drive that it is installed on. How do I get it to see the other drives? The system sees them when I boot up (shows all of them), but Ubuntu only sees those mentioned.

I was able to show the 2nd partition on the main drive using techniques shown in one of the guides here, but not a separate drive.
J.[/quote]

You need to 'mount' the additional hard drives in order to see them.

There are a number of things that you need to know to mount a hard drive, such as device name and partition number (i.e. /dev/hda1).  If you've got 3 hard drives, they would be hda, hdb, hdc.  If your 2nd hard drive (hdb) has 3 partitions (NTFS, FAT & ext3) the partitions would be hdb1, hdb2, hdb3.

With this information, you can then create 'mount points' and mount the volumes.

All of the gory details are spelled out here:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

Hope this helps,
Dave

---

### Post by Kyral on 2005-10-21
I hope you are not afraid to edit config files or the terminal, because this is a job best done with those two tools.

First paste the output of ```
sudo fdisk -l
``` and your /etc/fstab here

BTW What did you mean as a "separate drive"?

---

### Post by ivanjs on 2005-10-21
Thanks for the replies. I'm very comfortable with the terminal, I just haven't done anything involving mounting hard drives before. Appreciate the tips. I'll try them when  I get home...

---

### Post by ivanjs on 2005-10-21
[QUOTE=Kyral]BTW What did you mean as a "separate drive"?[/QUOTE]
Meaning I was able to mount the NTFS partitions that were on the drive Ubuntu was installed on, but not separate drives (the other 2 I mentioned).

---

### Post by Kyral on 2005-10-21
Ah. So you mean different physical drives...sometimes I forget I have 3 HDs ;p

---

