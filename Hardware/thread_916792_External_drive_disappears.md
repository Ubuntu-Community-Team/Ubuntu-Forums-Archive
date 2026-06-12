---
title: "External drive disappears"
date: 2008-09-11
forum: Hardware
---

### Post by jvoegele on 2008-09-11
I have a Western Digital My Book Mirror Edition drive connected to my Ubuntu Gutsy Gibbon desktop machine via USB.  This drive has built-in RAID 1 mirroring, and I reformatted the drives to ext3 immediately after opening the box.

Since the beginning, I've been having trouble with this device in that it "disappears", and becomes inaccessible to the operating system.  I have the drive configured in /etc/fstab to mount at /shared on my system, and for a while everything works fine.  However, if I let the drive stand idle for an extended period of time, the device disappears.  The mounted /shared directory is still there, but if I try "ls /shared" I get the following:

```
$ ls /shared/
ls: reading directory /shared/: Input/output error
total 0

```

Furthermore, the device file that represents the drive (/dev/sdc1) no longer exists.  If I try to umount the drive, I get an error message saying that the device is busy.

I had two theories about why this was happening.  The first thing I thought was that maybe brief power outages were causing the problem, so I purchased a UPS but it did not fix the problem.  My second thought was that perhaps the drive was putting itself into a sleep or standby mode after some period of inactivity, so a created a cron job that wrote to a file on the device every minute.  I thought that this had fixed the problem since the drive stayed up and running for over a full day, but this morning the drive has "disappeared" again :(

Does anyone here have any information or advice that might help me to keep this drive alive?

Thanks in advance for any help you can offer.

---

### Post by jvoegele on 2008-09-11
I forgot to mention previously that either rebooting or issuing a "mount -a" command remounts the external drive properly, although in the latter case the drive is assigned a new device file: /dev/sdd1 instead of /dev/sdc1.  (I am using UUIDs in my fstab so this doesn't cause any problems for me.)

---

### Post by mailforbiz on 2008-09-11
I am having a similar problem but with a different drive : Fantom 120 GB USB drive. I am beginning to suspect this is a problem with the USB driver. It used to work fine when I had XP. Its possible that it just went bad when I switched over to Linux but thats too big a coincidence. I'll try and put XP on one of my other computers, hook this back up and see how it fares.

---

### Post by yani1shu on 2008-09-13
I'm having a similar problem,  however, my drive disappears whenever i connect another external hard drive to my machine via usb. My original drive works fine till the very moment i connect the second drive, then the original one disappears and all i'm left with is the second one. Even 'fdisk -l' doesn't show anything in regards to the original drive. Any suggestions?

---

### Post by Chang An on 2008-10-27
jvoegele,  I just got that drive too.  I got the western digital mirror with two 500 gig drives.  I left it as NTFS but I already have fragmentation that windozes can't defrag.  So since its a hardware raid 1 you were able to format it to ext3 and the second drive also did the same right?  How to you monitor the health of the raid?  Also is the drive showing up in Ubuntu again?

---

### Post by jvoegele on 2008-10-27
> **Chang An said:**
> jvoegele,  I just got that drive too.  I got the western digital mirror with two 500 gig drives.  I left it as NTFS but I already have fragmentation that windozes can't defrag.  So since its a hardware raid 1 you were able to format it to ext3 and the second drive also did the same right?  How to you monitor the health of the raid?  Also is the drive showing up in Ubuntu again?

The drive is showing up again now.  The problem was actually a loose USB cable connection.

I was able to successfully format the drive to ext3 and everything works fine.  However, I don't know of any way to verify whether both internal drives are ext3 and are being mirrored, short of taking out one drive at a time and checking the data.  I'm merely assuming at this point that both drives are being used.

Does anyone know a way to verify without taking out one or the other drive?

---

### Post by sd23ddde on 2009-01-06
Hello everybody,

sorry warming this up but I just have the same error with the WD Mirror Edition 2TB. I have the drive in standard NTFS up and running (from time to time) but it also disappears. I tried several USB Ports but I'm not able to have it available a whole day. 

@jvoegele: the fix of the loose USB connection did the trick? As said I tried it with different USB ports but without any success...

I appreciate any help

---

### Post by grossinm on 2009-01-06
I am having a (mildly) similar problem w/ a WD My Book (essential edition).  The thread is  [here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1031554"),  your problem seems a bit dissimilar, but if I've learned one thing about Linux in the three days I've been working with it, is that the problem being experienced maybe far from the obvious one (at least to a noob).

---

### Post by jvoegele on 2009-01-06
> **sd23ddde said:**
> @jvoegele: the fix of the loose USB connection did the trick? As said I tried it with different USB ports but without any success...

I did three things to try to fix this problem:

1) Purchased a Uninterruptible Power Supply and plugged my computer and the drive into it.
2) Created a cron entry that would write something to the drive every minute so that it would not go to sleep.
3) Secured the USB cable connection.

In retrospect, it is possible that step (2) is the one that finally fixed the problem for me.  If you want to try it yourself, just add something like this to your crontab:

```
* * * * *   echo `date` > /shared/keepalive
```

---

### Post by sd23ddde on 2009-01-06
thanks for your fast reply.
I also think that the 2nd might solve it, since the disappearing is almost about 15 mins (always the same) so I guess its about some stupid sleep mode ;)

I will check this and reply if it worked. 
Thx again

@grossinm: I'm not sure but I think our problems are really different?! But: See you in your thread.

---

### Post by sd23ddde on 2009-01-06
looks really good!
the drive is online lots longer than before! I guess it does the trick. 

So does somebody know how to get the sleep / standby of the External Drive off? Since I would love to have a perfect way (writing a file is good but a dirty trick ;)).

---

### Post by sd23ddde on 2009-01-11
So, after a few days here is the current status:
Adding the keepalive script allowed me to keep the drive online (at least a while). Right now I have some strange behavior regarding i/o errors. Also the backup failed after an amount of approx 30gb. But thats another storry. I wanna digg a little before I'm back with it.

kind regards

---

### Post by sd23ddde on 2009-05-17
here we go again,

the keepalive is still working ;) but I also still have the strange i/o issue with my drive. It happens from time to time that the drive shows an i/o error and I can't (of course) write on the drive. Even disconnecting and reconnecting doesn't solve the problem.

A strange thing is, that my WD MyBook Mirror 2TB (ntfs formated) is mounted without any problems after restart. After the i/o error I tried umounting and remounting the drive (via mount -a) but than it tells my that it is not possible?!?!

Any suggestions?

Best Regards

---

### Post by cmcanulty on 2009-09-22
My 500GB Maxtor disappears too, works fine with windows. So I can never backup which is a huge problem, big enough to warrant me going back to windows if I can't back up as I have tons of critical stuff. GRsync and all the umpteen other backups start OK then errors as the drive disappears. This seems to be a common Ubuntu bug that really needs looking into.

---

