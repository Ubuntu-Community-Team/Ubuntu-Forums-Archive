---
title: "DVD drive won't mount for some reason..."
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2007-03-30
I have a few data DVD's that I burned with Nero on a Windows Box a few months ago.  But when I load them into a DVD drive (I've tried this one two different computers, both running Ubuntu), it doesn't mount the drive.  When I open up Places>Computer and then select the cd/dvd rom drive, it produces the following error:


```
mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       in some cases useful info is found in syslog - try
       dmesg | tail  or so
```

What should I do?

Edit:  By the way, the discs are 100% readable under windows XP.  I can read them right now from there.  But why not Linux?

---

### Post by Boopop on 2007-04-08
Same here, except my dvd is a game that I bought. Windows XP reads it fine.

---

### Post by vladc on 2007-04-08
Please post output of the 'dmesg' command. Thanks.

---

### Post by diablo75 on 2007-04-12
Well, before attempting the 'dmesg' command, I double checked to see if the disc would still not read, and if so, then run the command.  But it did read the disc this time.

I recently upgraded to version 7.04 beta, so that might have something to do with it.

No problems now.

---

