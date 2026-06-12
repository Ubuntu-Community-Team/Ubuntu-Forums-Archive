---
title: "[SOLVED] help! no operating system found"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by mpc350 on 2008-12-02
just got a lenovo ideapad y530 that came with vista, and downloaded and ran ubuntu from the live cd.  ran the guided partitioning -- left 110gb for ubuntu, 70gb for vista.  installation semed to go fine, but upon restart, got  the message 

'no operating system found'

rebooted from the live cd and ran fdisk -l and got:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9158    73561603+  83  Linux
/dev/sda2            9159       28475   155163802+   f  W95 Ext'd (LBA)
/dev/sda3           28476       30402    15471800   12  Compaq diagnostics
Partition 3 does not end on cylinder boundary.
/dev/sda5           24666       28475    30603793+   7  HPFS/NTFS
/dev/sda6            9159       24030   119459277   83  Linux
/dev/sda7           24031       24665     5100606   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dbae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7115    57151206   83  Linux
/dev/sdb2            7116        7297     1461915    5  Extended
/dev/sdb5            7116        7297     1461883+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

any ideas?

---

### Post by lisati on 2008-12-03
You might have to re-install GRUB (which helps manage the loading of the OS you wish to run)

One way is with the use of [supergrub]("http://www.supergrubdisk.org/")

---

### Post by caljohnsmith on 2008-12-03
You have linux partitions on both sda and sdb, so do you have different distros installed on each drive? Do you know which drive you are booting on start up? Also, I notice that your Vista partition is sda5, or a logical partition; was Vista installed to sda5, or did you move it there? 

How about posting the following output:
```
sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
sudo xxd  -l  2 -p /dev/sdb
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
Note that "-l" is a lowercase L, not a one. Also please post the output of:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
grub> quit
```

---

### Post by mpc350 on 2008-12-03
ubuntu@ubuntu:~$ sudo xxd  -l  2 -p /dev/sda
33c0
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
0000
ubuntu@ubuntu:~$ sudo xxd  -l  2 -p /dev/sdb
xxd: /dev/sdb: No such file or directory
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sdb
xxd: /dev/sdb: No such file or directory



       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> grub> find /boot/grub/stage1

Error 27: Unrecognized command

grub> grub> find /grub/stage1


I am suspecting what happened is that I loaded grub to the vista bootloader partition instead of its' own partition.  Does this sound right, and how can I fix it?

---

### Post by caljohnsmith on 2008-12-03
OK, I believe I see the problem; your sda drive still has a Windows MBR, and yet your Linux partition is the one with the boot flag. That setup unfortunately won't work unless you install Grub to the boot sector of the linux partition. But the easiest way is to just install Grub to the MBR and let it handle the booting process, but please do those Grub commands again from my previous post, but do not include the "grub>" prompt when copying/pasting them. Also, what is on your linux partitions sda1, sda6, and sdb1?

---

### Post by mpc350 on 2008-12-03
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> 

grub> find /grub/stage1

Error 15: File not found

I'm not sure how to find out what's on the partitions you asked for.

---

### Post by mpc350 on 2008-12-03
[IMG]http://file:///home/ubuntu/Desktop/gparted%20screenshot[/IMG]

hope this worked... tried to upload a screen shot of gparted to show the uses of my various partitions

---

### Post by mpc350 on 2008-12-03
trying one more time

---

### Post by mpc350 on 2008-12-05
I got frustrated and just completely wiped the drive, installed Ubuntu, and will lay Vista over it.

Oh well

---

### Post by razy60 on 2008-12-05
should have done it the other way round if you wanted to keep windows,(i think) as you will have to reinstall grub as windows will over write the mbr.

Raz

---

### Post by mpc350 on 2009-01-04
Windows (to my understanding) does mess up the MBR, but I can go back and tell grub to take back over the MBR and include windows as a grub boot option.  I tried to make it dual boot with easyBCD, but was completely unsucessful-- tried everything.  So I went back and told grub that it was the bootloader and added windows as an option.  In practice, this works very well for me.

---

