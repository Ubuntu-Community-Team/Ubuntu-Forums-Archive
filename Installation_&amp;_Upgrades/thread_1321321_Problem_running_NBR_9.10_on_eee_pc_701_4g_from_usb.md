---
title: "Problem running NBR 9.10 on eee pc 701 4g from usb"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by Aane on 2009-11-09
I am having problems running Ubuntu 9.10 netbook remix from a 4Gb usb drive on my eee pc 701 4g (512 Mb RAM).  I downloaded the ISO onto a Windows desktop and used UNetbootin to put the files on the usb stick.  When I try to boot the eee pc with the usb drive, I see the Ubuntu screen for a few seconds.  Then the screen goes black and the round curser spins and spins.  AFter 20 minutes with nothing else happening, I give up.  

Does anyone have any suggestions?  (I did use WinMd5sum to verify the ISO download).  I have looked at the instructions on the Ubuntu NBR download about using usbcreator to create the usb bootable drive, but I don't fuly understand the instructions.  I also downloaded  win32diskimager, but it only works with IMG files not the ISO file.

I have read where others have been able to get ubuntu 9.10 on their 701's and am jealous of their success.  Is the fact that I still use the original 512 MB RAM a problem?  Or is the 7" screen and display resolution just too small?

Thanks in advance for any advice.

---

### Post by efflandt on 2009-11-10
Do you have Ubuntu on any computer?  **System, Administration, USB Startup Disk Creator** effortlessly installs a live installation iso on USB.  I did it with Ubuntu 64-bit to install that on one partition and 32-bit for another partition to compare them.

At the moment I am running 32-bit Unbuntu 9.10 on a company laptop from 4 G USB stick.  With the CD data and 2.1 G reserved for persistent data (including settings, other installed packages for media and Firefox plugins, I still have 1.6 G free space on the Linux file system and 1 G vfat space if I want to put anything onto it from Windows.  I guess the 4G USB is mounted on /cdrom because that is where the install would expect to find it.

```
efflandt@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  2.1G  414M  1.6G  21% /
udev                  501M  284K  501M   1% /dev
/dev/sdb1             3.8G  2.8G 1000M  74% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  501M  344K  501M   1% /dev/shm
tmpfs                 501M   28K  501M   1% /tmp
none                  501M   96K  501M   1% /var/run
none                  501M  4.0K  501M   1% /var/lock
none                  501M     0  501M   0% /lib/init/rw

efflandt@ubuntu:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x00044144

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3913161    b  W95 FAT32

efflandt@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        927         73          0        106        564
-/+ buffers/cache:        256        744
Swap:            0          0          0
```So maybe the method you are using is not quite doing it properly.

---

### Post by Aane on 2009-11-11
I solved my problem and have been able to run Ubuntu NBR 9.10 live from usb.  I found additional instructions on the ubuntu help site:
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media) about what do to after using unetbootin to put the iso image files on a usb stick.

The following additional steps were taken, making changes to the usb drive files:

1.  Delete syslinux.cfg file or rename it to syslinux.old

2.  Enter isolinux folder and rename isolinux.cfg file to be syslinux.cfg.  Rename isolinux.bin to syslinux.bin.

3. Move to top level and rename the isolinux folder to be syslinux.

These changes enabled the ununtu live cd boot menu, and from there I was able to run nbr 9.10 live from usb.  It runs very well.  I enabled my wireless connection.  It looks really slick.  Everything fits on my 701's 7 inch screen.   

Aane Aaby

---

### Post by Aane on 2009-11-11
Oops.  Although I was able to run a live version of NBR 9.10 on my eee pc one time, I have since been unable to do it again.  The next time I tried to run off the USB, I got an endless series of repeating error messages.  The next two times, I got only the black screen with the rotating white disk.

I had created the bootable usb stick using unetbootin.  I can't figure out why it worked once but won't work now.  This is frustrating for someone who doesn't use ubuntu regularly (my eeepc runs on the original xandros).

The earlier respondant said I should use the usbcreator program that is part of the NBR ISO.  Do I need to burn the NBR ISO to a cd and run NBR live on my windows desktop.  Or can I use the ubuntu 9.04 cd I made earlier this year and select the NBR 9.10 ISO while running 9.04 live?

Thanks for any suggestions.

Aane Aaby

---

### Post by paxmark1 on 2009-11-12
There is one ubuntu variant that was extremely focused on the 701'a and 900's of the eee.  It is called crunch bang linux.  You could try a live usb of that.  It even had a kernel called cruncheee.  It has evolved to be usable for all sorts of computers, but it will probably always have an affinity for netbooks and the eee's

The kernel comes from [http://array.org/ubuntu/](http://array.org/ubuntu/)

Easypeasy, eeebuntu and crunchbang all are netbook orientated and ubuntu based.  

Some people have had problems with the liveusb programs on the 9.10 version of Ubuntu. Crunchbang will be at 9.04 for a few more months probably.  It is very fast and nimble, being based on the minimalist Openbox instead of Gnome or KDE.  If you have a spare usb stick, download the iso and put it on a stick and try it out if you are still having problems.  

peace,  mark

---

