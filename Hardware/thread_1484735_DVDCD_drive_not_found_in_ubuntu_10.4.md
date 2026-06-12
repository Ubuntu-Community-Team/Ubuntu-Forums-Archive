---
title: "DVD/CD drive not found in ubuntu 10.4"
date: 2010-05-16
forum: Hardware
---

### Post by igodspeed on 2010-05-16
Hello,
I am very new to linux. I own a dell inspiron 1500. I cannot see the dvd icon anywhere or be able to access any of its resources. I tried using many different dvds and cds but still there does not seem to be any activity. think i may need to modify my fstab file. currently this is how the fstab file looks:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0 
```If someone could please tell me what i should add here it would be greatly appreciated. The snapshot of sudo lshw -C disk is attached to this post. If there is any other information you may need, please let me know. Please help me get my dvd drive on my new computer to start working. 
Thanks for your help

---

### Post by igodspeed on 2010-05-17
No replies?

---

### Post by greenchilli on 2010-06-06
I have the same issue this morning - Just trying to create an ISO image from command line, but device not found. 

Normally I would just do the following. 

cat /dev/sr0 > /home/user/Videos/DVD.iso

...but I get the message "No medium found"

It worked before, but not today. Normally one can see all devices/file systems from System Monitor/File Systems tab. But nothing there...


I can see the device:
:~$ ls -l /dev/sr0 
brw-rw----+ 1 root cdrom 11, 0 2010-06-06 10:11 /dev/sr0


Still looking around...

---

### Post by greenchilli on 2010-06-06
Aha - I'm dumb. Obviously one can only mount or view the device if it contains valid media.
The DVD I've put in the drive was a dud, and the second one I've tried was a dud - So I tried a original movie DVD and now I can mount/view/play the device /dev/sr0

Try posting your results from: 

~$ wodim --devices

and 

/etc/fstab

and

cat /proc/filesystems

---

### Post by IwarV on 2010-06-07
I think I may have the same problem.
My computer has two optical drives. One is a PATA DVD ROM, the other is a SCSI CDR (Plextor PX-W124TS).

Any compatible medium inserted into the DVD ROM drive is mounted successfully. Any - bar none - compatible medium inserted the CDR is not.

output from "wodim --devices":
```
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'ASUS' 'DVD-ROM E608'
 1  dev='/dev/scd1'	rwrw-- : 'PLEXTOR' 'CD-R   PX-W124TS'
-------------------------------------------------------------------------
```

See also attached image from 'Disk Utility' showing an 'Unknown' medium inserted which was in fact an audio CD.

Any help greatly appreciated,

---

### Post by jjloupe on 2010-06-09
I am also having this problem, as are others. Seems there is no answer.

---

### Post by eddietours on 2010-06-10
Me too Damn can anybody help:confused:

---

### Post by BigLonn on 2010-06-11
Same here I noticed it seems to occurred after the last Kernel update  previous Saturday
Any one hear of anything I really need to get this  fixed when I try to  get the system to look at all I get is this

/usr/bin/dvd+rw-format -gui -force=full /dev/scd0
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.1.
:-( mounted media doesn't appear to be DVD±RW, DVD-RAM or Blu-ray

Any help would be appreciated!

---

### Post by jjloupe on 2010-06-11
I just realised that the drive works with CDs,but not DVDs...

---

### Post by pspsilveira on 2010-06-29
I updated to ubuntu 10.4 because I was having the same problem in ubuntu 9. Due to bad experience with upgrades, I choose a fresh install, removing the old partition with fdisk. 
I have two drives here: one DVD read only and one DVD to R/W. They were not working.

I am only a Linux user (not a geek or administrator), so I am surprised by the difficult lots of people are finding with this issue. Even more puzzled because I tried a very simple thing that I would bet wouldn't work, but it solved my problem.

I opened a terminal and became root:
$ sudo su
$ [sudo] password for silveira: 

then I realized that there was no entries in /etc/fstab, so I added
/dev/sr0       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sr1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

and, finally, since there was no  corresponding subfolders in /media, I typed (still as root) in the terminal:
$ cd /media
$ mkdir cdrom
$ mkdir cdrom1

It is working with data CDs and DVDs. As a simple user I do not know exactly what I am doing. However, it was so simple that I can barely believe that it is the problem that other users are facing. Can someone tell me if it helps? And why?

---

### Post by pspsilveira on 2010-07-08
> **pspsilveira said:**
>  [...] I updated to ubuntu 10.4 because I was having the same problem in ubuntu 9. [...] puzzled because I tried a very simple thing that I would bet wouldn't work, but it solved my problem [...] it was so simple that I can barely believe that it is the problem that other users are facing. 

I told you that it would not be so simple... my computer worked for a while but, today, is not finding/mounting CD/DVDs again. Annoying...

---

### Post by Superslacker on 2010-12-21
I am using 10.10 64 bit desktop. I had the same trouble accessing the dvd drive. 

This is what worked for me.

System/Preferences/System Settings/Removable devices.

The check box was not marked to enable automatic mounting of removable disks.

I checked the box / hit apply and restarted the machine

Burning and device access errors when dvd is inserted are now gone
[IMG]http://img23.imageshack.us/i/removabledevices.png/[/IMG][IMG]http://img23.imageshack.us/i/removabledevices.png/[/IMG]
  Screen shot is attached to this reply
[IMG]http://img23.imageshack.us/i/removabledevices.png/[/IMG]

---

### Post by FrontRanger on 2011-09-10
> **pspsilveira said:**
> It is working with data CDs and DVDs. As a simple user I do not know exactly what I am doing. However, it was so simple that I can barely believe that it is the problem that other users are facing. Can someone tell me if it helps? And why?

In case someone else is having this kind of problem...

Unlike many posters with this type of problem, mine did NOT happen immediately after a software change. My CD/DVD-ROM has worked fine with 10.04 LT for more than one year. It started failing today when I ejected a disc by simply pushing the button on the drive, forgetting to safely unmount it. I tried what pspsilveira posted above, but it did not work immediately. I tried restarting, and it still did not work. I then tried something that shouldn't work, but has solved other problems in the past for me: Cut the power supply, remove the battery, wait a little while, and boot. And lo! Now it works. I'm guessing some digital finite state machine was in an inescapable state, and had to come out by losing power. Who knows, but maybe this will help someone else.

---

### Post by kaiwi on 2011-10-03
Having the same problems for over a year now, since I upgraded to 10.04 Lucid Lynx. 

CDs and DVDs are usually automounted when I insert them right after loading Ubuntu. After maybe twenty minutes or so, the disks disappear from the desktop and I am unable to mount them again. 

I tried the "udisks" command to mount them manually, but in vain. "No medium found". 

So my only solution is to reboot whenever I want to access a CD or DVD. 

I suspect it's a very bad bug.

PLEASE HELP

---

### Post by bbrg548 on 2011-10-04
Just out of curiosity (and to rule out a hardware issue in my case), if you go into your "boot devices" menu in the BIOS on startup, is it showing there?

Mine is not, which is why I suspect I have an unrelated hardware issue. It started working on its own, in the middle of a session when I didn't do anything to cause it, but now it's not working again.

---

### Post by kaiwi on 2011-10-11
> **bbrg548 said:**
> Just out of curiosity (and to rule out a hardware issue in my case), if you go into your "boot devices" menu in the BIOS on startup, is it showing there?

Mine is not, which is why I suspect I have an unrelated hardware issue. It started working on its own, in the middle of a session when I didn't do anything to cause it, but now it's not working again.

Yes, all my devices show up in the BIOS. 

Just after posting my first contribution to this thread, I came across a bug report which solved my particular problem. At least I am able to make my CD/DVD devices reappear on Desktop when they have disappeared. See [http://ubuntuforums.org/showthread.php?t=1468035](http://ubuntuforums.org/showthread.php?t=1468035)

Good luck!

---

