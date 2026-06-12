---
title: "Fdisk problems"
date: 2008-08-01
forum: General Help
---

### Post by Polluted13 on 2008-08-01
Sorry if this is in the wrong place or if it's been posted elsewhere. I've think looked everywhere at this point.

I have an old 2 gig mp3 player that I mostly just use for moving data around between my PCs and my PS3. A while back there was a power outage when I was in the middle of loading some data on to it and now it won't mount anywhere.

Gparted recognizes it, but it's labeled as SDA instead of SDA1 and when I try to create a disk lable so I can format it gparted crashes. This seems to be due to a well known stack smashing error with drives larger than 512 megs. Also, Gparted only recognizes the drive as having around 400 megs of *unallocated* space, there's no mention of the other gig and a half.

Most people have been able to work around the stack smashing error by using fdisk, but when I run "sudo fdisk /dev/sda" I get "mount: can't find /dev/sda in /etc/fstab or /etc/mtab"

So...HELP! I lost my other thunmb drive and I can't be bothered burning everything to disc all the time. Can this be fixed?

Btw I'm running Hardy.

---

### Post by Polluted13 on 2008-08-02
Anyone?

Is there another thread I should check out?

---

### Post by Polluted13 on 2008-08-03
Okay then. Nevermind.

---

### Post by jflaker on 2008-08-03
Before you can change the partition, you must unmount the disk......Then try gparted

---

### Post by Polluted13 on 2008-08-03
I can't actually mount the disk in the first place. My PC only acknowledges that it's plugged in when I open Gparted. 
If I could mount the thing then I imagine I could format it without any troubles. Basically it's completely corrupted and I need some way alternative way to format it because Gparted doesn't like thumb drives larger than 512megs.

---

### Post by jflaker on 2008-08-03
Get backtrack 3 distro which has some disk utils on it which MIGHT help.  It is a livecd too.

---

### Post by Polluted13 on 2008-08-04
Cool. I'll check that out. Thanks.

---

### Post by geirha on 2008-08-04
> **Polluted13 said:**
> 
Most people have been able to work around the stack smashing error by using fdisk, but when I run "sudo fdisk /dev/sda" I get "mount: can't find /dev/sda in /etc/fstab or /etc/mtab"


The fdisk command you are trying to use is correct, but the error message is an error message given by the mount command. You haven't by chance run mount instead of fdisk?

Please try ```
sudo fdisk /dev/sda
``` again and post the error message. I'd be very surprised if you get that mount-message.

---

### Post by Polluted13 on 2008-08-07
That's what it was giving me, but I've messed around with it a bit since then. This time I got this:

moe@moe-laptop:~$ sudo fdisk /dev/sda
[sudo] password for moe: 
Note: sector size is 2048 (not 512)

Command (m for help):

Edit: Or perhaps that's what I got when I was trying to mount it in the first place.

---

### Post by geirha on 2008-08-08
Well, that looks normal, type m for help as it suggests, then create a partition on it.

---

### Post by maclover on 2010-09-30
ok i installed fdisk and i cant find it???:( where would it be at

---

### Post by srs5694 on 2010-09-30
> **maclover said:**
> ok i installed fdisk and i cant find it???:( where would it be at

There's no need to [ask the same question twice;](http://ubuntuforums.org/showthread.php?t=1585670) doing so wastes everybody's time.

---

