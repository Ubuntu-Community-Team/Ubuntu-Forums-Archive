---
title: "dd stuck trying to recover a dead disk"
date: 2013-06-12
forum: Hardware
---

### Post by vilman on 2013-06-12
Hi, 

lost a disk, trying to recover it by using dd, and hopefully being able to repair the partition on a new disk. 

The disk is an iOmega external USB, have tried to dismantle it to make it internal to have a better control of the disk (like 'SMART ctl'...) but it is welded. 

Run command: 

after some internet research, decide to try:

sudo dd  if=/dev/sdc of=/media/temp/oldHD  conv=noerror,sync bs=32M

dd gets stuck on byte 2583691264: 

```

laptop:~$ sudo dd  if=/dev/sdc of=/media/temp/oldHD  conv=noerror,sync bs=32M 
dd: reading `/dev/sdc': Input/output error
76+1 records in
77+0 records out
2583691264 bytes (2.6 GB) copied, 152.213 s, 17.0 MB/s
dd: reading `/dev/sdc': Input/output error
76+1 records in
77+0 records out
2583691264 bytes (2.6 GB) copied, 152.544 s, 16.9 MB/s
dd: reading `/dev/sdc': Input/output error
76+1 records in
77+0 records out
2583691264 bytes (2.6 GB) copied, 152.696 s, 16.9 MB/s
dd: reading `/dev/sdc': Input/output error
76+1 records in
77+0 records out

```

20 minutes later, stuck in the same byte

```
2583691264 bytes (2.6 GB) copied, 1117.79 s, 2.3 MB/s
76+1 records in
77+0 records out
```


the resulting image has not grown a byte. 


Have I misplaced the 'conv' dd options? 

some ideas? 


thanks!

---

### Post by The Cog on 2013-06-12
I have heard of this, but not needed to use it. There is a package gddrescue in the Ubuntu repositories. It may be worth a shot.
[http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html](http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)

---

### Post by vilman on 2013-06-13
Cool! this one at least does not gets stuck. I'll go deep into that, and post some update.

---

