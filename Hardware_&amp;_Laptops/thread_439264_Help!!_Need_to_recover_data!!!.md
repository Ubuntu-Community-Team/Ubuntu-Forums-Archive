---
title: "Help!! Need to recover data!!!"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by nick_533 on 2007-05-10
Hi all,

I am a novice with ubuntu..and just installed it on my laptop. I had two partions on my pc, 1.) 10gb C:\ where winodws works   and  2.) 20gb D:\ where I had some important files in 10gb , and the remaining 10gb was free.

I  chose auto-partition option, and Ubuntu partioned the D:\ into two parts  It installed on the free 10gb on D:\ but the other 10gb which had my files got hidden. I can not access it from windows or ubuntu.

I would really appreciate if you could tell me a way to view this hidden 10gb.

---

### Post by nick_533 on 2007-05-10
Hi all,

I am a novice with ubuntu..and just installed it on my laptop. I had two partions on my pc, 1.) 10gb C:\ where winodws works   and  2.) 20gb D:\ where I had some important files in 10gb , and the remaining 10gb was free.

I  chose auto-partition option, and Ubuntu partioned the D:\ into two parts  It installed on the free 10gb on D:\ but the other 10gb which had my files got hidden. I can not access it from windows or ubuntu.

I would really appreciate if you could tell me a way to view this hidden 10gb.

---

### Post by mikewhatever on 2007-05-10
In ubuntu, can you go to Applications>Accessories>Terminal and post the output of the command
> sudo fdisk -l

---

### Post by ajgreeny on 2007-05-10
Can you tell us the output from the command **sudo fdisk -l** in a terminal.  This will help us know if you have the partitions you think you have, and then, with a bit of luck, we can tell you how to access them.

---

### Post by nick_533 on 2007-05-10
the sudo fdisk -l displays the following

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         765     6144831    b  W95 FAT32
/dev/hda2             766        1530     6144862+   c  W95 FAT32 (LBA)
/dev/hda3            1531        3454    15454530    f  W95 Ext'd (LBA)
/dev/hda4            3455        4864    11325825   83  Linux
/dev/hda5            1531        3389    14932386   82  Linux swap / Solaris
/dev/hda6            3390        3454      522081   82  Linux swap / Solaris

---

### Post by nick_533 on 2007-05-10
hi..

the sudo fdisk -l gives the following output

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         765     6144831    b  W95 FAT32
/dev/hda2             766        1530     6144862+   c  W95 FAT32 (LBA)
/dev/hda3            1531        3454    15454530    f  W95 Ext'd (LBA)
/dev/hda4            3455        4864    11325825   83  Linux
/dev/hda5            1531        3389    14932386   82  Linux swap / Solaris
/dev/hda6            3390        3454      522081   82  Linux swap / Solaris

---

### Post by linuxhippy on 2007-05-10
it looks like your Win partitions are hda1 and hda2.  The second partition (hda2) is probably where your D drive went.  You first have to mount this if it wasn't automounted.  Open up a terminal to find out:

df -h

If /dev/hda2 has been mounted you will see which directory it's under (/media/hda2 probably).

If not you can mount it to an existing directory.

sudo mkdir /media/backup
sudo mount /dev/hda2 /media/backup


To see these files in nautilus:

sudo nautilus /media/backup or sudo nautilus /media/hda2

---

### Post by ajgreeny on 2007-05-10
Start ubuntu and then in a terminal try the commands:-
sudo mkdir /media/windows
sudo mount **/dev/hda1** /media/windows/ -t vfat -o iocharset=utf8,umask=000
for each of the partitions /dev/hda1, /dev/hda2, and /dev/hda3.  Hopefully one of them will be your partition with the files you want, and you will be able to see the files in nautilus.

It's also worth running gparted to see what that might show you

I think that hda1 is your windows 10G partition, from which you boot windows, hda2 is another fat32 10G partition with your files, I hope, but hda3 baffles me a bit as it is an extended partition, perhaps containing other virtual partitions.  Sorry I think I'm out of my depth here and need somebody else to help out further.  Try the above commands, however and you may be lucky, though I think you need to rationalise your partition arrangements somewhat.

Why have you got two swap partitions, by the way, it shouldn't be necessary and one of them looks to be huge (about 14 -15 GB)

---

