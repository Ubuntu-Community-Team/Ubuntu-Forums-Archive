---
title: "Problems since todays update"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by Nemmasis on 2009-03-21
I normally start my T61 Thinkpad on battery and plug it in when I'm done or the battery gets low. Today it ran the updates while on AC and I shut it down when finished. When I turned it on later it tried doing a file system check and failed and will now only start up while on battery so that it skips the check. I can't say for sure it was todays updates that caused it but here they are;

Upgraded the following packages:
gstreamer0.10-plugins-good (0.10.7-3ubuntu0.1) to 0.10.7-3ubuntu0.2
libavcodec1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavformat1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavutil1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libglib2.0-0 (2.16.6-0ubuntu1) to 2.16.6-0ubuntu1.1
libjasper1 (1.900.1-3) to 1.900.1-3ubuntu0.8.04.1
libnss3-1d (3.12.0.3-0ubuntu0.8.04.4) to 3.12.0.3-0ubuntu0.8.04.5
libpostproc1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
thunderbird (2.0.0.19+nobinonly-0ubuntu0.8.04.1) to 2.0.0.21+nobinonly-0ubuntu0.8.04.1

I don't know how to capture the error messages that pop up during boot, but it did say something about completing the file system check manually.

I found this in the system log;

EXT3-fs warning: mounting fs with errors, running e2fsck is recommended

Any suggestions?

---

### Post by cariboo on 2009-03-21
THe error message you are getting has nothing to do with the update, Linux automatically checks the health of your hard drive every 26 boots. There was an error found, and the drive must be unmounted to do a full check.

I would suggest you boot from your LiveCD and at the desktop open an Applications-->Accessories-->terminal and type:

```
sudo e2fsck /dev/sda1
```

You will have to substitue your partion label for /dev/sda.

Jim

---

