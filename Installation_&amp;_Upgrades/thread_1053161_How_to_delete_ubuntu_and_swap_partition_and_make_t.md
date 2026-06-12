---
title: "How to delete ubuntu and swap partition and make them ntfs"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by haran_hockey on 2009-01-28
Bascially I'm dual booting xp (C:\) and ubuntu with a swap partition so I have 3 partitions. Right now, xp is the default operating system and boot up so the first question is:

1. Do I need to restore the defualt xp loader(disable grub loader or whatever)

2. Second, I want to delete the swap partition and ext3 partition and make them 1 partition and make it NTFS so I can install windows 7 on that partition.

so basically right now, my setup is 
xp (ntfs): 46.35 0B
ubuntu (ext3): 27.22 GB
swap: 981 MB

I want to make it
xp(C:\): 46.35GB (leave it alone)
E:\(or w/e drive letter it assigns)(ntfs): 28.22(the rest) GB

---

### Post by spcwingo on 2009-01-28
If you used the Ubuntu live CD to install just use it to also delete the partitions, merge them, and format the new partition.  After booting the live CD open system>admin>partition editor.  From there you can do what you have to do.  To answer your other question, you will have to use the XP CD to reinstall winldr to the MBR.  After that you should be golden.  BTW, I can't stress this enough:  ***_BACKUP, BACKUP, BACKUP!!!_***

---

### Post by caljohnsmith on 2009-01-29
You will need to restore a Windows MBR (Master Boot Record) to your HDD so you can boot straight into Windows again; you can do that by booting your Windows Install CD, go to the "recovery console" and do:
```
fixmbr
```
Or if you want, you can restore a Windows MBR from your Live CD by opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
that assumes the HDD in question is "sda", so you can change it if necessary. Once you've restored a Windows MBR, it is safe to delete the Ubuntu partitions and create an NTFS partition with that space. As spcwingo all ready mentioned, you can do that with the System > Admin > Partition Editor. Good luck and let us know how it goes.

---

### Post by Javich on 2009-01-29
Just as a headsup, you may need to run the command
```
sudo swapoff
```
otherwise you won't be able to delete your swap partition since the live cd uses the partition if you have one.

---

