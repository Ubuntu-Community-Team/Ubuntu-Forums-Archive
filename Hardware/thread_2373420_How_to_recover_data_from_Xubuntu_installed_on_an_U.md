---
title: "How to recover data from Xubuntu installed on an USB that will not boot anymore?"
date: 2017-10-06
forum: Hardware
---

### Post by konrad-kaas on 2017-10-06
Hi, I am relatively new to Ubuntu, used it "lightly" for a few years. I had installed Xubuntu on an USB, which now (after some 2 years) does not boot anymore.
I installed the latest Xubuntu on another USB now, yet the old USB cannot be mounted, and seems not to be recognized by Testdisk.
I would just want to access it to save / copy some of the data still on it, after that I could format it.
Thanks in advance for your assistance!

---

### Post by Bucky Ball on 2017-10-06
Welcome. If testdisk doesn't recognise, does anything else? Does Gparted recognise it? If not, how will you format it? 

Plug it in, run this:

```
sudo blkid
```

Do it and its partitions show up anywhere in the output (probably towards the bottom)?

USB are not exactly reliable, they die unexpectedly, and regular backups should be kept if you are intending to run a persistence install from USB. Bit late for that advice. Future reference. :)

---

### Post by konrad-kaas on 2017-10-06
Thanks and sorry for the late reply! I run the code and it does not list the USB / its partitions. Gparted also does not see it.
When I insert it, it appears briefly on desktop, as it tries to automount. But when this fails it disappears from the desktop as well.
Anything else I can try? :-/

---

### Post by efflandt on 2017-10-06
When you connect it, see what shows up in dmesg about it (open a terminal window with Ctrl+Alt+T, type **dmesg**, and Enter key). If there is more about it than shows on the screen, you can scroll back with mousewheel or Shift+PgUp.

---

### Post by konrad-kaas on 2017-10-07
Thanks! I tried, but indeed the output is very long! I believe the significant part of it is this:

[  209.545160]  sdc: sdc1 sdc2
[  209.546425] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[  247.770549] xhci_hcd 0000:00:14.0: WARN: unexpected TRB Type 4
[  247.770604] usb 3-1: Disable of device-initiated U1 failed.
[  252.890220] xhci_hcd 0000:00:14.0: WARN: unexpected TRB Type 4
[  252.890251] usb 3-1: Disable of device-initiated U2 failed.
[  258.265936] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[  263.641673] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[  263.849618] usb 3-1: device not accepting address 3, error -62
[  264.061122] usb 3-1: Device not responding to setup address.
[  264.269156] usb 3-1: Device not responding to setup address.
[  264.473604] usb 3-1: device not accepting address 3, error -71
[  264.685130] usb 3-1: Device not responding to setup address.
[  264.893171] usb 3-1: Device not responding to setup address.
[  265.097522] usb 3-1: device not accepting address 3, error -71
[  265.309082] usb 3-1: Device not responding to setup address.
[  265.517105] usb 3-1: Device not responding to setup address.
[  265.721533] usb 3-1: device not accepting address 3, error -71
[  265.777714] usb 3-1: USB disconnect, device number 3
[  265.778131] sdc: detected capacity change from 30752000000 to 0
[  266.040938] usb 3-1: Device not responding to setup address.
[  266.249241] usb 3-1: Device not responding to setup address.
[  266.453684] usb 3-1: device not accepting address 4, error -71
[  266.664924] usb 3-1: Device not responding to setup address.
[  266.872963] usb 3-1: Device not responding to setup address.
[  267.077545] usb 3-1: device not accepting address 5, error -71
[  267.288976] usb 3-1: Device not responding to setup address.
[  267.496972] usb 3-1: Device not responding to setup address.
[  267.701507] usb 3-1: device not accepting address 6, error -71
[  267.912877] usb 3-1: Device not responding to setup address.
[  268.120962] usb 3-1: Device not responding to setup address.
[  268.325404] usb 3-1: device not accepting address 7, error -71
[  268.353523] usb usb3-port1: unable to enumerate USB device
[  268.353568] xhci_hcd 0000:00:14.0: Stop endpoint command completion for disabled slot 10

Does this make sense to you? :-)
Thanks!

---

### Post by C.S.Cameron on 2017-10-07
What type of install do you have on the flash drive? Persistent install or Full install?
If persistent install with casper-rw file you may be able to mount the persistence file:

```
sudo mkdir /media/casper

sudo mount -o loop casper-rw /media/casper/
```


Or you may be able to mount the file using Disks.

---

### Post by konrad-kaas on 2017-10-07
Hi! I have a full install...

---

### Post by efflandt on 2017-10-08
Although, it initially sees 2 partitions on it, it is not connecting properly and at some point thinks that size has gone to zero. Until you can solve that, I doubt you will get any data from it. Have you tried it with a different cable, or if connecting to a laptop, with its power supply connected just in case it is not getting quite enough power? Some drives include a cable with 2 USB plugs to assure enough power if connected to USB 2.0 ports that only supply the minimum 500 mA instead of more.

---

### Post by konrad-kaas on 2017-10-09
Thanks, I tried yet no success... I have only USB 3 ports, and the stick itself is also USB 3. Not sure from your message if I should somehow try to mount it on an USB 2 port...

---

