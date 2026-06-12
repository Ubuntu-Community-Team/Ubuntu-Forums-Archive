---
title: "Install on already partioned hard drive"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by ahsatb on 2009-05-27
Hi all
 
I had a disasterous day on Monday while trying to install Ubuntu. To cut a long story short it ended up with me managing to kill my computer to the point Windows wouldnt even boot. As a result it has been rebuilt and the department technican has left a 30 Gb unformated space on the hard drive for me to instal Ubuntu if required. Please can someone provide some guidance (ideally very clear instructions for a stupid person) to explain how to go about installing Ubuntu on this avaliable partion, as I am a bit confused as obviously the online instructions tell you how to make a partition.
 
Many thanks
Tasha

---

### Post by YldGuy on 2009-05-27
[www.youtube.com/watch?v=faaVIcS1QAk](www.youtube.com/watch?v=faaVIcS1QAk)

---

### Post by Xavier71 on 2009-05-27
That video has been removed from YouTube ...

Anybody out there to help, I'm stuck at the same level.

---

### Post by scrooge_74 on 2009-05-27
1. live CD
2. When you get to the part it ask you on where to install Ubuntu, you need to tell the system to install in that free space you have.
3. Pick the manual formatting option so you can tell the system to format that section of the disk for linux and leave the rest untouch.

Basically that is the moment you have to be carefull not erase your windows partition at this stage. After you get the partition set for linux the rest is easy

**EDIT: [[COLOR="Blue"]Here[/COLOR] ]("http://www.psychocats.net/ubuntu/index.php")there is more info for you.**

---

### Post by drs305 on 2009-05-27
ahsatb, welcome to the ubuntu forums.

This link has pretty good graphics on installations. It's for 8.04 Hardy but the procedures are the same:
[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml")

Here is the official installation page, which is also good:
[https://help.ubuntu.com/9.04/installation-guide/i386/index.html]("https://help.ubuntu.com/9.04/installation-guide/i386/index.html")

---

### Post by ahsatb on 2009-05-27
Thanks very much for the advice.  I've had a look at some of the links you have all left and I hope to be able to have a play tonight once I get my laptop back :)

---

### Post by presence1960 on 2009-05-27
here is some info : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

you want to scroll down to #8. At the partitioner screen you want to choose "manual" option. This will bring up a window with all your hard disk(s) and their partitions. Highlight the partition you want to install Ubuntu on and click "Edit".  Another screen will appear and you need to choose the filesystem and mountpoint. If you are using Jaunty choose ext3 or ext4 for Filesystem and choose "/" as mountpoint. Ext 4 is newer but a lot faster than ext3. Edit: choose partition type-primary or logical.also.

when you get to the screen that says Ready To Install (#14 on that link) you want to click the advanced button so you can install GRUB to MBR. If you only have one hard disk choose sda (not a partition such as sda1, sda2, etc) This will give you the option at boot of choosing Ubuntu or Windows. If you have 2 hard disks you want to choose the disk that Windows is on (either sda or sdb)

Attached are the images to which I referred.

---

### Post by ahsatb on 2009-05-27
I seem to have done it :)  Thanks all for your help.

---

### Post by presence1960 on 2009-05-27
Excellent!! Enjoy.

P.S. Welcome to the community

---

