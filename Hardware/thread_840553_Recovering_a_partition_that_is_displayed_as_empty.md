---
title: "Recovering a partition that is displayed as empty"
date: 2008-06-25
forum: Hardware
---

### Post by ybd on 2008-06-25
Hey.

A few days ago I was forced to reinstall Hardy because I chowned the root... unfortunately I installed it into new partitions and so had to mess around to format the old partitions and resize the new ones and reinstall Grub (with the Super Grub Disc). Unfortunately now one of my partitions (that was not touched in the partitioning process I mentioned) now displays as completely empty in Hardy, and almost empty in XP (one folder is there and the contents are completely in tact). Despite that the partition displays as almost full just like it's supposed to be in places that tell you how much free space the drive has.

I tried PhotoRec which seems to work fine, but I just don't have enough free space for it (but it gives me the impression that almost nothing is lost). I'm a bit too paranoid to use Testdisk without guidance... anyway is there any good program that I could use?

---

### Post by ybd on 2008-06-25
bump. (the thread is near the 4th page already.)

any help would be very much appreciated as always.

---

### Post by Odrodzona-Sarmacja on 2008-06-25
I think you could try to mount that partition on your new Ubuntu first. Just create some /media/tmp directory(=mount point) and mount it on it this partition. All files should return on your hd on all your mounting points of this partition. I had with this new Xubuntu 8.04 once something alike. Every file from hd just vanished. However when I just mounted it all files magically returned to the very last one. My permanent solution is to edit /etc/fstab to auto mount this partition, so contents of a hard drive will never disappear again and will always mount correctly.

I hope it will help you somehow.

---

### Post by ybd on 2008-06-25
fstab already auto mounts this partition, and this installation of Ubuntu used to work with the partition in question. Still, thanks.

Messing around a little (mounting/unmounting) allowed me to get the messages displayed in the attachment... however I tried doing that setuid root process and the drive is still "blank".

---

### Post by Odrodzona-Sarmacja on 2008-06-26
1. This looks to me like you do not have root account on this computer (it is not your computer in other words :P ).
OR
fstab is mounting this drive for root user access only with "default" value in options, which you have to change in fstab to "nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000" value in options to access this drive as user.

2.Then also I am little confused over that "external FUSE library". I am not sure exactly what is wrong with it. I would also try reinstalling all packages in synaptic manager which contain "fuse" or "ntfs" in its name or description, but i don't think it will solve the problem, as it rarely does.

I hope it helps somehow...

---

