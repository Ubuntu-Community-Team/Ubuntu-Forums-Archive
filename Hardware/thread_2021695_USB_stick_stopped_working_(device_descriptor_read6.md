---
title: "USB stick stopped working (device descriptor read/64, error -71)"
date: 2012-07-09
forum: Hardware
---

### Post by areUKEidding on 2012-07-09
Since today my 16 GB transcend USB stick stopped working. It does not work on any computer (Windows PC, Mac and my laptop with ubuntu) I tried so far without any obvious reason. Basically I have lost hope and I guess it is just broken, but maybe somebody has an idea.

This is what dmesg shows when I connect the usb stick:
> 
[16470.292064] usb 2-1: new full-speed USB device number 26 using uhci_hcd
[16470.416083] usb 2-1: device descriptor read/64, error -71
[16470.644081] usb 2-1: device descriptor read/64, error -71
[16470.860105] usb 2-1: new full-speed USB device number 27 using uhci_hcd
[16470.988107] usb 2-1: device descriptor read/64, error -71
[16471.216084] usb 2-1: device descriptor read/64, error -71
[16471.432070] usb 2-1: new full-speed USB device number 28 using uhci_hcd
[16471.848072] usb 2-1: device not accepting address 28, error -71
[16471.960100] usb 2-1: new full-speed USB device number 29 using uhci_hcd
[16472.376081] usb 2-1: device not accepting address 29, error -71
[16472.376129] hub 2-0:1.0: unable to enumerate USB device on port 1
I have found some threads about this error -71, but they all were about harddrives and usb sticks only not working in linux but working fine in windows, which mine doesn't. I cannot see the stick in the disk utility either and in some other thread someone recommended the device storage manager, but that did not detect anything as well.

So what do you think? Is it broken or can it be fixed? It is unfortunately slightly over a year old, so I don't think I can have it replaced. Lucky for me that there is nothing on it that I desperately need, so if I have to erase everything to get it working again, that would be fine.

---

### Post by eneskuray on 2012-07-09
how aften do you format your disk ? and did you reduce your usb stick ?

---

### Post by areUKEidding on 2012-07-09
As far as I remember I only formatted it once, been a while ago right after I bought it. FAT file system so I can use it with any computer. No partitions, unless there is some hidden ones like on some of these SanDisk sticks, don't know if Transcend does that as well.

---

### Post by eneskuray on 2012-07-09
is there any light  on stick ?

---

### Post by areUKEidding on 2012-07-10
Yes the stick has a little blue light and when plugged in it is on constantly.

---

### Post by eneskuray on 2012-07-16
i have been looking for solition but there isnt anything . you should send it customer service

---

### Post by areUKEidding on 2012-07-20
Thanks for your efforts, I actually did that already a couple of days ago, but forgot to mention it here.
The manufacturer (transcend) has something like lifetime warranty so they were fine with replacing it. But I probably won't save any valuable data on it anymore...

---

