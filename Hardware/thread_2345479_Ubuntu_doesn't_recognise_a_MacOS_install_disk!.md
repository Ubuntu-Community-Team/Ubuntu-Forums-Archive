---
title: "Ubuntu doesn't recognise a MacOS install disk!"
date: 2016-12-04
forum: Hardware
---

### Post by vlitzanov on 2016-12-04
I have a bunch of Mac install CD's that install OS X Panther and OS 9.0.4. Some of these CD's are in TERRIBLE condition and I want to copy all of them over to my PC (Running Ubuntu 14.04 32-bit & Win7 64-bit) for a re-burn. 

A small sample:

[ATTACH=CONFIG]272541[/ATTACH]
[SIZE=1]I don't even know how this happened. The others only have the data film peeling off.[/SIZE]

The problem is, I can't get anything to recognize and mount the CD's so I can copy the files. I've tried the terminal, multiple programs, anything I could find. Nothing worked. I do have a working iMac G3 in the basement, but the DVD drive is beyond repair (YAY!). 

Any ideas of how I can read these CD's? What format do they use?

Thing's I've tried list:

[LIST]
[*]HFVExplorer (Hard to find)
[*]HFSExplorer
[*]Terminal with following:
[/LIST]
```

[FONT=Verdana]sudo mkdir /media/test[/FONT]
sudo mount -t iso9660 /dev/cdrom /media/test
ls /media/test
sudo mount -t udf /dev/cdrom /media/test
ls /media/test
sudo mount -t hfs /dev/cdrom /media/test
ls /media/test
sudo mount -t hfsplus /dev/cdrom /media/test
ls /media/test

```

---

### Post by QIII on 2016-12-04
Hello and welcome to the Forums!

I would say the two most likely issues are:

1.  The disks are in "TERRIBLE" condition.  :)

2.  The disks contain protection of some sort that check to see if they are being run on Apple hardware.  I'd think the protection would keep them from being "run", not detected, but you never know.

My money is on possibility #1 (if the disks are delaminating, you can forget them), in which case there is very little anyone can do.

---

### Post by vlitzanov on 2016-12-05
Ok then. Thanks!

Unfortunate that I can't get them to work.

---

### Post by karl96 on 2016-12-05
What's the output of 
```
df -T
```

---

