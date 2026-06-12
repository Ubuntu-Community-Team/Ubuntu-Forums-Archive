---
title: "Cannot format Lexar Micro SD card"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by rakzor on 2008-03-06
Here's my problem. I got a Lexar Micro SD a few days ago and I can't format it. Google doesn't help at all and I've tried everything I can to get it to work.

Here is the output of dmesg

```
 [166860.201098] sd 22:0:0:0: [sdd] Device not ready: <6>: Sense Key : Not Ready
[current] 
[166860.201109] : <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[166860.201118] end_request: I/O error, dev sdd, sector 8
[166860.205086] sd 22:0:0:0: [sdd] Device not ready: <6>: Sense Key : Not Ready
[current] 
[166860.205098] : <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[166860.205107] end_request: I/O error, dev sdd, sector 8
[166860.209092] sd 22:0:0:0: [sdd] Device not ready: <6>: Sense Key : Not Ready
[current] 
[166860.209106] : <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[166860.209114] end_request: I/O error, dev sdd, sector 8
[166860.213092] sd 22:0:0:0: [sdd] Device not ready: <6>: Sense Key : Not Ready
[current] 
[166860.213106] : <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[166860.213114] end_request: I/O error, dev sdd, sector 8
[166860.217091] sd 22:0:0:0: [sdd] Device not ready: <6>: Sense Key : Not Ready
[current] 
[166860.217104] : <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[166860.217113] end_request: I/O error, dev sdd, sector 8
[166860.220470] sd 22:0:0:0: [sdd] Device not ready: <6>: Sense Key : Not Ready
[current] 
[166860.220483] : <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[166860.220492] end_request: I/O error, dev sdd, sector 8
[166860.225093] sd 22:0:0:0: [sdd] Device not ready: <6>: Sense Key : Not Ready
[current] 
[166860.225105] : <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[166860.225114] end_request: I/O error, dev sdd, sector 8
[166860.229090] sd 22:0:0:0: [sdd] Device not ready: <6>: Sense Key : Not Ready
[current] 
[166860.229105] : <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[166860.229113] end_request: I/O error, dev sdd, sector 8
[166860.233090] sd 22:0:0:0: [sdd] Device not ready: <6>: Sense Key : Not Ready
[current] 
[166860.233103] : <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[166860.233112] end_request: I/O error, dev sdd, sector 0  
```

It will show under GParted but just as unallocated and won't let me format.

---

### Post by wolfen69 on 2008-03-06
open gparted via terminal
```
sudo gparted
```
```
sudo umount /dev/sdax
```
replace sdax with what your card is.
you should be able to format it now. sudo is the key here. you cant do these things as a regular user.

---

### Post by rakzor on 2008-03-06
It says "Error while creating disklabel" 

And in the terminal it says 

```
Unable to open /dev/scd1 read-write (Read-only file system).  /dev/scd1 has been opened read-only.
Unable to open /dev/scd1 - unrecognised disk label.
Unable to open /dev/sdd - unrecognised disk label.
Unable to open /dev/sdd - unrecognised disk label.
Input/output error during read on /dev/sdd
Input/output error during write on /dev/sdd
```

---

