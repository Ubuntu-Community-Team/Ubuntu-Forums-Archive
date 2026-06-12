---
title: "CD Rom size reported wrong"
date: 2008-09-24
forum: General Help
---

### Post by dougie173 on 2008-09-24
I'm having a bit of a weird problem.

I've been running ddrescue to get some data off of some old CDs and DVDs I have have lying around.

It was working correctly, but now every CD or DVD I'm being reported as 1073 MB?!:confused:

If I run df -h i get this output:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             286G  191G   92G  68% /
...
/dev/scd0             4.3G  4.3G     0 100% /media/cdrom0

```



But if I run fdisk -l /dev/cdrom it reports an incorrect size:

```

Note: sector size is 2048 (not 512)

Disk /dev/cdrom: 1073 MB, 1073741312 bytes
255 heads, 63 sectors/track, 32 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x00000000

Disk /dev/cdrom doesn't contain a valid partition table

```

It doesn't matter whether I put a DVD or CD in the cd drive fdsik -l and subsequently ddrescue reports 1073MB

Any ideas?

---

### Post by Peter09 on 2008-09-24
Have you unmounted a previous DVD?

---

### Post by dougie173 on 2008-09-24
Yes I've tried unmounting as well as ejecting the CD/DVD

The CDs and DVDs mount correctly in nautilus and I can see all the files but when I try and run ddrescue (and fdisk) it tries to extract 1073 MB from both CDs (which are 650MB!!) and DVDs (4.3GB??)

---

### Post by Peter09 on 2008-09-24
try

fdisk -l /dev/scd0

---

### Post by dougie173 on 2008-09-24
This gives the same results as fdisk -l /dev/cdrom (Which is kind of expected as /dev/cdrom/, /dev/cdrw, /dev/dvd, and /dev/dvdrw are all just symbolic links to /dev/sdc0)

```

neal@whereever:~$ fdisk -l /dev/scd0
Note: sector size is 2048 (not 512)

Disk /dev/scd0: 1073 MB, 1073741312 bytes
255 heads, 63 sectors/track, 32 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x00000000

Disk /dev/scd0 doesn't contain a valid partition table


```

I can't even force it to try and extract more data:

```

neal@bonkserve:~$ ddrescue -v -b 2048 -s $(df |grep scd0|awk '{print $2}')k /dev/cdrom dsk201.iso log201


About to copy 1073 MBytes from /dev/cdrom to avi201
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 32 hard blocks
Hard block size: 2048 bytes
Max_retries: 0    Split: yes    Truncate: no


```

---

### Post by dougie173 on 2008-09-27
Just to add some more information to this thread:

I booted into the 2.6.24-18-generic kernel and this problem stopped. And the problem returned when I booted back into the 2.6.24-19-generic kernel.

---

