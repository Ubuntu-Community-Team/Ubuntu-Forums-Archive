---
title: "USB Devices not being detected"
date: 2010-11-07
forum: Hardware
---

### Post by dudestir on 2010-11-07
Hi All

We recently undated my son's machine to 10.10 and yesterday he tells me no USB devices are being detected. I don't believe it's hardware and he's a 16 year old boy so anything could have been changed.

lsusb returns

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

whether a device is plugged in or not, front ports or back.

Any ideas on where I should start looking would be greatly appreciated.

Dean

---

### Post by sikander3786 on 2010-11-07
Which machine is it specifically? Desktop or laptop?

I hope you have checked the USB thumb drive with another system and it works there.

Can you check with some USB mouse or keyboard if they are working on your USB ports or it might be a hardware fault.

lsusb doesn't list anything except the root hub as you see.

---

### Post by dino99 on 2010-11-07
from synaptic, check that usbmount & usbutils are installed

sudo update-usbids && sudo update-pciids

---

### Post by karthick87 on 2010-11-07
what is the ouput of dmesg?

Type dmesg in terminal and post your results here.

---

### Post by dudestir on 2010-11-07
Hi All

It's a desktop computer.

When I stick a thumbdrive in it lights up but is not detected.

I've reinstalled usbmount & usbutils and ran

sudo update-usbids && sudo update-pciids

the usbids did install

dmesg doesn't change from before the thumbdrive is inserted to after.  In both cases I have the same

dmesg | grep usb
[    0.233337] usbcore: registered new interface driver usbfs
[    0.233350] usbcore: registered new interface driver hub
[    0.233369] usbcore: registered new device driver usb

Dean

---

