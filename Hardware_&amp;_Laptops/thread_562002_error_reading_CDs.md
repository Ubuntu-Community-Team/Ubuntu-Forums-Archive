---
title: "error reading CDs"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by Apo2k4 on 2007-09-28
Hi,
I've recently been having trouble reading some CDs - one was burned by a friend who uses Vista, the two others are audio CDs that are at least 15 years old, so there should be no fancy extras that should prevent access. The CDs open just fine in Win XP, but not on my two Ubuntu boxes with feisty and gutsy.
Here's what I tried so far:

apo@eyecookie:~$ sudo mount /dev/sr0 /media/cdrom0/ -t iso9660
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

apo@eyecookie:~$ dmesg | tail -n 100
[54401.088000] end_request: I/O error, dev sr0, sector 1248
[54401.092000] end_request: I/O error, dev sr0, sector 1024
[54401.092000] UDF-fs: No partition found (1)
[54401.104000] end_request: I/O error, dev sr0, sector 64
[54401.104000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[54415.732000] end_request: I/O error, dev sr0, sector 995712
[54415.732000] printk: 9 messages suppressed.
[54415.732000] Buffer I/O error on device sr0, logical block 124464
[54415.736000] end_request: I/O error, dev sr0, sector 995712
[54415.736000] Buffer I/O error on device sr0, logical block 124464
[54415.740000] end_request: I/O error, dev sr0, sector 995712
[54415.740000] Buffer I/O error on device sr0, logical block 124464
[54415.744000] end_request: I/O error, dev sr0, sector 0
[54415.744000] Buffer I/O error on device sr0, logical block 0
[54415.748000] end_request: I/O error, dev sr0, sector 0
[54415.748000] Buffer I/O error on device sr0, logical block 0
[54415.752000] end_request: I/O error, dev sr0, sector 0
[54415.752000] Buffer I/O error on device sr0, logical block 0
[54415.756000] end_request: I/O error, dev sr0, sector 995872
[54415.756000] Buffer I/O error on device sr0, logical block 124484
[54415.760000] end_request: I/O error, dev sr0, sector 995872
[54415.760000] Buffer I/O error on device sr0, logical block 124484
[54415.764000] end_request: I/O error, dev sr0, sector 995872
[54415.764000] Buffer I/O error on device sr0, logical block 124484
[54415.768000] end_request: I/O error, dev sr0, sector 995872
[54415.768000] Buffer I/O error on device sr0, logical block 124484
[54415.772000] end_request: I/O error, dev sr0, sector 995872
[54415.776000] end_request: I/O error, dev sr0, sector 995872
[54415.780000] end_request: I/O error, dev sr0, sector 995816
[54415.784000] end_request: I/O error, dev sr0, sector 995864
[54415.788000] end_request: I/O error, dev sr0, sector 995872
[54415.792000] end_request: I/O error, dev sr0, sector 995872
[54415.796000] end_request: I/O error, dev sr0, sector 0
[54415.800000] end_request: I/O error, dev sr0, sector 0
[54415.804000] end_request: I/O error, dev sr0, sector 0
[54415.808000] end_request: I/O error, dev sr0, sector 0
...
[54415.920000] end_request: I/O error, dev sr0, sector 995584
[54415.924000] end_request: I/O error, dev sr0, sector 995584
[54415.928000] end_request: I/O error, dev sr0, sector 995584
...
[54416.088000] end_request: I/O error, dev sr0, sector 0
[54416.092000] end_request: I/O error, dev sr0, sector 0
[54420.616000] end_request: I/O error, dev sr0, sector 64
[54420.616000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

apo@eyecookie:~$ sudo dd if=/dev/cdrom of=test.iso
dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0368366 seconds, 0.0 kB/s


That's what I tried so far. Any ideas what else I could try?

---

### Post by eggdeng on 2007-09-28
Sorry if I'm reading you wrong but are you trying to mount audio CDs? You can't / don't need to mount these - just specify an action in System ->Preferences ->Removable Drives & Media ->Multimedia Tab.

---

### Post by Apo2k4 on 2007-09-28
Indeed, it was an audio CD (didn't know you can't mount those), but it didn't work for the Vista CD either, and dd should work regardless of it being an audio CD or not, right?
Also, I tried to read them with Soundjuicer, but to no avail.

---

### Post by rickdog on 2007-09-29
i'm having the same problem. just got a cd burned in vista with a just a few jpeg on it and I could not read it on either a Kubuntu or Ubuntustudio box. what's up with that? I think it's another example of the crap that MS tries to pull. i can hardly wait till they're brought down or split up.

---

### Post by Apo2k4 on 2007-10-01
Been fooling around with some other audio CDs ---

Avantasia - The Metal Opera:

[77481.012000] end_request: I/O error, dev sr0, sector 0
[77481.012000] printk: 3 messages suppressed.
[77481.012000] Buffer I/O error on device sr0, logical block 0
[77481.012000] Buffer I/O error on device sr0, logical block 1
[77481.012000] Buffer I/O error on device sr0, logical block 2
[77481.012000] Buffer I/O error on device sr0, logical block 3
[77481.012000] Buffer I/O error on device sr0, logical block 4
[77481.012000] Buffer I/O error on device sr0, logical block 5
[77481.012000] Buffer I/O error on device sr0, logical block 6
[77481.012000] Buffer I/O error on device sr0, logical block 7
[77481.056000] end_request: I/O error, dev sr0, sector 0
[77481.056000] Buffer I/O error on device sr0, logical block 0
[77481.060000] end_request: I/O error, dev sr0, sector 4
[77481.060000] Buffer I/O error on device sr0, logical block 1

apo@eyecookie:~$ sudo dd if=/dev/cdrom of=test.iso
dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0478268 seconds, 0.0 kB/s

Blind Guardian - Live CD1: Same results

Jami Sieber - Lush Mechanique (Magnatune CD): Same results...

The Diablo 2: LOD disk worked, though... so there seems to be a problem with all audio CDs (all I tried so far, anyway...) and some normal data CDs (the ones burned by Vista?)

Tried dd'ing the CDs on another (feisty, this one's on gutsy) box, same results again...

---

