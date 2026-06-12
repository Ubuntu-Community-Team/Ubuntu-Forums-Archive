---
title: "Multiple OS, Bootloader how to?"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by draperdt on 2009-08-02
Hi,

My initial OS = Linux Mint KDE 7.

I got a copy of windoze 7 and I wanted to test it. So I created a NTFS partition using Gparted live cd and then I installed the other OS. Now I messed up since I cant get to the Mint 7 bootloader. 

What can I do to make my desktop give me options to choose an OS? Where is this file and what should I edit to make it do that.

I dont have the Mint 7 DVD handy but I do have a fedora 10 DVD. I put the DVD in, went to "Rescue Installed OS.." and went to command prompt.

At the command prompt fdisk gave me the following info:

Disk /dev/ssda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 x 512 = 8225280 bytes
Disk identifier : 0xbab2bab2

Device Boot Start End Blocks Id System
/dev/sda1 1 25496 2047965884 83 Linux
/dev/sda2 * 25497 29650 33367005 7 HPFS/NTFS
/dev/sda3 29651 30401 60324074 5 Extended
/dev/sda5 29651 30401 60324074 5 Swap

Thanks in advance.

---

### Post by merlinus on 2009-08-02
Assuming you were using grub, try this from a terminal whilst running a live cd:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```Remove the cd and restart.

---

### Post by draperdt on 2009-08-02
Perfect, worked like a charm. Thanks.

---

### Post by merlinus on 2009-08-02
Excellent!  For future reference, anytime you install any flavor of windows after linux, it will write itself to the mbr.  You can then use this method to reinstall grub.

---

