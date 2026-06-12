---
title: "DMA won't enable on any hard drive"
date: 2008-05-16
forum: Hardware
---

### Post by xmrkite on 2008-05-16
Hello, I have a 8.04 install on a core 2 duo 1gb ram computer. DMA won't enable on any of my hard drives.

Here is what i run to enable dma:

sudo hdparm -d1 /dev/sdc

It returns:

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device


This is a seagate 500gb ide drive hooked up as the primary slave.

As a result, video playback is not too great and very choppy. Also, file transfers are pretty slow...not horribly slow, but slower than when i was with ubuntu feisty.

Any ideas?
-Thanks

---

### Post by sdennie on 2008-05-16
Many (all?) SATA drives don't need to have DMA manually enabled (and don't support it via hdparm).  What is the output of:

```

sudo hdparm -I /dev/sdc
sudo hdparm -tT /dev/sdc

```

---

### Post by xmrkite on 2008-05-17
Hello, here are the results:

sudo hdparm -I /dev/sdc

/dev/sdc:
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(identify) failed: Input/output error


sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   1036 MB in  2.00 seconds = 517.99 MB/sec
 Timing buffered disk reads:   70 MB in  3.04 seconds =  23.04 MB/sec



Also, keep in mind, this is not an sata drive, it's an ide drive.

-Thanks

---

### Post by sdennie on 2008-05-17
That's odd that hdparm -I doesn't work but, are you sure that DMA isn't working?  23M/sec seems quite fast for and ide drive not having DMA.  You could see if "hdparm -i" works and gives any more information.

---

### Post by xmrkite on 2008-05-17
Here's what i get:

sudo hdparm -i /dev/sdc

/dev/sdc:
 HDIO_GET_IDENTITY failed: Invalid argument


Any ideas?

---

### Post by sdennie on 2008-05-17
I'm not sure why none of the information commands in hdparm aren't working but, I do think that DMA is enabled on your drive.  Have you ruled out the possibility that your graphics card isn't configured correctly?

---

### Post by xmrkite on 2008-05-17
It could be graphics drivers, but i highly doubt it. I have nvidia 7300 card and mythbuntu installs the drivers automatically. Also, i notice that when the drive does just a little bit of activity other than the video being played back, the playback stutters very badly. This never happened with ubuntu 7.04, and i really tested it extensively, and i mean really extensively, by having the disk do over 12 reads while doing up to 6 writes, all at the same time. Now, in 8.04, if it does more than 4 reads or writes (total) it stutters more than when no reads are going on.

So i really don't think it's the drivers...besides, why is hdparm giving those weird errors?
-Thanks

---

### Post by nicedude on 2008-05-17
Check in your computers BIOS to see if DMA is supported/enabled there for starters as the BIOS have control that will supersede any Operating system in use. If not then enable DMA and select the highest mode it will allow you to.

---

### Post by xmrkite on 2008-05-18
Seems to me that dma is enabled in the bios.

Also, it appears we may have a bigger problem. I tried playing a file from an sata drive (as far as i know, sata does not use dma), and i experienced the same stuttering.

When there was nothing else running, the video played great, but as soon as i run another program in the backround, the video starts stuttering, even though the video file is on a different hard drive than the OS.

Any ideas? Seems like i should be able to play a video and do something else at the same time. Ubuntu 7.04 let me really push this system without any stuttering, and all of a sudden, now i can't do anything and watch a video at the same time...it really sucks and hopefully it's not something that will make me ditch ubuntu because i really like ubuntu and don't want to have to start shopping around for different linux systems.

-Thanks

---

### Post by sdennie on 2008-05-18
Ubuntu 7.04 didn't have compiz enabled by default I don't think.  If you hit Alt-F2 and then type: "metacity --replace" and then run your videos, does it help?

If not, what is the output of "uname -a"?  Maybe you are running the server kernel and the latency is so poor that video isn't playing well.

---

### Post by xmrkite on 2008-05-18
OK, when i run that command i get:

The command "metacity --replace" failed to run:

Failed to execute child process "metacity" (no such file or directory)


Please remember, i'm using mythbuntu which uses xfce and not gnome.

---

### Post by xmrkite on 2008-05-19
OK, i added in an sata hard drive, and when playing videos from that drive, i get the same stuttering, so it probably isn't dma, but it's gotta be something.

Are there some sort of tests i can run to find out where the lag is?

Thanks

---

