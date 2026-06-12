---
title: "USB problem: last message &quot;waiting for device to settle before scanning&quot;"
date: 2008-07-27
forum: General Help
---

### Post by thehagman on 2008-07-27
Hello,

when attaching my digicam to USB port, the connection does not complete.
This is what happens:
1) connect cable.
2) camera (Panasonic DMC-FX01) asks PC or Pictbridge?
3) I answer PC
4) popup appears and asks what to do  (open in new window / open with didicam software / do nothing)
5) no matter what I reply, the result is that I cannot see the data on the cam; however, the camera icon appears on the desktop. Also, when I use digicam software, it can autodetect the camera (but not access data). 

Sometimes (today only after about 20 tries) the device is not recognized as a camera but rather merely as "generic" mass storage (the popup comes with a USB stick icon instead of a camera icon). Once this happens, I *can* access the data on the camera.

Similar things have happened with a TomTom instead of the camera, so I don't think it is a problem with the camera

Today I noticed that in those cases when things do not work, the last message in dmesg reads:

usb-storage: waiting for device to settle before scanning

When everything works fine, a device scan complete message (and more) ouccurs almost immediately after that. 

I am not totally sure but I have a feeling like hitting "cancel" in the popup when it appears with the camera icon helps increases the probability of obtaining the usb-stick-and-working variant in later experiments, but this may be superstition.

---

### Post by kuja on 2008-07-28
Try what they did in this thread: [http://ubuntuforums.org/showthread.php?t=143593](http://ubuntuforums.org/showthread.php?t=143593)

---

### Post by silkstone on 2008-07-28
I'm sorry I can't help directly, but perhaps it would be easier to transfer the files with a card reader rather than by hooking up the camera itself. I've always found that quicker and more reliable.

---

### Post by marcio123 on 2010-05-31
I have the same problem :/ on ubuntu 10.04 (on 9.10 it was pertect) 
Only few pendrives work on my laptop.  

Rest works only if I boot ubuntu with them already attached.


Is there a way to force it to settle so it can do this scanning?

---

### Post by marcio123 on 2010-06-19
I have the same problem on my 3 laptops (2 asus, 1 toshiba) 

1 has 64 bit 10.04
2 have 32 bit 10.04


lsusb shows
Bus 001 Device 017: ID 13fe:3100 Kingston Technology Company Inc. 2 GB USB stick

dmesg

[498799.435027] usb-storage: device found at 14
[498799.435031] usb-storage: waiting for device to settle before scanning

after that there should be
device scan complete but it doesn't appear.


Does anyone have similar problems ??

---

### Post by 1script on 2010-06-21
> **marcio123 said:**
> I have the same problem on my 3 laptops (2 asus, 1 toshiba) 

1 has 64 bit 10.04
2 have 32 bit 10.04


lsusb shows
Bus 001 Device 017: ID 13fe:3100 Kingston Technology Company Inc. 2 GB USB stick

dmesg

[498799.435027] usb-storage: device found at 14
[498799.435031] usb-storage: waiting for device to settle before scanning

after that there should be
device scan complete but it doesn't appear.


Does anyone have similar problems ??

Yeap, same here.

Pretty much can't use flash memory (in a usb-connected reader) or USB flash drives ever since 10.04 upgrade. Everything was working on this PC through all the previous upgrades - 8.04->8.10->9.04

Here is my dmesg:
```
[   79.236535] sd 7:0:0:3: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[   79.236538] sd 7:0:0:3: [sde] Sense not available.
[   79.236547] sd 7:0:0:3: [sde] Assuming drive cache: write through
[   79.236549] sd 7:0:0:3: [sde] Attached SCSI removable disk
[   79.682237] usb 2-6: new high speed USB device using ehci_hcd and address 11
[   79.843000] usb 2-6: configuration #1 chosen from 1 choice
[   79.843366] scsi8 : SCSI emulation for USB Mass Storage devices
[   79.843462] usb-storage: device found at 11
[   79.843463] usb-storage: waiting for device to settle before scanning

```

lsusb:

/dev/sde is not mount-able. mount says device does not exist.
Any idea is greatly appreciated !

---

### Post by 1script on 2010-06-21
I just wanted to add to the topic by saying that the scanning actually "completes" as soon as you remove the device. Below are the dmesg outputs after inserting and removing the card. My flash card reader has four slots hence the four devices being added:

CARD INSERTED:
```
[  175.153294] usb-storage: device found at 31
[  175.153296] usb-storage: waiting for device to settle before scanning

```
CARD REMOVED:
```
[  180.150225] usb-storage: device scan complete
[  180.150828] scsi 29:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[  180.151317] scsi 29:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[  180.151818] scsi 29:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[  180.152317] scsi 29:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[  180.152652] sd 29:0:0:0: Attached scsi generic sg4 type 0
[  180.152767] sd 29:0:0:1: Attached scsi generic sg5 type 0
[  180.152877] sd 29:0:0:2: Attached scsi generic sg6 type 0
[  180.152984] sd 29:0:0:3: Attached scsi generic sg7 type 0
[  180.156071] sd 29:0:0:0: [sdb] Attached SCSI removable disk
[  180.156691] sd 29:0:0:1: [sdc] Attached SCSI removable disk
[  180.157313] sd 29:0:0:2: [sdd] Attached SCSI removable disk
[  180.157937] sd 29:0:0:3: [sde] Attached SCSI removable disk

```
So, how does one make the device settle when it does not want to?

---

### Post by Richard87 on 2010-07-05
I have the excatly same problem on Ubuntu 10.04 Desktop...

I have a Olympus u840....

---

### Post by Programmer210 on 2010-07-25
> **Richard87 said:**
> I have the excatly same problem on Ubuntu 10.04 Desktop...

I have a Olympus u840....

I'm seeing the same problem on a fully up-to-date 64 bit desktop 10.04.

For me, USB flash drives work fine and mount. What doesn't mount is my cellphone. If I use the BitPIM program to access the cellphone it works, but I can't access it as a USB filesystem, even after telling the phone to go into mass storage mode.

I'm wondering if it is this requirement of switching to mass storage mode that is causing the problem - somehow the usb subsystem is not waiting long enough for that to happen? It may be the same issue with cameras - they don't switch immediately, and so Linux times out somehow.

---

### Post by amirhomayoun on 2010-09-03
Had the same problem here:

```
usb-storage: waiting for device to settle before scanning
```

and then nothing. Believe it or not, the problem was the micro usb cable that was not **fully** plugged in the external hard drive. Once I fixed it everything worked.

Hope your's is a simple problem as mine!

---

### Post by 1script on 2010-09-14
In my case the problem actually went away after upgrading to 10.04 . The device now mounts fine however only root has full access to it. Additionally, when you remove the device, its status in Nautilus never changes, just hangs in there until you reboot. Just a minor annoyance though.

Now, if I can only figure out the way to auto-mount the USB storage devices for write/read access by regular users ...

---

### Post by naaman on 2012-11-18
> **amirhomayoun said:**
> Had the same problem here:

```
usb-storage: waiting for device to settle before scanning
```

and then nothing. Believe it or not, the problem was the micro usb cable that was not **fully** plugged in the external hard drive. Once I fixed it everything worked.

Hope your's is a simple problem as mine!

:KS Yes, I had a similar issue with my external HDD caddy:
[LIST]
[*]the switch was set to ESATA (by accident) and not USB.
[/LIST]  

Good old [Layer 1]("http://en.wikipedia.org/wiki/OSI_model") problem..

---

### Post by wildmanne39 on 2012-11-18
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

