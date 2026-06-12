---
title: "dvd burning, feisty, hdparm and dma questions"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by judgekaster on 2007-03-26
I have feisty installed and updated. I'm having problems with dvd-burning, using k3b, gnome-baker or the nautilus burner. Invariably, dvd burning fails unless I run it at 1x. And even at that speed, some data fail to write correctly. I use good-quality DVDs. CD burning is fine.

I tried to check the DMA settings, using hdparm, but don't get any information. 

```

sudo hdparm /dev/scd1

/dev/scd1:
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device


```
I get nothing when I try

```

sudo hdparm -d /dev/scd1

```

Seems there have been changes with the 2.6.20 kernel with regard to naming devices. Are there changes too with regard dma settings?

Any advise?

---

### Post by jetpeach on 2007-04-20
are you using a sata optical drive? if so, my understanding is DMA does not need to be enabled, see
[http://ubuntuforums.org/showthread.php?t=362612&highlight=HDIO_GETGEO+failed](http://ubuntuforums.org/showthread.php?t=362612&highlight=HDIO_GETGEO+failed)

---

### Post by andyanderso on 2007-04-20
I have the same issue when I try to check my dma settings.  When I was running edgy I used to get a line saying using dma=1 or using dma=0 depending on whether it was on or off when used "sudo hdparm /dev/hdb." Now I get:
[INDENT]andy@hermes:~$ sudo hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
andy@hermes:~$ [/INDENT]

I noticed that the drive id changed from hdb to sdc0 but i don't know if this would also indicate a change to SATA?

---

### Post by dc. on 2007-04-20
I have the same problem because I want to activate my harddrive's acoustic management feature with hdparm -M but it doesn't work anymore with Feisty and the new libata /dev/sdXX style.

the only parameters that still seem to work are -A and -W (read-lookahead and write-caching).

---

### Post by andyanderso on 2007-04-23
Has anyone made any headway with this issue?

---

### Post by junjan on 2007-04-27
:confused: 

Similar problem here. DVD -R are getting corrupted from Nautilus and Gnomebaker. Brasero not working also but without destroying the DVD.
CD burning ok.

---

### Post by dc. on 2007-05-04
bump

---

### Post by finalzero on 2007-05-05
This should be reported as a bug, i.e. Feisty treating IDE drives as SATA

---

### Post by vodalus on 2007-05-10
I have this problem as well:

$ sudo hdparm  /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

Has anyone filed a bug report for this?  If so post the number here so I can follow it.

---

### Post by andyanderso on 2007-05-21
I do not think anyone has filed a bug.  Anyone want to do it?  So far this issue does not seem to be changing my computer's performance.

---

### Post by dc. on 2007-05-28
Solved with 2.6.20-16-generic

---

### Post by divali on 2007-05-29
Please explain how you came to correct the problem. There are quite a few of us with this little nuisance. 
Thanks

---

### Post by jdk_ on 2007-08-21
The problem persists for me, and I do have 2.6.20-16-generic.

Any help?

---

### Post by ril560 on 2007-09-26
Add me to the list of people this affects.

---

### Post by bluebuzzard on 2007-10-05
me too. CD creator gives error messages or freezes when trying to burn a data CD.

---

### Post by dinub1 on 2007-10-05
> **finalzero said:**
> This should be reported as a bug, i.e. Feisty treating IDE drives as SATA

Why? a SATA drive is by default an IDE device (they can be P-ATA, S-ATA or ATAPI). :popcorn:

---

