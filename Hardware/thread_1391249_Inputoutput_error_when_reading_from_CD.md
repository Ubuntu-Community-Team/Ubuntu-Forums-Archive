---
title: "Input/output error when reading from CD"
date: 2010-01-26
forum: Hardware
---

### Post by ThomasTC on 2010-01-26
I'm trying to convert an audio CD to an ISO image, but all my attempts run into a brick wall. I'm beginning to suspect that this might be a kernel bug.

The following happens on an Intel i7 system, running an up-to-date Ubuntu Karmic, Desktop Edition, 64-bits. My kernel is 2.6.31-16-generic.

My DVD-RW drive is:
```
$ sudo lshw -class disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7170A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.O3
       serial: [Optiarc DVD RW AD-7170A 1.O3 Jul14,2006 BT-LIG
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```

First attempt:

```
$ dd if=/dev/sr0 of=image.iso
dd: reading `/dev/sr0': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.127185 s, 0.0 kB/s

$ dmesg
...
[  276.480290] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  276.480295] sr 6:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  276.480299] sr 6:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  276.480305] end_request: I/O error, dev sr0, sector 0
[  276.480309] __ratelimit: 78 callbacks suppressed
[  276.480311] Buffer I/O error on device sr0, logical block 0
[  276.480314] Buffer I/O error on device sr0, logical block 1

```

Permission problem? Running as root gives the same result. Besides, I do have read permission as a normal luser:

```
$ getfacl /dev/sr0
getfacl: Removing leading '/' from absolute path names
# file: dev/sr0
# owner: root
# group: cdrom
user::rw-
user:thomas:rw-
group::rw-
mask::rw-
other::---
```

Different CD? I tried two other discs, same problem. It's not the CD itself that is broken.

Drive broken? But I've just been using it to listen to this very CD (in Rhythmbox) for *at least twenty minutes*!

Next attempt: dd_rescue. It's dd with smarter error handling.

```
$ dd_rescue /dev/sr0 image.iso
dd_rescue: (info): ipos:         0.0k, opos:         0.0k, xferd:         0.0k
                *  errs:      0, errxfer:         0.0k, succxfer:         0.0k
             +curr.rate:        0kB/s, avg.rate:        0kB/s, avg.load:  0.0%
dd_rescue: (warning): /dev/sr0 (0.0k): Input/output error!

dd_rescue: (info): ipos:         0.5k, opos:         0.5k, xferd:         0.5k
                *  errs:      1, errxfer:         0.5k, succxfer:         0.0k
             +curr.rate:      444kB/s, avg.rate:      150kB/s, avg.load:  0.0%
dd_rescue: (warning): /dev/sr0 (0.5k): Input/output error!

dd_rescue: (info): ipos:         1.0k, opos:         1.0k, xferd:         1.0k
                *  errs:      2, errxfer:         1.0k, succxfer:         0.0k
             +curr.rate:      449kB/s, avg.rate:      225kB/s, avg.load:  0.0%
dd_rescue: (warning): /dev/sr0 (1.0k): Input/output error!

dd_rescue: (info): ipos:         1.5k, opos:         1.5k, xferd:         1.5k
                *  errs:      3, errxfer:         1.5k, succxfer:         0.0k
             +curr.rate:      417kB/s, avg.rate:      266kB/s, avg.load:  0.0%
dd_rescue: (warning): /dev/sr0 (1.5k): Input/output error!

...

```

It gives a read error on *every single block*!

I searched around, of course, and found that it might be related to hibernating. I'd just booted a hibernated system, so I rebooted (cold), but still got the same problem.

And still, at times, I can just play the CD as if nothing is the matter. At other times, Rhythmbox will hang or also throw I/O errors at me, but it could be that my read attempts upset the drive.

In Windows 7 (also 64-bit) using CloneCD, I can read the disc just fine.

I'm at a loss here. Anybody any idea what else I could try?

---

### Post by jasloper on 2010-01-28
I had the same sort of errors when I used a CD/RW disc.  Someone on this forum suggested it was a bad disk.  I got some CD-R discs, and burned a new image.  Loaded just fine.

---

### Post by gecka on 2010-03-27
Exactly same problem here. I tried other CDs with same result.

```
sudo dd if=/dev/sr0 of=cdimage.iso
dd: reading `/dev/sr0': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0260971 s, 0.0 kB/s
```

whereas brasero can create an iso image from that CD.

---

### Post by ifreecarve on 2010-10-21
i'm experiencing this now and it's really frustrating.  what do i have to do to enable dd or cat to work on my cdrom?

---

### Post by psusi on 2010-10-21
An ISO image is an image of the iso9660 cdrom filesystem for storing data files.  An audio cd does not contain a filesystem, so what you are trying to do makes no sense.

If you want to rip an audio cd, you need to use something meant for that, like cdparanoia, or just fire up Rhythmbox.

---

### Post by mciverza on 2012-01-28
> **psusi said:**
> An ISO image is an image of the iso9660 cdrom filesystem for storing data files.  An audio cd does not contain a filesystem, so what you are trying to do makes no sense.

If you want to rip an audio cd, you need to use something meant for that, like cdparanoia, or just fire up Rhythmbox.

Brasero runs this command (one line) to create the image:

cdrdao read-cd --device /dev/sr0 --read-raw --datafile ~/Audio-Disc.toc.bin -v 2 ~/Audio-Disc.toc

---

