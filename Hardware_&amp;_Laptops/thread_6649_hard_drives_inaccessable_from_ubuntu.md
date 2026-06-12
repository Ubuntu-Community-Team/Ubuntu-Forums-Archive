---
title: "hard drives inaccessable from ubuntu"
date: 2004-11-30
forum: Hardware &amp; Laptops
---

### Post by helios on 2004-11-30
First off, I want to tell you how impressed I am with this operating system.  As a KDE guy, I shrugged off gnome because it wasn't "pretty".  You are gaining a gnome fan as we speak...and, I have never had such an easy time of installing nvidia drivers with 3d support with any operataing system.  the instructions on the wiki are awesome and my gratitude to whoever posted them.  This system rocks.

Now be gentle, I am a 12 year windoze Zombie and have only a basic understanding of Linux. I have taken off my training wheels and am totally Linux now.  Kanotix on hda, ubuntu on hdb.  I am most comfortable with debian simply because of apt-get/dpkg.  Ubuntu does a wonderful job with it especially after I updated my sources.list from the kind persons  on the wiki.  but, this is my problem.
In Kanotix, knoppix, mepis, etc; it was a simple matter to exchange files between hard drives...drag and drop worked nicely.  In Ubuntu, I am getting an error message saying :

/dev/hdb2:  no such file or directory
mount: /dev/hdb2: cannot read superblock.

This does this from either hd, a or b.  How do I fix this?  I do not know how to look and see if ubuntu has different names for these drives, because maybe if I change them in properties, it will do it.  I had that problem with my cd drives in mplayer and once I changed it in the mplayer properties, it read the drive.  Any help in this matter would be appreciated because I must share files back and forth between systems.   whew...all that to ask a 20 second question...

chattily yours

helios

---

### Post by jdong on 2004-11-30
What filesystems are these partitions formatted in?

---

### Post by helios on 2004-11-30
hda holds a kanotix hd installation formated in ext3. As far as ubuntu, I don't know...or I dont know how to look and check.  I chose "take over entire disk" when I installed so whatever the default format is will be what is there.  As I stated, my knowledge of Linux is slight, but I am guessing this is a mounting problem, but don't get me to lyin'...I am a total noob.

found the info in the "info center" (go figure)  states as below:

/dev/hdb2    /mnt/hdb2     fs type:  auto      mount options:  auto,users,exec



thanx

helios

---

### Post by Magneto on 2004-11-30
[QUOTE=helios]hda holds a kanotix hd installation formated in ext3. As far as ubuntu, I don't know...or I dont know how to look and check.  I chose "take over entire disk" when I installed so whatever the default format is will be what is there.  As I stated, my knowledge of Linux is slight, but I am guessing this is a mounting problem, but don't get me to lyin'...I am a total noob.

found the info in the "info center" (go figure)  states as below:

/dev/hdb2    /mnt/hdb2     fs type:  auto      mount options:  auto,users,exec



thanx

helios[/QUOTE]
 try ```

sudo cfdisk /dev/hdb

```
what's listed?

type ```

sudo cfdisk
```

what's listed

---

### Post by helios on 2004-11-30
cfdisk 2.12h

                              Disk Drive: /dev/hdb
                        Size: 40020664320 bytes, 40.0 GB
              Heads: 16   Sectors per Track: 63   Cylinders: 77545

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hdb1        Boot        Primary   Linux ext3                       39508.19
    hdb5                    Logical   Linux swap / Solaris               512.49


on cfdisk command:

 hdb1        Boot        Primary   Linux ext3                       39508.19

thanx

helios

---

### Post by Magneto on 2004-11-30
[QUOTE=helios]cfdisk 2.12h

                              Disk Drive: /dev/hdb
                        Size: 40020664320 bytes, 40.0 GB
              Heads: 16   Sectors per Track: 63   Cylinders: 77545

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hdb1        Boot        Primary   Linux ext3                       39508.19
    hdb5                    Logical   Linux swap / Solaris               512.49


on cfdisk command:

 hdb1        Boot        Primary   Linux ext3                       39508.19

thanx

helios[/QUOTE]
 ok problem here

How many drives do you have in your PC? Harddisks and DVD/CD etc
How are they connected? First drive MASTER on channel 1 ide is DVD rom hda1 2nd is 10gb hard drive hda2 etc
your BIOS post might tell you or the front page of your BIOS config might have them laid out
if you dont know which is master and which is slave its ok

the problem is cfdisk is defaulting to hdb but you say you have to harddrives one on hda and one on hdb
is one disk a scsi disk? 
usually cfdisk will display hda if you dont specify /dev/hd* so I'm wondering what's going on

---

### Post by helios on 2004-11-30
[B]
How many drives do you have in your PC? Harddisks and DVD/CD etc[/B]

two hard drives, hda and hdb: two cd/dvd roms.  I do not know why ubuntu is handling (or if it even is) these drives differently.  If I were to install knoppix or mepis on my hdb, I could access hda without a problem.  this has only occured with ubuntu.  neither drives are scsi, both are western digital:  one a 120 gig and the other a 40 gig.  hda is primary while hdb is slave according to my bios.  I am a bit lost here.

thanx

helios

---

### Post by Magneto on 2004-11-30
[QUOTE=helios][B]
How many drives do you have in your PC? Harddisks and DVD/CD etc[/B]

two hard drives, hda and hdb: two cd/dvd roms.  I do not know why ubuntu is handling (or if it even is) these drives differently.  If I were to install knoppix or mepis on my hdb, I could access hda without a problem.  this has only occured with ubuntu.  neither drives are scsi, both are western digital:  one a 120 gig and the other a 40 gig.  hda is primary while hdb is slave according to my bios.  I am a bit lost here.

thanx

helios[/QUOTE]
 can you mount /dev/hda1 manually? mount -t ext3 /dev/hda1 

what does cfdisk /dev/hda show?

---

### Post by helios on 2004-12-01
thanx magneto, 

I am sorry for the delay in posting.  I am not able to mount either drive from the opposing OS.  I will have to come back to it later because this problem is a showstopper for us.  Ubuntu looks like a promising OS but because of our need to migrate to linux quickly and with the highest level of stability and usability, we're gonna have to take a look at it again in the next release.  I just don't have time to "make it work" right now.  I am looking to use Ubuntu on both the server and desktop sides for our business.  This is a good OS and I hope it develops quickly.  Other problems I faced were sluggish or hanging  file system transfers.  This may have been system problems and not OS-related, but our mepis and Kanotix distros give us no such problems.

thanx

helios

---

### Post by Magneto on 2004-12-01
[QUOTE=helios]thanx magneto, 

I am sorry for the delay in posting.  I am not able to mount either drive from the opposing OS.  I will have to come back to it later because this problem is a showstopper for us.  Ubuntu looks like a promising OS but because of our need to migrate to linux quickly and with the highest level of stability and usability, we're gonna have to take a look at it again in the next release.  I just don't have time to "make it work" right now.  I am looking to use Ubuntu on both the server and desktop sides for our business.  This is a good OS and I hope it develops quickly.  Other problems I faced were sluggish or hanging  file system transfers.  This may have been system problems and not OS-related, but our mepis and Kanotix distros give us no such problems.

thanx

helios[/QUOTE]
 Server and desktop I'd go slackware for servers and slackware w/ gnome desktop  if not Ubuntu.  Sorry your experiences didn't suit your needs.

---

