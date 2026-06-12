---
title: "No longer able to access second harddrive"
date: 2008-05-03
forum: Hardware
---

### Post by stangdude22 on 2008-05-03
... new to ubuntu
I wasn't having any problems when I first installed ubuntu. But I was kinda annoyed by the fact that I had to select the second hard drive before any program could access it. Because of this, I typed "boot" under one of the options under preferences (it seemed like a good idea at the time, LOL) Anywho, now I just get a "cannot mount volume" message when I select it.

Seems like this was caused completely by my ignorance, but does any one have any ideas?

---

### Post by Patb on 2008-05-03
Stang. It sounds like you have set the boot option on the wrong partition.  Could you get into a terminal and post the output from:
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```
and 
```
tail -30 /boot/grub/menu.lst
```
With that information, I or someone else should be able to solve both your problems.  

Cheers, Pat.

---

### Post by stangdude22 on 2008-05-03
Got a command not found on sudo fsdisk -l

---

stangdude22@stangdude22-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

stangdude22@stangdude22-desktop:~$ tail -30 /boot/grub/menu.lst

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=A230635930633407 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=A230635930633407 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

Hopes this helps. Let me know what ya got!

Thanks!

---

### Post by Patb on 2008-05-03
Sorry, typo.  Try "sudo fdisk -l".  Cheers Pat

---

### Post by stangdude22 on 2008-05-04
> **Patb said:**
> Sorry, typo.  Try "sudo fdisk -l".  Cheers Pat

No prob! FYI, the 250gb is the main boot (with vista and ubuntu), the 500gb is the one I am having trouble with.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x050a5313

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a428619

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS

---

### Post by Patb on 2008-05-04
Sorry Stang, I'm out of my depth on this one because your system is using NTFS on both hard drives.  I am not familiar with the syntax.  

The fdisk output seems right.  The boot flag applies only to your 250G drive as shown by the * in the line:
> /dev/sda1 * 1 30402 244196352 7 HPFS/NTFS
To automatically mount your second 500G drive, you can simply create a directory where you want it to be mounted and add a line to the fstab file but I'm not certain of the syntax for an NTFS formatted partition, so I won't guess.  If it were formatted as linux ext3, the line should read something like:
```
/dev/sdb1 /media/sdb1     ext3    defaults        0       2
```
From what you have posted, I cannot see why you get the "cannot mount volume" message.  I hope someone more expert can help.  

With plenty of space as you have, you might consider a separate /home partition (guidelines [here]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") and [here]("http://www.psychocats.net/ubuntu/separatehome")) but that is another topic. 

Sorry that I can't help more.  

Cheers, Pat.

---

### Post by stangdude22 on 2008-05-04
Well I appreciate the help anyways. Hopefully someone will chime in.
Thanks again

---

### Post by stangdude22 on 2008-05-05
Anyone else got any ideas on this one?

---

### Post by TheMemphisExperience on 2008-05-06
Well...I don't know anything about all this magic terminal magic...but have you tried getting NTFS config from the add/remove applications or Synaptic package manager?

---

### Post by stangdude22 on 2008-05-06
No, haven't tried that. But I have had it working before. I'll look into that later tonight

---

### Post by stangdude22 on 2008-05-07
> **TheMemphisExperience said:**
> Well...I don't know anything about all this magic terminal magic...but have you tried getting NTFS config from the add/remove applications or Synaptic package manager?


YAY!!! don't know why it worked before? Its there now.

---

