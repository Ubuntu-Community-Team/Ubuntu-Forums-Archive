---
title: "Partioning question (spread installation on 2 disks)"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by Niniel on 2009-02-06
Hello,

I'm/was using Ubuntu on a laptop as a second OS. So when I put 7.10 ion it a while back, I had only 4.5 GB of space available, and after installing a few things I ended up with about 330 MB of free space.
Not enough to do an upgrade to a newer version.
So I decided to start from scratch with 8.10. I can't free up any more room on the hd, but I did get myself an 8 GB flash card that I want to use as a second hd. 
The question now is how to set this up.
I tried putting everything on the hd except for /home (during installation I picked / for sda2 and /home for sdb1), but the installation failed (curiously, prior to starting the installation, setup complained that there wasn't enough space on sdb1 even though it has more than 7 GB free). Then I tried putting /usr on the flash card. Failed again with a similar error about the lack of space on /usr.
I guess I'm doing something wrong here, but I don't know what. 
Any suggestions? 

Thank you.

---

### Post by taurus on 2009-02-06
Is there anything on that flash drive?  How many partitions there are on it?  Why not format it to clear out all the old stuff on it first?

---

### Post by Niniel on 2009-02-06
The partition on the flash drive should be empty, I set sdb1 to be formatted during installation. 
There is an sdb2 on the drive (500 MB) that has some stuff on in that I want to keep (a copy of my old /boot folder [for the grub boot screens])
But at this point I'm more interested in coming up with a good partitioning scheme. i.e. *should* it work when I set sda2 to / during installation and sdb1 to /usr or /home?

Update: I followed your advice and deleted all my Linux partitions, and then set them up anew, but I'm still getting an error claiming that the /usr partition on sdb1 is too small. I'm not getting a recommended size though.
Update: Hm, according to [this guide]("http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install") my setup was correct, except that I didn't create a separate /boot partition.

Update: Maybe the CD had errors (even though the error checker didn't find any). Anyway, I used an alternate installation CD to get a base system - since that disk was also not error free (3rd broken disk) I have to pull applications down from the internets. 
Oh well, at least it's working now. Still have to do the wireless setup but that shouldn't be too bad.

---

