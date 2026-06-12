---
title: "DVD drive can't read some of the DVDs/VCDs"
date: 2013-11-10
forum: Hardware
---

### Post by amitst on 2013-11-10
I noticed that my DVD reader is not able read any of my data CDs. It is able to read DVDs (though unable to detect selective DVDs which I know them to work well on another desktop).

What might be wrong? 

Here are my machine specs:
```

Processor: Intel® Core&#8482;2 Duo CPU E4600 @ 2.40GHz × 2 
Graphics: Intel® 945G x86/MMX/SSE2
32-bit OS

```

Here is the dmesg and /proc/sys/dev/cdrom/info output:
```

$ dmesg | egrep -i --color 'cdrom|dvd|cd/rw|writer'
[    0.711373] ata1.00: ATAPI: Optiarc DVD RW AD-7200A, 1.06, max UDMA/66
[    0.865904] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7200A  1.06 PQ: 0 ANSI: 5
[    0.868269] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.868274] cdrom: Uniform CD-ROM driver Revision: 3.20

$ less /proc/sys/dev/cdrom/info
CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:		sr1	sr0
drive speed:		1	48
drive # of slots:	1	1
Can close tray:		1	1
Can open tray:		1	1
Can lock tray:		1	1
Can change speed:	0	1
Can select disk:	0	0
Can read multisession:	1	1
Can read MCN:		1	1
Reports media changed:	1	1
Can play audio:		1	1
Can write CD-R:		0	1
Can write CD-RW:	0	1
Can read DVD:		0	1
Can write DVD-R:	0	1
Can write DVD-RAM:	0	1
Can read MRW:		0	1
Can write MRW:		0	1
Can write RAM:		0	1

```

---

### Post by amitst on 2013-11-11
Bump :)

Do you think not able to read CD might be related to hardware problem in my desktop's DVD writer?

---

