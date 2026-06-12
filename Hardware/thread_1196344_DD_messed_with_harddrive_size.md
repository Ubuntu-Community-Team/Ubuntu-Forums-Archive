---
title: "DD messed with harddrive size"
date: 2009-06-24
forum: Hardware
---

### Post by piratebill on 2009-06-24
EDIT:
I think this thread is in the wrong area for these forums.  Moving it to general help.  


Ok I have a really odd issue here.  My friend was running out of HD space and asked me to clone their old laptop drive (running XP) to newer, larger drive.  I used dd to copy the drive
```
sudo dd if=/dev/sdb of=/dev/sdc
```

It did clone successfully, but it kept the partition to 38 gigs.  I then used Gparted to resize the ntfs partition to fill the rest of the drive.  It gave me the bluescreen of death upon booting.  We then decided it would be easier to reload windows from scratch (this is where the weird part happens).

The Xp cd only sees the new drive to be capable of holding 38 gigs.  However, gparted still sees the drive is 120 gigs.  If I format the drive with gparted, windows still wont recognize more than 38 gigs (tried with two computers).  I figured that dd changed some table that windows reads, but linux ignores so I ran this:
```
sudo dd if=/dev/zero of=/dev/sdb
```
to zero out the drive, but the problem persists.  

I am very stumped here.  the last idea I have is to get an old drive of mine, format it to use 120 gigs and dd that to the new one, but this will take a lot more time than I have left to give.  Do any of you know what is going on with this hard drive:confused:?

---

### Post by piratebill on 2009-06-24
Slight update:

I formated the drive using gparted (120 gig partition) and had fdisk varify the partition. It said
```
total allocated sectors 234436483 greater than the maximum 75200265
```

I know that is not a standard message. Any ideas at all?

---

### Post by piratebill on 2009-06-25
More updates.  The cylinder count, head count and sector per track count are not what they should be.  By googling the drive, I found it should be 16383/16/63.  I tried changing these values in fdisk, but no luck.  How can I change these values so that they stick?  I think that would fix everything.


Do you think dd did this, or is the drive just fraked?

---

### Post by XPuntu on 2009-08-16
You seem to be doing the right things. What OS disk are you running fdisk from? Win98? Did you delete the partition (38GB) first and then see what fdisk reported?

---

