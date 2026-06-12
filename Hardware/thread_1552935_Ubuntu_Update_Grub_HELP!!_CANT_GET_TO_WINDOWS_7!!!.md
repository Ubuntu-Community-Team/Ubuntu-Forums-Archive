---
title: "Ubuntu Update Grub HELP!! CANT GET TO WINDOWS 7!!!"
date: 2010-08-14
forum: Hardware
---

### Post by tdrunner95 on 2010-08-14
HELP!!!!!! i was updating my ubuntu 10.4, when it asked me if i wanted to install some grub thing. Being Stupid, i did. When it was time for me to restart, my Laptop (Toshiba Satellite L455-S5975 running Windows 7) came up with a grub error saying "device not found or something". i cant boot my windows 7 partition or my recovery partition (i think they may have been deleted). PLEASE PLEASE PLEASE!!! can somebody give me some insight on what i should do, if you dont know what i should do, can you please give me a link where i could possibly, get the real backup disks. PLEASE HELP!!!! Also if i insert the ubuntu disc and install it again, should that error message go away, and i would just have ubuntu, because right now im thinking i should do that.
 
the reason why i am in desperate need of help is, if my parents find out..... IM DEAD!!!!

---

### Post by tadaskr on 2010-08-14
well, I had that problem when played too much with ubuntu terminal. And i fix that by deleting windows partition installing windows then ubuntu. If you don't install ubuntu, you just don't find way to load ubuntu
Good luck :)

---

### Post by ajgreeny on 2010-08-14
Start by running the ubuntu live CD and then in terminal run ```
sudo fdisk -l
``` to see what is on the hard disk.  That will tell us whether or not windows and the recovery partition still exist.

I am assuming this is a full partitioned install of ubuntu we are dealing with, and not a wubi install, where the live CD was run from inside windows, and ubuntu installed as if it were another windows application.  The command above should give us a clue about that as well, so let's wait and see before anything is done that causes even greater problems.

---

### Post by bcbc on 2010-08-14
> **tdrunner95 said:**
> HELP!!!!!! i was updating my ubuntu 10.4, when it asked me if i wanted to install some grub thing. Being Stupid, i did. When it was time for me to restart, my Laptop (Toshiba Satellite L455-S5975 running Windows 7) came up with a grub error saying "device not found or something". i cant boot my windows 7 partition or my recovery partition (i think they may have been deleted). PLEASE PLEASE PLEASE!!! can somebody give me some insight on what i should do, if you dont know what i should do, can you please give me a link where i could possibly, get the real backup disks. PLEASE HELP!!!! Also if i insert the ubuntu disc and install it again, should that error message go away, and i would just have ubuntu, because right now im thinking i should do that.
 
the reason why i am in desperate need of help is, if my parents find out..... IM DEAD!!!!
Don't panic. Don't reinstall anything. This is a Wubi install (you installed ubuntu from within Windows), right? You just need to restore the windows bootloader.

If you have the windows disks, refer to this howto to reinstall the windows bootloader: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

It's also possible to fix it from a live CD, which is useful if you don't have the windows disks:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

here is the bug report: [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

---

### Post by tdrunner95 on 2010-08-14
> **bcbc said:**
> Don't panic. Don't reinstall anything. This is a Wubi install (you installed ubuntu from within Windows), right? You just need to restore the windows bootloader.
 
If you have the windows disks, refer to this howto to reinstall the windows bootloader: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 
It's also possible to fix it from a live CD, which is useful if you don't have the windows disks:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
 
here is the bug report: [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)
 
when i put this first line of code in, it gives me a yes or no optition, what do i put

---

### Post by pikipadfoot on 2010-08-14
hi guys, i have the same problem. im an ubuntu newbie and i kinda just clicked away... 
i tried doing what u guys were saying in another thread where i load it using the USB and it did load and i tried typing the sudo lilo code, and typed yes. the second code came back with a: lilo not installed.. or something.. what do i do from here?

---

### Post by bcbc on 2010-08-14
> **pikipadfoot said:**
> hi guys, i have the same problem. im an ubuntu newbie and i kinda just clicked away... 
i tried doing what u guys were saying in another thread where i load it using the USB and it did load and i tried typing the sudo lilo code, and typed yes. the second code came back with a: lilo not installed.. or something.. what do i do from here?

There must have been an error installing lilo. Make sure you are connected to the internet. Try the first line again and copy and paste the output back here.

---

### Post by pikipadfoot on 2010-08-14
ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main mbr 1.1.10-2 [23.0kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main lilo 1:22.8-8ubuntu1 [390kB]
Fetched 413kB in 8s (46.7kB/s)                                                 
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 129801 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian


ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.

heeey it worked.. i think.. is this whats supposed to happen? 
i really appreciate this.

---

### Post by wilee-nilee on 2010-08-14
I think the W7 recovery ISO can be used to run fixboot or fixmbr.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Try the highlighted command, and use the http for help if needed.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

This is just information, bcbc knows the best way to approach this sort of grub situation.

---

### Post by bcbc on 2010-08-14
> **pikipadfoot said:**
> ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main mbr 1.1.10-2 [23.0kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main lilo 1:22.8-8ubuntu1 [390kB]
Fetched 413kB in 8s (46.7kB/s)                                                 
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 129801 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian


ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.

heeey it worked.. i think.. is this whats supposed to happen? 
i really appreciate this.

Yes, that's right. just reboot.

---

### Post by pikipadfoot on 2010-08-14
yeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeey
THANK YOU BCBC!!!!
(im bowing before my screen)
:-p

---

### Post by tdrunner95 on 2010-08-14
> **bcbc said:**
> yes, that's right. Just reboot.
 omg omg omg thank you so much, thank you so much!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by bcbc on 2010-08-14
You are welcome :)

---

