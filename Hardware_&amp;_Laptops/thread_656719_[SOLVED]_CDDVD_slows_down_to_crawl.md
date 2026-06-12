---
title: "[SOLVED] CD/DVD slows down to crawl"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by markbann on 2008-01-02
When ripping CD's with Sound Juicer CD/DVD slows to a crawl.  Starts with rip time of 5 mins and eventually just goes to 40+ minutes.  It will usually complete task.  When I first installed this did not happen.  I noticed it after a variety of software changes.  Restarting the ripping stays at the slow speed.  Eject CD and try a new one and sometimes still slow, sometimes fine.  
(Drive worked fine when this was a windows computer.)

Read a variety of posts but didn't really see any solutions.  
Installed grip to see if it changed anything.  Same issues Grip is faster and seems to recover from slowdowns better.

Newbie to Ubuntu - have worked with SuSE some.
System Unbuntu server (with gnome installed)  7.10
Was XP computer - added new hard drive and installed fresh from CD -(- desktop install version would not launch)
1 Cd/DVD Sonty DVD-ROM DDU1611
2 - Plextor CD-R PX-W1210A -- doesn't work at all
ASUS A7V266-E motherboard - farily old

[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4a03d63c-b187-4342-ad7f-6213916f59e5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b987056b-0a1e-49ba-ab91-4fb20d8348e0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0[/INDENT]

---

### Post by perixx on 2008-01-03
hy markbann,

I don't know sound juicer, but perhaps it has some feature enabled like 'allow drive slow down during extraction' or some such thing. Or maybe the reading speed is set too low or the program has problems with reading the medium content in general.

You aren't using some drive slowdown-command like 'eject' or 'setcd', are you? If yes, or no, you might try to use e.g. 'setcd' to set a higher reading speed before loading sound juicer, by using a little script like 
```
#! /bin/bash

setcd /dev/dvd -x S
/usr/bin/X11/smplayer
```
while 'S' has to be replaced by a number of your choice and possible support of your drive, and '/usr/bin/X11/smplayer' by the path to your sound juicer program. I'm using the script to slow down the drive while watching movies, btw.

perixx

---

### Post by markbann on 2008-01-05
> **perixx said:**
> hy markbann,
with reading the medium content in general.

You aren't using some drive slowdown-command like 'eject' or 'setcd', are you? If yes, or no, you might try to use e.g. 'setcd' to set a higher reading speed before loading sound juicer, by using a little script like 
perixx
<snip>

Thanks for the comments.  No, I'm not using any other commands.  And since grip slows down considerably as well I'm not sure that will help.  I'll look and see what it does.

Quick question that may or may not pertain.  The CD icon the shows on the desktop does not show that the CD is mounted when I check the properties.  Is that normal?

---

### Post by perixx on 2008-01-05
I know it's normal for audio CD's, they're not mounted by default; but DVD's? Not sure... 
when watching movies, Thunar shows the disc not as mounted though!
On the other hand, it's only possible to directly eject a running DVD when, using the 'eject' command (which unmounts media AFAIK), and not just by pressing the eject button on the drive itself - like it's possible with audio-CD's.

perixx

---

### Post by markbann on 2008-01-06
Tried to do a test and burn an iso image of a audio cd to see if it slows down.  tried the dd command and got this response
$dd if=/dev/hdc of=cd.iso
dd: reading `/dev/hdc': Input/output error
...

When mounted a data CD mounts here:

/dev/hdc on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=mark)

---

### Post by markbann on 2008-01-06
The fault was the CD's themselves.  They had a very fine film residue on them from a cheap case and hot sun in the car.  Several were effected so it wasn't obvious it was the CD's.
LIght polishing with siliver polish solved it.  Juicer still is MUCH slower than grip.  Perhaps if I can get the encoding going on grip I'll switch.

---

### Post by perixx on 2008-01-07
> $dd if=/dev/hdc of=cd.iso
I'm not yet familiar with all the powerful functions of the 'dd' command; but I thought that you need to be root to use it?
Also, I thought that 'if=' resembles sth. like 'from', whereas 'of=' means sth. like 'to' with the 'dd' command? Like when I use it for exporting the bootsector to a file:
```
sudo dd if=/dev/hda of=~/bootsect.lnx
```
The way I read your command, you are trying rip a CD to the 'cd.iso' file? Where to exactly? At first I thought you'd like to burn to that CD.
 
correct me please, if I'm wrong...

perixx

---

### Post by markbann on 2008-01-07
I switched to trying to burn an iso image just to test the speed of reading the drive.

---

### Post by Chessmaster on 2008-01-20
Also, have a look at the third post in this thread:

[http://ubuntuforums.org/showthread.php?t=462349&highlight=sound+juicer+slow](http://ubuntuforums.org/showthread.php?t=462349&highlight=sound+juicer+slow)

cd paranoia will slow things down heaps depending on the condition of your CD and what settings you have.

---

