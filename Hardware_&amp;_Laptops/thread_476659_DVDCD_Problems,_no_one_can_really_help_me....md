---
title: "DVD/CD Problems, no one can really help me..."
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by FredDie3785 on 2007-06-17
Ok so let me ge t this straight....
I'm Ubuntu user since 6.06 Dapper Drake. Now I'm running Ubuntu 7.04 Feisty Fawn and I must say that's a great OS. Ok let's get to the point....

I've got strange problems with my DVD-Writer. 
When I'm trying to play Audio-CD [every Audio CDs], something like this appears: 
Screen#1
[[IMG]http://img520.imageshack.us/img520/2154/screenshotqe0.th.png[/IMG]](http://img520.imageshack.us/my.php?image=screenshotqe0.png)
And the Amarok is saying that he "Could not read the Audio CD"

When I put the DVD-Video [every DVD I have] , again some strange info appears:
Screen#2
[[IMG]http://img388.imageshack.us/img388/3324/screenshot1uk1.th.png[/IMG]](http://img388.imageshack.us/my.php?image=screenshot1uk1.png)

When I'm inserting random DVD with random files [movies,mp3s etc] there's some disturbing behaviour. Let me explain it ona example. I've inserted DVD with movies in divx format. Every single film is in it's own folder. But the only folder I can get into is the 1st [Screen#3], what so ever I cannot open the movie inside that folder. The Mplayer that I'm using is giving me information that...well it's a long info [Screen#4], and the avi changes its icon as if it would be a txt file or something. When I right clik it the Mplayer gives me some crash info called "seek failed" [Screen#5]. 

Screen#3
[[IMG]http://img369.imageshack.us/img369/1341/screenshot3lj4.th.png[/IMG]](http://img369.imageshack.us/my.php?image=screenshot3lj4.png)

Screen#4
[[IMG]http://img484.imageshack.us/img484/5391/screenshot4yn0.th.png[/IMG]](http://img484.imageshack.us/my.php?image=screenshot4yn0.png)

Screen#5
[[IMG]http://img387.imageshack.us/img387/5830/screenshot5yr3.th.png[/IMG]](http://img387.imageshack.us/my.php?image=screenshot5yr3.png)

I can guarantee that I've installed all the necesarry codecs and libdvdcss, w32codecs [or whatever is called], becasue other movies that I have on my HDD are working fine. 

I'm also attaching my fstab.
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=12df0867-a50f-47e1-b2f3-9dade56d2a5f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=729d3a6e-4cfc-4362-bef8-abde9c5645d0 /media/Kontener ext3    defaults        0       2
# /dev/hda4
UUID=460c0991-8c64-4c64-b070-d7a0e96f571d /media/Media    ext3    defaults        0       2
# /dev/hdb1
UUID=1050AA5A50AA45F6 /media/Windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=81c58a5f-e1fe-4fde-8d45-0222d22036d7 none            swap    sw              0       0
/dev/hdc	/media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I would really appreciate it, if someone could help me with this thing, becasue I'm fighting with it for over a week.

---

### Post by gnirts on 2007-06-18
Try rolling back the kernel version to whatever it was before you had the buggy behavior.

---

### Post by FredDie3785 on 2007-06-20
You mean that I should choose the older kernel version in the boot menu?? Well, this doesn't work. Maybe you're talkin' about other rerolling...

---

