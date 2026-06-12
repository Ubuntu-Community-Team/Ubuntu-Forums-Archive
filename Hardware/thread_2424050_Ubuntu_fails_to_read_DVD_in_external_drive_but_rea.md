---
title: "Ubuntu fails to read DVD in external drive but reads CDs"
date: 2019-08-02
forum: Hardware
---

### Post by a1023132 on 2019-08-02
I purchased an external Blu-ray disc/DVD drive (LG WH16NS40) that connects via USB, but DVD's don't work.
[LIST]
[*]Both the DVD's I tested worked on my Windows machine (I played them and also was able to make copies using MakeMKV) but not my Ubuntu machine, using the same drive. 
[*]When there's a DVD in the drive, the disk utility says "no media" ([https://i.imgur.com/X5tcb4G.png](https://i.imgur.com/X5tcb4G.png)) and MakeMKV can't load the disc (it gets stuck). 
[*]"eject" in the terminal fails and just hangs indefinitely 
[*]"sudo fdisk -lu" hangs indefinitely 
[*]"sudo lshw -C disk" hangs indefinitely 
[*]"ls -al /dev/sr0" hangs indefinitely when it says 'SCSI' 
[*]"regionset" also hangs when I try to set the region. 
[/LIST]

The last five bullet points apply only when there's a DVD in the drive. I tested it with a CD and with no disc, and none of the five commands failed. With the CD in the drive, I did "regionset" and set the region to 1 but that didn't fix anything. Not sure what to do.

Whenever the hanging would occur and I unplugged the drive, I got the following error message: [https://i.imgur.com/ZbrXadZ.png](https://i.imgur.com/ZbrXadZ.png) ("Error mounting /dev/sr0 ... special device /dev/sr0 does not exist").

---

### Post by kpatz on 2019-08-02
Have you tried the USB drive on the Windows machine to see if it works there?  To rule out the drive being faulty.

---

### Post by a1023132 on 2019-08-02
> **kpatz said:**
> Have you tried the USB drive on the Windows machine to see if it works there?  To rule out the drive being faulty.

Yes (When i tested the DVD on the Windows machine I did it using the same external drive.)

---

### Post by a1023132 on 2019-08-02
Is it possible that either the external enclosure or the usb cable that connects the enclosure to the laptop is causing the problem?

---

