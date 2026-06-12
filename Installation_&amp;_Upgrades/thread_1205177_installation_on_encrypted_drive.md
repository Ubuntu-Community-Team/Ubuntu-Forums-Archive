---
title: "installation on encrypted drive"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by hix3r on 2009-07-05
Hello!

I have tried to install ubunt 9.04 x64 version on my computer.
I have a
160 GB SATA drive
200 GB SATA drive
40 GB PATA drive.

Now my plan was this. Partition the 160 GB drive into a 40 and a 120 sized one. Install Windows XP x64 on the 40 GB partition. This was successful.

Now I got the ubuntu alternate installer. Booted up, and configured the drives as I saw one tutorial on setting up kubuntu with encryption. I want to install ubuntu on the 40 GB PATA drive. It was something like this:

I made an ext3 300 MB partition with boot flag on, and mounted as /boot.
I set the rest up as partition for encryption.
I configured the encryption settings.
I took the encrypted volume and set it to be used as a partition for LVM.
I created a volume group with three volumes. 20 GB ext4 as "/", 2 GB as swap area, the rest as ext4 "/home".
At the end I took the space from the 160 GB SATA drive, which was not the windows xp partition (120 GB), and took the other 200 GB drive, set them up in LVM as ONE volume and set it to ext4 and mounted as a custom labeled "/data".
This was not encrypted, only the 40 GB PATA drive was encrypted except the /boot partition there.

Now install was successful, but when the computer reboots, I get "Error loading operating system" and stop. I can't get to ubuntu nor windows. What can I do?

BTW this is a link to the tutorial I followed. So basically I set the 40 GB PATA drive up exactly like this!
[http://www.youtube.com/watch?v=BEr1ChbZhEM](http://www.youtube.com/watch?v=BEr1ChbZhEM)

---

### Post by hix3r on 2009-07-06
Okay, I managed to solve the problem by getting rid of the 40 GB drive, so far so good. Now I made a 60 GB partition on the 200 GB drive for XP and combined the other hard drive and the remaining space in LVM, to a big 280 GB partition. Made that for encryption, divided up to root, home, swap. Now it is working however GRUB does not show XP. So I searched around, and made this. This is how my partitions look:

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94673aad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2              25       19929   159886912+   5  Extended
/dev/sda5              25       19929   159886881   8e  Linux LVM

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb7bdb7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7833    62918541    7  HPFS/NTFS
/dev/sdb2            7834       24792   136223167+   5  Extended
/dev/sdb5            7834       24792   136223136   8e  Linux LVM

And this is how the end of my GRUB menu.lst looks like:

# (2) Windows XP
title Windows XP Professional x64 Edition
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

So what am I doing wrong? When I choose the option XP in GRUB it says NTDLR missing, press Crtl+Alt+Del to restart.

---

