---
title: "My hard disks wakes up when I did'nt ask"
date: 2010-02-09
forum: Hardware
---

### Post by miloose on 2010-02-09
Hi there. First, sorry if my English is not perfect, but as nobody can help me on the French forum, I come here...

I'm on Karmic 64 bits.
I have three hard drives with the following configuration:
/dev/sda: IDE
/dev/sdb: IDE
/dev/sdc: SATA

Till last month, I only had the two IDE drives, but they are very noisy. So, I decided to buy a new silent drive. I plan to use the two noisy drives very occasionnaly and I do not want them to be mounted by default.
On my /dev/sdc drive, I have the following partitions:
sdc1: /
sdc6: /home
sdc5: swap
sdc3: crypted drive with my personnal data

Here is my /etc/fstab:
```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=ad03bf8b-5ce7-4c88-a7a8-b319c477def1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc6 during installation
UUID=8e6b3f56-7963-4d1e-b772-32422bfc50e5 /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=9e0396a0-e1f2-4133-8eb7-3214056d028c none            swap    sw              0       0
```

When the computer starts up, the following script is ran to ask me my password for the crypted partition and to force the other drive going to sleep:
```
#! /bin/bash
# Script to connect the crypted disks
password=`zenity --entry --hide-text --text "Entrer le mot de passe de déchiffrement du disque"`
echo "$password" | sudo /sbin/cryptsetup luksOpen /dev/sdc3 donnees
sudo mount /dev/mapper/donnees /media/donnees -l 
sleep 30
sudo hdparm -Y /dev/sda
sudo hdparm -Y /dev/sdb
exit
```
The problem is that after around 15-20 minutes, I can hear (at least one of) the noisy drive waking up. After a few minutes, it goes in standby mode (due to the fact that I checked the option in the power manager I suppose). 20 minutes later, it wakes up again, and so on.

Any idea how I tell those drive to sleep untill I manually mount them ?

Thanks a lot.

---

