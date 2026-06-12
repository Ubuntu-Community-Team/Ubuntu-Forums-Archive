---
title: "CD-Writer unable to read CD"
date: 2024-03-17
forum: Hardware
---

### Post by satimis on 2024-03-17
Hi all,

It is very strange the DVD-Writer of my daily working PC unable to read CDs.  I haven't used it for prolonged time, neither reading CD nor burning CD.  But it can be detected.

$ sudo lshw -C disk
```

  *-cdrom                   
       description: DVD-RAM writer
       product: DVD RW AW-G170S
       vendor: SONY
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: 1.72
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

Please advise how to fix the problem.

Is the life-time of the DVD-writer coming to the end?  I need to purchase a new one?

Thanks in advance.

Regards

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
Tried follows;
$ sudo mount /dev/sr0 /mnt```

mount: /mnt: no medium found on /dev/sr0.
```

$ sudo mount /dev/cdrom /mnt```

mount: /mnt: no medium found on /dev/sr0
```
The CD is in the tray.  It is a working CD.

This CD can be read ONCE before on this DVD writer.

---

### Post by phatton1 on 2024-03-17
This may be a stupid question, but have you cleaned the drive for a while?

---

### Post by Autodave on 2024-03-17
Do you hear the drive spinning up after you insert a disc and close the drawer?

---

### Post by satimis on 2024-03-17
Hi all,

Thanks for your reply.

Sorry no.  I haven't cleaned this DVD-writer after building this daily working PC which was built about 8 years ago.

Neither I have used the DVD-writer burning CD/DVD.  It just stands idly there.  I only used it to read software on CDs at time of PC installation in the very early beginning.

The music CD for testing is working without problem.  It have been detected and worked only 2 times.  I have tried other music CDs.  It is still the same.

I marked the position of the CD before inserting the tray.  Sometime its position changes and another time the position of the CD remains unchanged.  The LED light of the DVD-writer is out after a while of inserting the CD tray.

Another strange thing is the CD tray will be inserted automatically by slightly touching the tray with finger.

How to clean the DVD-writer ?

Regards

---

### Post by phatton1 on 2024-03-17
With a dcd cleaning disc

---

### Post by satimis on 2024-03-17
> **phatton1 said:**
> With a dcd cleaning disc
Thanks

Regards

---

### Post by satimis on 2024-03-17
Hi all,

I can mount the CD with;

$ gio mount cdda://sr0/

$ gio list cdda://sr0/
no output

The CD is empty without any content.  It is quite strange

Regards

---

### Post by satimis on 2024-03-18
Hi all,

Performed following test:-

1)
Remove a working DVD-Writer from my stand-by Ubuntu PC and connect it to the Daily working PC

2)
On Terminal run

$ sudo lshw -C disk
```
 
  *-cdrom                   
       description: DVD-RAM writer
       product: DRW-24D5MT
       vendor: ASUS
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sr0
       version: 2.00https://ubuntuforums.org/showthread.php?t=2496103
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodis

```

3)
Insert a music CD and it can be detected automatically.

4)
After mounting the music CD, I can play all .wav files on all tracks.

**[COLOR="#FF0000"]It concludes that the Sony DVD-Writer has come to the end of its life.[/COLOR]**  I won't inject further effort to rescue it, including clearning it.  I would buy a new DVD-Writer. Nowadays its price is NOT expensive.

Meanwhile I'll perform ripping of music CDs on my stand-by Ubuntu PC. Actually I won't burn CD.  Please see my anther posting;

Abour ripping music CD to mp3 files
[https://ubuntuforums.org/showthread.php?t=2496103](https://ubuntuforums.org/showthread.php?t=2496103)

Lot of thanks for all of you to help me and your effort and time spent.

Thanks again for all of you.

Regards

---

