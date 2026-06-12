---
title: "setting DMA and 32bit IO on SATA in Feisty"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by finite9 on 2007-04-03
On an old laptop with dapper, I can set dma and 32bit IO on hda or hdc with:

```
hdparm -d1 -c1 /dev/hdc
```

In Feisty with an SATA drive neither command works:

```
andrew@everest:~/Photos$ sudo hdparm -d1 -c1 /dev/scd0
Password:

/dev/scd0:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 IO_support   =  0 (default 16-bit)

```

Does Hdparm work with SATA drives?  Why wont these commands work with SATA but work fine with ATA drives?

---

### Post by hazelkid on 2007-04-21
I encountered the same problem. 

```
hdparm -d1 -c1 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 IO_support   =  0 (default 16-bit)

```

I googled up a little and i got something like hdparm isn't working for sata drives and use sdparm instead. sdparm seems to be a similar hdparm tool but for scsi and I can't figure out how to make it work on my sata.

---

### Post by kevinatkins on 2007-04-21
I'm having the same problem, too... and I'm somewhat confused by it. Disk performance is awful!

---

### Post by finite9 on 2007-04-21
I mailed the developer of sdparm and he doesn't know how to do this either because it depends on the capabilities of the drive.  He asked me to read through some SATA spec PDFs and try to see what the DVD-RW drive supported to help him troubleshoot this, but I do not have very much time to look into this.  If the dev does not have any concrete suggestions them I do not hold out much hope of this being fixed unless a later kernel supports it better.

---

### Post by robertobech on 2007-04-21
Count one more with this problem... I dont even have a SATA drive, but since Ubuntu now treats IDE HDs the same way as SATA HDs I can't make dma work.

---

### Post by nubutu on 2007-04-23
Same here...and still haven't found anything.

---

### Post by robertobech on 2007-04-23
Worse yet: I've just found out that when burning CDs things go incredibly slooooooowwwww... when my CD burner was recognized as hdc hdparm worked fine, but now hat it's seen as scd0, no DMA!

---

### Post by atze76 on 2007-04-24
same problem here. With dapper (6.06) the harddrive was mapped to /dev/hdx and there was no problem to change the parameters. But with feisty (7.04) all the drives are mapped to /dev/sdx. I cannot even watch dvds. It is real pain in the a**. I thought the graphics driver would be the cause for choppy video playback, but now I suspect that it is the 16-bit I/O setting of my HD and DVD drive.

---

### Post by hazelkid on 2007-04-24
to be honest I haven't noticed any problems playing dvd's, but when i try to copy/move files from one partition to another it goes very slow; usually 6Mb/sec (used to get up to 50Mb/sec in windows with Total Commander. And with ext3/xfs partitions windows is useless.

---

### Post by nubutu on 2007-04-26
Hi

I posted in the following thread some information gathered from usenet, it might work:

[http://ubuntuforums.org/showthread.php?t=415057](http://ubuntuforums.org/showthread.php?t=415057)

And, I may be talking rubbish, but considering both threads deal with exactly the same issue, is there a way to merge them or something, so if somebody looks for this issue doesn't miss anything?

Cheers

---

### Post by hazelkid on 2007-04-26
Well i had no better choice but reinstalling edgy. It works much better for me than Feisty. Happy Edgy user here. Values from "hdparm -Tt" are double compared to Feisty. However I my SATA drive still works on 16 bit transfer instead of 32 and no visible DMA resulting my copy/move speed to be a quarter to the one I get in Windows.

About the Usenet info, I belive it is not a solution for me having a SATA disk drive. :(

---

### Post by robertobech on 2007-04-26
Man, I can't understand how this kind of thing can happen to Ubuntu. You see, I really love Ubuntu, but I can't recommend Ubuntu Feisty to my friends if they can't watch DVDs or burn CDs at a reasonable speed. And I don't see the Ubuntu team even mentioin the problem to its users. Is there a bug open or some stuff like that?

---

### Post by Strannik on 2007-04-27
I am having the same problem with this, this is really just scary, not like the ubuntu team at all! what can be done to get it working normally?

---

### Post by psusi on 2007-04-27
Just to make sure, this issue is with ide drives, not sata right?  Have you filed a bug report?

---

### Post by Strannik on 2007-04-27
yes, I did. [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/110636)
and yes, i have a regular ide drive

---

### Post by nubutu on 2007-04-28
Hi

I found something quite intereresting here.

[http://linux-ata.org/faq.html](http://linux-ata.org/faq.html)

I think many things are clearer now. For those of you who have not DMA activated in the optical drive it would be worth to try what's said there. Also, there's a list of features and current state of affairs for the supported hardware. 

For the less serious problem of acoustic management with hdparm--which I believe it's done automatically--I still haven't found anything. As for hdparm -tT /dev/sda, I'm getting the same result as before for the buffered disk reads and half what it used to be in Edgy for the cached reads--maybe because of the multicount setting not activated?

Anyway...

---

### Post by Strannik on 2007-04-28
anyway, its till a big showstopper for me.. really strange, and still no workaround or even any patches (updating daily)

---

### Post by finite9 on 2007-04-30
just want to add that I found out that 32bit IO is *only relevant* for drives that are *not* connected via the standard ribbon cable!  If your drive is in a laptop or on a standard ribbon cable connected to the controller, than apparently, 32bit IO has no effect as all S/ATA drives are still only 16Bit on the interface.  This is according to the hdparm manpage under -c option.

If this is true, and DMA is enabled on my drives, then I don't know really where the speed problem really lies??  It is not just cdrom, but hard drives as well, that run really slow compared to my other older laptop with PATA drive running Dapper.

Also, DMA is standard on SATA drives, so I know this is enabled.  My drive however does not support NCQ.  looking at the linux-ata site, 32Bit IO is not supported and is low priority because most transfers takeplace over DMA, and very few use PIO.

---

### Post by chalewa on 2007-04-30
> **finite9 said:**
> just want to add that I found out that 32bit IO is *only relevant* for drives that are *not* connected via the standard ribbon cable!  If your drive is in a laptop or on a standard ribbon cable connected to the controller, than apparently, 32bit IO has no effect as all S/ATA drives are still only 16Bit on the interface.  This is according to the hdparm manpage under -c option.

If this is true, and DMA is enabled on my drives, then I don't know really where the speed problem really lies??  It is not just cdrom, but hard drives as well, that run really slow compared to my other older laptop with PATA drive running Dapper.

Also, DMA is standard on SATA drives, so I know this is enabled.  My drive however does not support NCQ.  looking at the linux-ata site, 32Bit IO is not supported and is low priority because most transfers takeplace over DMA, and very few use PIO.

my hard disc is actually beyond slow.

---

### Post by isazi on 2007-05-01
Never had an hard drive so slow, and it's not my fault, cause with edgy all was good.
I don't blame ubuntu developer for the decision taken for feisty, but until hdparm support the new subsystem i cannot use it, my system is slow and noisy, and sdparm cannot work cause my disk is an ide disk (and yes, i've tryed).
Wish we can go beyond this problem soon, cause ubuntu deserve all the better :)

---

### Post by robertobech on 2007-05-02
I've noticed something strange. As I said, Feisty now sees my IDE HD as sda instead of hda, and so I can't use hdparm on it anymore. However, I installed Feisty on my wife's PC yesterday and her Ubuntu calls her IDE HD hda. Now I'm really confused...

---

### Post by Martijn van Es on 2007-05-03
Hey robertobech
I think you will find difference in the kernel versions both systems use. type uname -a in konsole and plz post output here since i am curious.

---

### Post by chalewa on 2007-05-03
edit

---

### Post by Martijn van Es on 2007-05-05
Come on... it is very quiet here! Nobody came up with a solution?

---

### Post by bandan on 2007-05-05
> **Martijn van Es said:**
> Come on... it is very quiet here! Nobody came up with a solution?

You should have read [http://linux-ata.org/faq.html]("http://linux-ata.org/faq.html") posted by nubuntu.
In short, with sata every data transfer goes through dma, so it doesn't matter if the hdd is accessed in 16bit or 32 bit mode. And dma is always on.

bandan

---

### Post by chalewa on 2007-05-05
> **bandan said:**
> You should have read [http://linux-ata.org/faq.html]("http://linux-ata.org/faq.html") posted by nubuntu.
In short, with sata every data transfer goes through dma, so it doesn't matter if the hdd is accessed in 16bit or 32 bit mode. And dma is always on.

bandan

um no

---

### Post by Martijn van Es on 2007-05-07
Well Bandan, if that is true, what could be causing the ultra slow transferspeeds for the PATA disks of all the people in this thread?
And is there a command we can type in the shell to view the value of the automatic settings?

---

### Post by finite9 on 2007-05-08
> **Martijn van Es said:**
> Well Bandan, if that is true, what could be causing the ultra slow transferspeeds for the PATA disks of all the people in this thread?
And is there a command we can type in the shell to view the value of the automatic settings?

Well, Bandan *did* say that this was for SATA disks.  PATA disks do *not* have DMA enabled by default, so you still need to try to enable this with ```
hdparm -d1 /dev/xda
``` where x is either h or s.

SATA disks have DMA as a requirement of the standard which is why its enabled by default.

I do not know where the problem lies, but as I am the original thread starter and this thread concerns SATA disks only then maybe you guys with PATA disks have another issue.

I think there is already a bug report on launchpad for this, not created by me, and it does seem that maybe this is something for the devs to fix, as using hdparm or sdparm does not do the job.

---

### Post by psusi on 2007-05-08
> **finite9 said:**
> Well, Bandan *did* say that this was for SATA disks.  PATA disks do *not* have DMA enabled by default, so you still need to try to enable this with ```
hdparm -d1 /dev/xda
``` where x is either h or s.

SATA disks have DMA as a requirement of the standard which is why its enabled by default.

I do not know where the problem lies, but as I am the original thread starter and this thread concerns SATA disks only then maybe you guys with PATA disks have another issue.

I think there is already a bug report on launchpad for this, not created by me, and it does seem that maybe this is something for the devs to fix, as using hdparm or sdparm does not do the job.

You seem to misunderstand.  The whole problem is that hdparm does not work on scsi devices, so you can't use it on /dev/sda.

---

### Post by Martijn van Es on 2007-05-12
martijn@laptop:~$ sudo hdparm -d1 /dev/sda
Password:

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

---

### Post by SergeiFranco on 2007-05-12
Have same problem here is my post:
[http://ubuntuforums.org/showthread.php?p=2640646#post2640646](http://ubuntuforums.org/showthread.php?p=2640646#post2640646)

---

### Post by finite9 on 2007-05-13
> **psusi said:**
> You seem to misunderstand.  The whole problem is that hdparm does not work on scsi devices, so you can't use it on /dev/sda.

Err, no I don't misunderstand the problem, but maybe my post misleads a bit.

The issue on this thread is that with an SATA drive, performance is slow.  hdparm does not work on SATA disks (or those using sda as device) and sdparm can not increase performance/is very difficult to interpret to be able to increase performance: nothing seems at face value to increase performance with sdparm.

With SATA drives, DMA is always enabled, and setting 32bit IO on either PATA or SATA drives makes no difference for drives connected using standard ribbon cable, so using hdparm with a SATA drive is completely pointless from a performance perspective.  Therefore, it is unlikely that the problem can be solved at all by configuring with hdparm/sdparm.  I made the comment about setting DMA for PATA drives, as DMA is not enabled as standard on PATA drives, but as I do not have one of these, I did not realise that *some* people with PATA drives are seeing them as sda and not hda.  Note that not everyone has this issue.  Some people with PATA drives and Feisty see their device as hda still, and they can set DMA with hdparm.

The problem is most likely something more fundamental in the scsi device driver.

---

