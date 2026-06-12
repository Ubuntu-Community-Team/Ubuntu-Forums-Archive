---
title: "USB disk, &quot;Read only filesystem&quot; error [SOLVED]"
date: 2008-06-14
forum: Hardware
---

### Post by sande87 on 2008-06-14
I have a Western Digital 500gb USB drive. Iv been using it problem free for a while. But one day it got fickle with me and said "Read only filesystem" when I tried to delete something on it. I searched the forum and found some threads discribing similar problems, but not my problem exactly. 

I tried some of the other solutions, but they didnt work. So I tried remounting the disk, and it worked. 

I used: "sudo mount -t $FILESYSTEM /dev/$DEVICE $MOUNTPOINT -o $USER,remount"

example: "sudo mount -t vfat /dev/sdb1 /media/SANDE-o sande,remount"

$FILESYSTEM is the filesystem the parition uses
$DEVICE is the device or partition you want to remount
$MOUNTPOINT is where you want your disk remounted
$USER is your username

i also made an alias in .bashrc in /home to make things easier:
alias stupid_disk='sudo mount -t $FILESYSTEM /dev/$DEVICE $MOUNTPOINT -o$USER,remount'

use the same substitution as above. paste the line in the bottom of .bashrc in /home

PS! im fairly new to linux, so there might be some better way to do this, but this solution worked for me, so feel free to mail me for corrections and/or questions

---

