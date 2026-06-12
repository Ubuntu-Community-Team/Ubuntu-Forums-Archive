---
title: "[Hardy] Can't enable DMA on CDROM"
date: 2008-04-27
forum: Hardware
---

### Post by csete on 2008-04-27
I've recently upgraded from Gutsy to Hardy on both of my Ubuntu machines.  My laptop seems to be working ok.  While trying to rip a CD on my server machine, I'm finding that DMA is not enabled and I can't get it enabled. I've read comments on the net that this might be a kernel error, but I'm not sure.  As it stands, I can't really use the drive to do a rip because of the poor speed.

Can anyone help?
Thanks,
Craig

```

xxx@xxx:~$ uname -r
2.6.24-16-server

```

```

xxx@xxx:~$ sudo hdparm /dev/scd0

/dev/scd0:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

```

xxxx@xxxx:~$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

---

### Post by csete on 2008-04-28
Bump.  Anyone?


Am I going to have any trouble if I boot the machine with the Gutsy kernel?  I haven't checked to see if it is still installed after the upgrade.

I wonder if this is the same issue as the following?

[http://ubuntuforums.org/showthread.php?t=762115](http://ubuntuforums.org/showthread.php?t=762115)

---

### Post by janfsd on 2008-04-29
I got the same problem like you, which kind of recorder do you have? Mine is Asus 1608P
Another question: I have got problems to open and copy files from my cds since Hardy, I get input/output errors. Do you have them too?

---

### Post by justinlawrence on 2008-05-15
i've got the same problem on an IBM Thinkpad lenovo R60e. I have devoted over 8 hours to this and just can't get to the bottom of this. if anyone can point us in the right direction, it'd be hugely appreciated

---

### Post by csete on 2008-05-16
I should have replied to this thread earlier.  It turns out that the problem was the CD I was trying to rip and not the drive.  When I put in another CD, it worked just fine.

---

### Post by alih on 2008-05-23
I cured this problem by following mystictim's recipe ([link]("https://bugs.launchpad.net/ubuntu/+bug/175022")) :guitar:

---

### Post by mrestes on 2008-05-24
I'm having problems accessing my cdrom with certain applications. cd ripping is _slow_. I tried entering sudo hdparm /dev/scd0 and got the same error as above. I'm using Hardy Heron. VLC plays everything flawlessly. Totem couldnt find my disc unless it was in scd0 (wouldnt play scd1.) Grip wasnt able to detect any discs at all. Maybe this is a configuration error on my behalf? Not sure. 

 - Rusty

---

