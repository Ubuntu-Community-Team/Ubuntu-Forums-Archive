---
title: "Speeding up CDROM/DVD reads"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by Viro on 2008-03-28
Hi there, I have a laptop which is suddenly having very slow CD-ROM drive reads. It takes about 10 minutes to copy a 640 MB file which is clearly unacceptable. In order to try and speed things up, I've run hdparm on it and below is the output.

```

/dev/scd0:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

IO_support can't be set to 32 bit since it's an SATA connection. I can't really see what's wrong. 

Anyone able to shed some light on this? It's very very weird.

---

### Post by Yellow Pasque on 2008-03-28
My drive gives the same output from hdparm, but doesn't have this problem. Try *sdparm -va /dev/scd0* or *sudo lshw -C disk*. I don't really know how to interpret the results of sdparm, but it will give you much more info than hdparm.

---

