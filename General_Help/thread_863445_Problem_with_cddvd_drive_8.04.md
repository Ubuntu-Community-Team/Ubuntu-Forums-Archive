---
title: "Problem with cd/dvd drive 8.04"
date: 2008-07-18
forum: General Help
---

### Post by cloverz7 on 2008-07-18
I searched around, but I've tried editing my fstab to many different things and nothing seems to work. Any help here would be great. The dvd is a one that I made using Vista before Installed ubuntu. Here is my copy of my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=faca8fc5-4058-4c33-9115-f262f6b9eff2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c3cca4ef-bc58-4e57-aad3-073aa752a3a1 none            swap    sw              0       0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Now some of this could be set up incorrectly because of me editing so much:(. I just installed ubuntu last night, but I've used it before so everything is up to date, but I may have forgotten to install some packages or something, any advice or help would be awesome, thanks guys.

---

### Post by cloverz7 on 2008-07-18
Bump :( Also just noticed that I can't open blank cd's...hm.


Could not open location 'burn:///'
The default action does not support this protocol.

is the actual error for blank cd's

---

### Post by editrix on 2008-07-19
There's a gazillion problems with cd burning in Hardy. Go to [www.uboontu.com](www.uboontu.com) and search "burn cd" or any of the error messages you get. I filed a bug report on my particular problem but it's somehow disappeared (although it got confirmed) and I've never solved my problem, but with any luck, you'll find your answer.

---

### Post by cloverz7 on 2008-07-19
Still no fixes yet :( I've tried just about everything I've seen still not fixed...please help!

---

### Post by cloverz7 on 2008-07-19
Bump sorry to be aggrivating but I know someone out there can help me

---

### Post by mc4man on 2008-07-19
> The dvd is a one that I made using Vista before Installed ubuntu that may have created a disk that isn't playable in a default ubuntu install. (live system - udf 2.01) see screenshots.

Why don't you run ```
sudo lshw -C disk
``` to check on the drives logical names
If you run the above with  media inserted in the drive there should be some indication of what was detected, and if a filesystem how mounted at bottom of listing for the drive. Some examples here 
[http://ubuntuforums.org/showthread.php?p=5333436#post5333436](http://ubuntuforums.org/showthread.php?p=5333436#post5333436)

---

### Post by cloverz7 on 2008-07-20
I don't really know what you were asking me to do but here is the result of sudo lshw -C disk

>  *-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7190A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: ATA Disk
       product: Hitachi HDP72503
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: GM3O
       serial: GEB330RC0JJ70F
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=624f624f
  *-disk:0
       description: SCSI Disk
       product: USB SD Reader
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 1.00
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       product: USB CF Reader
       vendor: Generic
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdc
       version: 1.01
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:2
       description: SCSI Disk
       product: USB SM Reader
       vendor: Generic
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sdd
       version: 1.02
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:3
       description: SCSI Disk
       product: USB MS Reader
       vendor: Generic
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sde
       version: 1.03
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde



edit okay maybe I get it a little better, this is with the data DVD in...Please someone help :-/

---

### Post by mc4man on 2008-07-20
> *-cdrom
description: DVD-RAM writer
product: DVD RW AD-7190A
vendor: Optiarc
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/cdrom
logical name: /dev/dvd
logical name: /dev/scd0
logical name: /dev/sr0
version: 1.03
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
[COLOR="Red"]configuration: ansiversion=5 status=ready
*-medium
physical id: 0[/COLOR]
logical name: /dev/cdrom

That is showing media has been found in your drive but no filesystem detected. If that's the data dvd made in vista then that's the likely culprit. 
To test whether it's something in your hardware or setup insert some media in the drive with a _known filesytem that's compatible with ubuntu_. This could be a data cd/dvd not created in vista or a commercial dvd movie. Then see if you can access the files or play the movie. You could also run lshw again and should see info on the  mounted filesystem. For instance a proper data dvd or dvd video will return this line(s)
> configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready

a proper data cd this
> configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready

---

### Post by cloverz7 on 2008-07-20
Interesting so vista is the POS in this situation. A little more satisfied with that answer. Only problem is how can I get the data off, is it possible to resize a partition to temporarily install vista to get it mount that temporary partition in ubuntu and just copy/paste? Because otherwise I don't want to have to get rid of all the work I've done on ubuntu so far, but I really need the info off this disk.On a side note if I could just get my WC3 installation with wine working right I'll be on par and on the right track to ubuntu goodness.

edit: Not good I think I edited too much...:( This is the output of a normal DVD (The Zodiac movie)>  *-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7190A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/ZODIAC_DOM_PS
       version: 1.03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/ZODIAC_DOM_PS
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted



Double edit: It seems that I can read the files off the disk, but the movie doesn't play using totem...strange. The Error it spits out is " Could not read from resource"

---

### Post by mc4man on 2008-07-20
> but the movie doesn't play using totem That's your 2nd pos. 
Totem generally gives that error from one of three things.
No region set on drive (if you've ever watched a commercial dvd in windows that's not an issue)
It's not accessing the right device (defaults to /dev/dvd, so you _should_ be ok there)
libdvdcss2 isn't installed  ??

better to install vlc, libdvdcss2 and troubleshoot from there (if needed)
here's what I do from fresh install, never fails me, if you have medibuntu enabled as a repo skip that part
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

> but I really need the info off this disk
If you knew someone with vista or even maybe xp (sp2) i'd just copy from there box to new media or flash drive. If so and it's vista and your burning choose 'mastering mode'

---

### Post by cloverz7 on 2008-07-20
After installing vlc and all it's plugins still nothing =/ open the dvd with vlc and it does nothing.


edit: Every time I start vlc with the dvd(menus) option it just closes immediately testing after a system restart

double edit: now works after system restart. I guess my problems are over minus that dvd I have that won't open :( and well wine and wc3 but that's a different story for a different time. Thanks a ton

---

### Post by mc4man on 2008-07-20
> wine and wc3
browse, and or post here 
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by cloverz7 on 2008-07-20
Oh lord...on a new attempt to install wc3 my computer shows that wc3 is mounted but will not open the files one it...this is a new one it was working yesterday:(

fixed sorry for the unnecessary bump

---

### Post by 0x4B61726E on 2008-12-24
do you think this would work with an external enclosure?

---

