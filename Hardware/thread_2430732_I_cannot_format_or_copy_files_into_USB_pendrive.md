---
title: "I cannot format or copy files into USB pendrive"
date: 2019-11-06
forum: Hardware
---

### Post by ppbiju on 2019-11-06
I have tried to format the usb pendrive from disk and found the format menu is not active then i tried 
 fdisk -w /dev/sdb  and get
fdisk: cannot open /dev/sdb: Permission denied

after that i isssued the following command and got the result as follows 
 dmesg | tail
[ 1180.713494] usb-storage 2-2:1.0: USB Mass Storage device detected
[ 1180.714416] scsi host3: usb-storage 2-2:1.0
[ 1181.722536] scsi 3:0:0:0: Direct-Access     Generic  Flash Disk       8.07 PQ: 0 ANSI: 4
[ 1181.723656] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1181.724290] sd 3:0:0:0: [sdb] 30720000 512-byte logical blocks: (15.7 GB/14.6 GiB)
[ 1181.724933] sd 3:0:0:0: [sdb] Write Protect is on
[ 1181.724934] sd 3:0:0:0: [sdb] Mode Sense: 23 00 80 00
[ 1181.725588] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1183.141171]  sdb: sdb1
[ 1183.144160] sd 3:0:0:0: [sdb] Attached SCSI removable disk


please help

---

### Post by CatKiller on 2019-11-06
> **ppbiju said:**
> 
[ 1181.724933] sd 3:0:0:0: [sdb] Write Protect is on

That's generally a physical slider to protect the contents of the drive.

---

### Post by Skaperen on 2019-11-06
did you slide it to the off position and try again?

---

### Post by #&amp;thj^% on 2019-11-06
also wouldn't hurt to see what shows with:
```
ls -l /dev/sd*
```

---

### Post by ppbiju on 2019-11-06
the pendrive do not have a physical slider

---

### Post by ppbiju on 2019-11-06
> **1fallen said:**
> also wouldn't hurt to see what shows with:
```
ls -l /dev/sd*
```



I have got the following output


brw-rw---- 1 root disk 8,  0 Nov  7 08:49 /dev/sda
brw-rw---- 1 root disk 8,  1 Nov  7 08:49 /dev/sda1
brw-rw---- 1 root disk 8, 10 Nov  7 08:49 /dev/sda10
brw-rw---- 1 root disk 8, 11 Nov  7 08:49 /dev/sda11
brw-rw---- 1 root disk 8,  2 Nov  7 08:49 /dev/sda2
brw-rw---- 1 root disk 8,  3 Nov  7 08:49 /dev/sda3
brw-rw---- 1 root disk 8,  4 Nov  7 08:49 /dev/sda4
brw-rw---- 1 root disk 8,  5 Nov  7 08:49 /dev/sda5
brw-rw---- 1 root disk 8,  6 Nov  7 08:49 /dev/sda6
brw-rw---- 1 root disk 8,  7 Nov  7 08:49 /dev/sda7
brw-rw---- 1 root disk 8,  8 Nov  7 08:49 /dev/sda8
brw-rw---- 1 root disk 8,  9 Nov  7 08:49 /dev/sda9
[B]brw-rw---- 1 root disk 8, 16 Nov  7 08:55 /dev/sdb
brw-rw---- 1 root disk 8, 17 Nov  7 08:55 /dev/sdb1[/B]

---

### Post by C.S.Cameron on 2019-11-06
I have seen this a few times, sounds like your pendrive is dead, if you are lucky it may be read only to the existing data.
I have a SD card that I use as a server that went read only, but still works as a server booted toram.

---

### Post by #&amp;thj^% on 2019-11-06
See if this helps: [https://sharadchhetri.com/2013/12/19/how-to-fix-read-only-usb-pen-drive-in-ubuntu/](https://sharadchhetri.com/2013/12/19/how-to-fix-read-only-usb-pen-drive-in-ubuntu/)

---

### Post by ppbiju on 2019-11-07
> **1fallen said:**
> See if this helps: [https://sharadchhetri.com/2013/12/19/how-to-fix-read-only-usb-pen-drive-in-ubuntu/](https://sharadchhetri.com/2013/12/19/how-to-fix-read-only-usb-pen-drive-in-ubuntu/)


I have tried but get only the following out put


~$ sudo su -
[sudo] password for biju:         
:~# df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     790M  1.5M  789M   1% /run
/dev/sda8      ext4       46G   36G  7.8G  83% /
tmpfs          tmpfs     3.9G  105M  3.8G   3% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     790M   44K  790M   1% /run/user/1000
/dev/sdb1      vfat       15G  2.6G   13G  18% /media/biju/bkup
tmpfs          tmpfs     790M     0  790M   0% /run/user/0
:~# umount /media/biju/bkup 
:~# dosfsck -a /dev/sdb1
fsck.fat 4.1 (2017-01-24)
open: **Read-only file system**

pl. help

note : I have used this pendrive to create bootable disk by using _startup disk creator_ one or more times with ubuntu 18.04 after that  I just formatted by right clicking on nautilus and copied the iso after that the disk become readonly.  ie. I have used only 3 / 4 times after getting it.  Is there is any way to factory reset this pendrive

---

### Post by #&amp;thj^% on 2019-11-07
Well then that's not very encouraging, I have only one suggestion now, Download a Gparted iso found here: [https://gparted.org/livecd.php](https://gparted.org/livecd.php).
Now this may prove to be a challenge if you don't have a source to burn it to. IE: USB/CD/DVD.
If you do, boot to it (Gparted) and see if that will sort it out. (A Re-format is what your after) this is my preferred method. **_***Be careful to pick the USB Drive and not your Installed OS._**
If your unable to burn and boot to the Live Gparted session, try to install it in your current Desktop:
```
sudo apt install gparted
```
I have seen for whatever reason Gnome-Disk tool have the same results as your now seeing.(Read Only)
Good Luck

---

### Post by ppbiju on 2019-11-08
> **1fallen said:**
> Well then that's not very encouraging, I have only one suggestion now, Download a Gparted iso found here: [https://gparted.org/livecd.php](https://gparted.org/livecd.php).
Now this may prove to be a challenge if you don't have a source to burn it to. IE: USB/CD/DVD.
If you do, boot to it (Gparted) and see if that will sort it out. (A Re-format is what your after) this is my preferred method. **_***Be careful to pick the USB Drive and not your Installed OS._**
If your unable to burn and boot to the Live Gparted session, try to install it in your current Desktop:
```
sudo apt install gparted
```
I have seen for whatever reason Gnome-Disk tool have the same results as your now seeing.(Read Only)
Good Luck

I have downloaded the live Gparted iso burn it to another pendrive and booted with it then check the faulty pendrive but found Read only error.   I tried with Disk tool also but it is found that the format menu is not active 

is there any other way to recover it

---

### Post by oldfred on 2019-11-08
If you have no data to recovery, you may be able to zero out boot block?

Reset USB flash that was dd'd to make it usable again
[https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266](https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266) & 
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

---

### Post by sudodus on 2019-11-08
We don't know yet, if it is a hardware problem or a software problem. You can analyze it according to the following link

[Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

and if you are lucky, get a working USB pendrive again.

---

### Post by ppbiju on 2019-11-09
I have used mkusb and tried to [COLOR=#000000][FONT=arial]Wiping the first megabyte (MibiByte) of /dev/sdb ... :[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]... Failed :-(


[/FONT][/COLOR] I am using credit card type pendrive is this one have any protective notch or some mechanism to protect write 
As it is plain design I am not able to find anything like that

---

### Post by sudodus on 2019-11-09
I'm sorry, it seems your USB pendrive is damaged beyond repair, when it does not allow wiping the first mibibyte.

---

### Post by ppbiju on 2019-11-15
I have one more doubt 
I have copied two iso images of Ubuntu into the pendrive before it gets readonly  the files  reads well.  I can copy it to any where without any errors.  
if the pendrive is damaged then how I can copy the files.  The problem is that I can't copy any thing to it or deleting the existing files and of-course I can't format it...

---

### Post by sudodus on 2019-11-15
If you tried with mkusb to wipe the first mibibyte of the pendrive, and it failed, I don't think it will be possible to write an iso image or anything else. I think that the drive failed after those two iso images were written.

The flash memory hardware and the electronics of pendrives are mass produced and if you have bad luck, it will not last for a long time. The problem was *probably* not that two iso images were written, anything might have been written. You reached the point when too many memory cells were damaged, there were no more spare cells to replace those that were failing.

The following link and links from it may help explaining what happened,

[Pendrive lifetime](https://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

