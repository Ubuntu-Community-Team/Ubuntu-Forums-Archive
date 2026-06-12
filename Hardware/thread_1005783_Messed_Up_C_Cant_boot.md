---
title: "Messed Up C:/ Cant boot"
date: 2008-12-08
forum: Hardware
---

### Post by C.U.B.E.M.A.N on 2008-12-08
First of all, i know there are lots of threads about this, but in all of them, they have a working windows install, and i dont. And also sorry for spelling, the keybord layout is not fixed.

So, i was messing around with some mac install , and shut down before i started to install. i booted up vista afterwards, and everything seemed to work, but after another reboot, vista did not boot properly, and just showed a black screen with a cursor after the boot screen. i have tryed to run vista recovery, but it finds nothing. When i try to boot up my wubi ubuntu, i get a error about unclean shoutdown, and that i need to go to windows and run the chkdsk f command, which i cant.

So i boot up the live cd, go to gparted, and checks the hd. i get the following

```
GParted 0.3.8

Libparted 1.8.9

Check and repair filesystem (ntfs) on /dev/sda2  00:00:11    ( ERROR )
     	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
     	
path: /dev/sda2
start: 20980890
end: 323062937
size: 302082048 (144.04 GiB)
check filesystem on /dev/sda2 for errors and (if possible) fix them  00:00:11    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 154666004992 bytes (154667 MB)
Current device size: 154666008576 bytes (154667 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 387828 (0x5eaf4): extra cluster in $Bitmap
Cluster accounting failed at 387829 (0x5eaf5): extra cluster in $Bitmap

Cluster accounting failed at 490858 (0x77d6a): extra cluster in $Bitmap
Cluster accounting failed at 490859 (0x77d6b): extra cluster in $Bitmap
Cluster accounting failed at 490860 (0x77d6c): extra cluster in $Bitmap
Cluster accounting failed at 490861 (0x77d6d): extra cluster in $Bitmap
Cluster accounting failed at 490862 (0x77d6e): extra cluster in $Bitmap
Cluster accounting failed at 490871 (0x77d77): extra cluster in $Bitmap
Cluster accounting failed at 490872 (0x77d78): extra cluster in $Bitmap
Cluster accounting failed at 490873 (0x77d79): extra cluster in $Bitmap
(lots of more of this kind of messages)
Cluster accounting failed at 5884707 (0x59cb23): extra cluster in $Bitmap
Filesystem check failed! Totally 878 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.
```

So how can i run a command similiar to chkdsk f trough the ubuntu live cd?
or is there any other way to solve this...

A quick reply would be VERY nice
[-o<

---

### Post by Addiction2Code on 2008-12-08
Well, it looks like your hard drive has bad blocks, I know you can run fsck under Ubuntu, for an automatic repair type at the terminal fsck -p and see if that helps.

---

### Post by C.U.B.E.M.A.N on 2008-12-08
> **Addiction2Code said:**
> Well, it looks like your hard drive has bad blocks, I know you can run fsck under Ubuntu, for an automatic repair type at the terminal fsck -p and see if that helps.

Your command only returns 

ubuntu@ubuntu:~$ fsck -p
fsck 1.41.3 (12-Oct-2008)

What is the parameters for fsck?

---

### Post by pastalavista on 2008-12-08
Download and burn a [SuperGrub]("http://www.supergrubdisk.org/") disk. It will fix your grub so Windows will boot if it is bootable. If it's not bootable, you'll need your Windows Installation disk to repair the MBR and whatever else may be wrong with Windows and then run the SuperGrub disk again to make it dual-boot.


I believe (not sure) Wubi is similar to grub in the tools available, except for running in Windows. But forget I told you about SuperGrub unless you ever decide to do an actual dual-boot. The Windows disk is your best hope.

---

### Post by caljohnsmith on 2008-12-08
If you don't have a Windows Vista Install CD, you can instead download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). I would boot that, go to the command line and do:
```
bootrec /rebuildbcd
chkdsk /r
```
And run the chkdsk as many times as it takes until it reports no errors. After that reboot, and let me know how far you get booting Vista. We can work from there if you want.

---

### Post by C.U.B.E.M.A.N on 2008-12-17
Thanks, fixed with the vista recovery cd, that suddenly found out that my hard drive was broken :)

---

