---
title: "Mounting USB Camera problem"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by self-defence on 2007-10-26
Hi,

I've just installed Ubuntu 7.10 and set everything up then tried to connect ma camera(Nikon D40x) in order to copy a few images of it. And when I turned it on nothing happened so I tried to connect another camera and it mounted and also tried a USB storage and it also mounted. The strange thing is that this used to work in 7.04 and the camera is set to Mass Storage connection(works fine on another Ubuntu 7.04 machine), but now works only if I connect it via PTP mode.
Anyone have a clue what could be the problem?

Thanks for all the help and best regards.

My /var/log/messages file output:
```

Oct 26 00:11:55 localhost kernel: [ 8695.116000] usb 3-1: new high speed USB device using ehci_hcd and address 9
Oct 26 00:11:55 localhost kernel: [ 8695.248000] usb 3-1: configuration #1 chosen from 1 choice
Oct 26 00:11:55 localhost kernel: [ 8695.248000] scsi8 : SCSI emulation for USB Mass Storage devices
Oct 26 00:12:00 localhost kernel: [ 8700.248000] scsi 8:0:0:0: Direct-Access     NIKON    D40X             1.00 PQ: 0 ANSI: 2
Oct 26 00:12:00 localhost kernel: [ 8700.248000] sd 8:0:0:0: [sdb] 3970049 512-byte hardware sectors (2033 MB)
Oct 26 00:12:00 localhost kernel: [ 8700.248000] sd 8:0:0:0: [sdb] Write Protect is off
Oct 26 00:12:00 localhost kernel: [ 8700.252000] sd 8:0:0:0: [sdb] 3970049 512-byte hardware sectors (2033 MB)
Oct 26 00:12:00 localhost kernel: [ 8700.252000] sd 8:0:0:0: [sdb] Write Protect is off
Oct 26 00:12:00 localhost kernel: [ 8700.252000]  sdb: sdb1
Oct 26 00:12:00 localhost kernel: [ 8700.256000] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Oct 26 00:12:00 localhost kernel: [ 8700.256000] sd 8:0:0:0: Attached scsi generic sg2 type 0
Oct 26 00:12:00 localhost kernel: [ 8700.376000] end_request: I/O error, dev sdb, sector 3970048
Oct 26 00:12:00 localhost kernel: [ 8700.376000] printk: 613 messages suppressed.
Oct 26 00:12:00 localhost kernel: [ 8700.376000] end_request: I/O error, dev sdb, sector 3970048
Oct 26 00:12:00 localhost kernel: [ 8700.380000] end_request: I/O error, dev sdb, sector 3970048
Oct 26 00:12:00 localhost kernel: [ 8700.384000] end_request: I/O error, dev sdb, sector 3970048
Oct 26 00:12:00 localhost kernel: [ 8700.600000] end_request: I/O error, dev sdb, sector 1
Oct 26 00:12:00 localhost kernel: [ 8700.604000] end_request: I/O error, dev sdb, sector 0
Oct 26 00:12:00 localhost kernel: [ 8700.604000] end_request: I/O error, dev sdb, sector 1
Oct 26 00:12:22 localhost kernel: [ 8722.588000] usb 3-1: USB disconnect, address 9
```

---

### Post by Boone on 2007-10-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/145153](https://bugs.launchpad.net/ubuntu/+bug/145153) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Same thing here. D40x doesn't work in Gutsy. So I tried it in Dapper and Feisty, where it worked fine.  Any ideas?

Daniel

PS: Similar bug is filed in Launchpad for Nikon D40. The Workaround (change setting to PTP in camera) works for importing in gphoto but is not really an alternative because of the missing mass storage device.

---

### Post by self-defence on 2007-10-27
Yes it seems to be the same bug. :( This is really unfortunate because it used to work on previous versions. Hope someone finds a fix soon. :)

Best regards

---

### Post by self-defence on 2007-10-28
Would it help if I used an older kernel version?

Best regards to all

---

### Post by self-defence on 2007-11-03
Well apparently I have to patch the kernel with this [patch]("http://launchpadlibrarian.net/9678067/unusual_devs.patch").
Witch I've tried to do for kernel 2.6.23 but it still doesn't work or I'm compiling the kernel wrong.

Anyone had any luck with this?

Bye

---

### Post by pakux on 2007-11-07
I had kind of a similar issue: when I first connected my D40x to my laptop it didn't work, Later on googling around I found about the PTP mode and it worked;  as soon as the camera is plugged and turned on a dialog comes up and I'm able to download the pictures.... at least (gThumb). And there is always the possibility to take the card off the camera and insert it directly in the laptop card reader, as a turnaround.

Looking at the bug reports it seems like some folks had the issue solved after the firmware update (D40) and/or using new kernels. I gave mine a try and still nothing if swtiched to mass storage mode.

---

### Post by self-defence on 2007-11-08
Is there a firmware update for the D40x? I've been looking for it but haven't found anything. 
The PTP also works and if it is the only way that works then that's the way I'll need to do it. Unfortunately my laptop doesn't have a card reader but I know it works if I plug the SD card into the USB card reader. 
Well I hope that sooner or later it will work. :)

Thanks for the input.

---

### Post by self-defence on 2007-11-15
Well problem temporarily fixed with a 5 € card reader. :)
Unfortunately it means that I have to carry around another peace of equipment but it's a small, light one.

Bye

---

### Post by cturnbull802 on 2007-12-29
it does not work for mine either for my laptop running ubuntu 7.10, i am using a card reader built into my printer via a windows share to gain access.... what a pita!

---

### Post by cturnbull802 on 2007-12-29
.

---

### Post by self-defence on 2007-12-29
Well I just got my self a usb multi card reader and I hook it up when I need to download images. But I still haven't figured out why only SD cards formated in my Nikon take a really long, long time to mount or they sometimes just don't mount at all.
Have you experienced anything similar to this?

Bye

---

### Post by cturnbull802 on 2008-01-09
i dont know, i havent ever mounted it via ubuntu, only on my windows box via my printer. and it is fast. i think its the last straw for me, maybe in another couple releases i will try ubuntu again, but its back to xp for me :(

in xp everything just works.

---

### Post by self-defence on 2008-01-10
Well on Windows and MacOS X it seems to work fine for me to... But as I said the problem with the card reader is that form my D40x card (by the way if the card is not formated in the camera it doesn't work even thou it is fat32) it takes longer to mount than some other cards form other cameras. Or sometimes it doesn't mount at all only after a reboot.

Well it works 1/2 of the time so I can work with it. :)

Bye

---

### Post by millguy on 2008-02-13
I found this thread through google and would like to note that in 7.1 switching the camera to PTP mode got it working on my laptop. In the camera's menu system choose:

setup menu -> USB -> MTP/PTP

Hope that works for everyone. I know someone else mentioned it but I'm guessing not everyone is trying it based on these responses.

---

### Post by self-defence on 2008-02-14
Yep that was the first thing I noticed that on PTP mode it seemed to work but not on MTP. I fixed it with a workaround so that I connected a card reader via USB but it still fails to mount sometimes and I always need to lug around more gear.

Thanks for contributing anyway.

---

### Post by Neobuntu on 2008-03-10
What's going on? Printer transfer mode works. A good reader works. The camera should work just as it does in Windows (XP). 

My camera is SDHC compatible and I planned to use it as mass storage. Why would it works with old Kubuntu and not the latest?

The printer transfer mode does not let me access movies or delete any accessed files on camera (internal memory or SD).

---

### Post by PaulGrahamRaven on 2008-04-04
Thanks for the tips, folks - images seem to transfer fine from my vanilla D40 in PTP mode, and the dialogue box is much more intuitive than the XP version. w00t!

---

### Post by Eemeez on 2008-06-11
Got it also working in two ways:

1) PTP -> seems quite slow ..
2) multicard reader

---

### Post by Marouf on 2008-07-09
I just had this same problem, quick fix was to change my camera from USB mode from  Auto to Mass Storage mode. 

Worked like a charm within 2 seconds. 

Ubuntu 8.04.1
Camera is a Sony Cybershot 7.2 MP

---

### Post by pannerrammer on 2008-07-18
> **millguy said:**
> I found this thread through google and would like to note that in 7.1 switching the camera to PTP mode got it working on my laptop. In the camera's menu system choose:

setup menu -> USB -> MTP/PTP

Hope that works for everyone. I know someone else mentioned it but I'm guessing not everyone is trying it based on these responses.

I'm using Hardy 64-bit and have Nikon D40. Changing to MTP/PTP as described by millguy above worked for me (with f-spot). Thanks.

---

