---
title: "Dual boot with two drives - which is which?"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by trainwreckof78 on 2009-02-18
I have searched through this forum and found similar stuff but not what I really want to know. Once informed I am sure it will seem simple but, I'm being safe. I have websites running on Windows and Linux servers. On my desktop I have been only running Windows. I have 2 340gb disks. Windows Vista on C:, and D: is for data/backups. D: is the drive I want to install Ubuntu on. When I boot the iso cd and proceed to install and then on to partitioning both drives show. However how do I tell which is C: or D:. They are both 320gb. Both are displayed with the same capacity and same numbers, except on has a 13 and the other a 16. Still does not help me tell which is which. Drive D: has a 100gb partition which does not show. Both Drives are formatted NTFS which I know I will have to format the partition on D: for Ubuntu. I only want to know how to tell which is which. Thank you.
Trainwreckof78

---

### Post by ssican on 2009-02-18
You will need **GParted, on the LiveCD of Ubuntu**.
For more information see this webpage:
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

See the topic,item: **-4-  Other tips ...**

EDIT:
See, also: Dualboot Two Hard Drives
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by caljohnsmith on 2009-02-18
How about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
That should show your two 340 GB drives, so choose the NTFS partition from one of them (say sda1 for example) and do:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
And that will give you a listing of the root directory of that partition. I would assume that would probably be enough to distinguish which drive has Vista and which is the D drive. Once you know which drive is which, it would be good to unmount the partition you mounted so you won't have problems with the installer:
```
sudo umount /mnt
```
Anyway, let me know how that goes or if you run into problems.

---

### Post by trainwreckof78 on 2009-02-19
Thanks for the assistance. I am reading the suggested docs and I have run GParted. I haven't made any moves yet 'cause I am trying to learn as I go and do it right without damage. I will let you know of the outcome within 24hr.

---

