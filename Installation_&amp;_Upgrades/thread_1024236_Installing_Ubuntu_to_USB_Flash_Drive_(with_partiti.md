---
title: "Installing Ubuntu to USB Flash Drive (with partitions)"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by nosoupforyou on 2008-12-28
Firstly I'm completely new to gnu/linux and this is my first post so Hi, I hope this question isn't too noobish (I read a ton of documentation) I am  mainly a windows user but decided to try a live cd on an old PC before trashing it. Now I'm becoming closer to 60/40 and I like the idea of using a USB (8GB, 25MB/s read/write for $30!) to keep my OS with me on the go since all my non-geek friends have horribly bloated PCs.

 Basically, my problem is when I install ubuntu to my usb drive (sandisk 8gb cruzer contour) I cannot access any files on my usb drive outside of the casper-rw (I believe it is called) file that is set to a predetermined size when creating a usb-boot disk using the tool included in ubuntu 8.10. 

 I thought creating another partition would work since I cannot mount the usb drive that ubuntu is installed on in ubuntu. This way I can keep ubuntu and the casper-rw file on one partition and all my documents I want available on the drive for both ubuntu and windows on the other partition. Will this solve my problem or is there a better way, everywhere I looked stated that you cannot create multiple partitions on a usb flash drive, or at least have both partitions visible in windows. 

 The only option that seems plausible is that my drive came with U3 so I have two partitions on my flash drive, one that is meant to look like a CD, could I re-size these partitions and install ubuntu on one of them and since the second partition is made to look like a CD drive, will that mean it will boot in a bios that can check for cds but not usbs? I am guessing no since it is probably only formatted with CDFS but I don't know too much about that topic.

-Also, is it possible to re-size the casper-rw file after installing ubuntu or does this require you to reinstall ubuntu?
-Is it possible to upgrade ubuntu to 9.04 when it is released on the usb drive or will this require me to re-install it?
-To increase the life the of the usb drive by reducing the number of read/write cycles, is it possible to keep the casper-rw file in ram (I have 3gb) and only write to the usb on shutdown or does it already write to the usb infrequently enough/the number of read/write cycles for usb drives is so large I don't need to worry about this?

Thanks to anyone who helps!

-Off topic and unimportant but will Python 3.0 be available by default in 9.04 or at least installed by default parallel to Python 2.x?

---

### Post by 67GTA on 2008-12-29
The usb creator tool only installs a "Live CD" version. There are no users, or user folders. You can plug in your USB before running the installer, and actually install a regular install by selecting the USB stick during the partitioner screen. That way, the USB stick will be just like a hard drive install.

---

### Post by snowpine on 2008-12-29
67GTA's advice is pretty good, but there is one very important step missing.

If you choose a full install to a USB device, you need to install the Grub bootloader to that device, not to your internal hard drive. When you get to the final step 7 of the installer, click Advanced Options and choose to install Grub on the correct device (for example /dev/sdb).

---

### Post by Pumalite on 2008-12-29
Check this too:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by nosoupforyou on 2008-12-29
Thanks for all your replies!
I still can't make it so the files on the usb can be accessed by both ubuntu and windows but I'm pretty happy with the setup I used.

Here's the setup for anyone who wants to partition the usb to work in both windows and ubuntu (they still can't access each other's partitions) 
First partition (sdb1, I believe) - 2600mb FAT 32, /windows, Primary
Second partition (sdb2) - 5124mb Reiser File System, /, Primary
Last Partition, Swap Space, ~450mb (can't remember exact amount or what the total available memory was after formatting)

I'm just wondering, would it have been possible for me to format the entire thing with FAT32 or NTFS (keeping swap space at the end) and install ubuntu on it so the entire ubuntu partition is readable in windows?

edit: Do I need to have have a partition to use as swap space since it is a USB install, what effect does it have on the speed and won't it wear out the usb by constantly re-writing to the same bytes?

---

### Post by nosoupforyou on 2008-12-30
I don't know if it has something to do with me removing U3 from the usb drive but after a complete format into FAT32, I tried the live USB installer again and I was able to successfully access the files in the linux user's homefolder which are stored in the casper-rw file and the other files that are accessible via windows!
edit: now it doesn't anymore, maybe I forgot to take the dvd out of the drive? but I remember having to specifically tell the bios on every boot to go to the usb first instead, oh well.

The only cons to the live usb install now is the fact that you are logged in as a live user and have to go through the live boot menu every time. I may submit this idea to brainstorm later for an actual USB installer that uses the same method as the live usb creator but actually installs it to the USB as a regular user.

---

