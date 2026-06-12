---
title: "Extremely slow speed on USB transfer"
date: 2010-02-23
forum: Hardware
---

### Post by tribaldata on 2010-02-23
Hi, 

I recently got a external HDD from LaCie (1TB) and i'm experiencing some excruciating slow speed while transferring files from my server to the External HDD which is plugged in the rear USB port.

So let's say I'm transferring a 1.3Gb file, the transfer rate start around 6.50 MB/s then dramatically drop to 1.05MB/s.:confused:

The transfer of 1.3Gb take around 9 to 11 minutes.](*,)

How can i know if I'm running the proper driver for USB2.0 and not only the 1.0.

Here is the output of lsmod | grep usb 

```
root@monkeyrule:~# lsmod | grep usb
usb_storage            52576  1

```

and here is dmesg | grep usb

```
root@monkeyrule:~# dmesg | grep usb
[    0.219232] usbcore: registered new interface driver usbfs
[    0.219284] usbcore: registered new interface driver hub
[    0.219345] usbcore: registered new device driver usb
[    1.071546] usb usb1: configuration #1 chosen from 1 choice
[    1.072633] usb usb2: configuration #1 chosen from 1 choice
[    1.381624] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    1.581569] usb 1-2: configuration #1 chosen from 1 choice
[    2.222862] usbcore: registered new interface driver usb-storage
[    2.255322] usb-storage: device found at 2
[    2.255330] usb-storage: waiting for device to settle before scanning
[    7.253640] usb-storage: device scan complete
[185672.560096] usb 1-2: USB disconnect, address 2
[2898362.612067] usb 1-1: new full speed USB device using uhci_hcd and address 3
[2898362.787239] usb 1-1: configuration #1 chosen from 1 choice
[2898362.796550] usb-storage: device found at 3
[2898362.796555] usb-storage: waiting for device to settle before scanning
[2898367.816344] usb-storage: device scan complete

```

Anyone have an idea? It will be more then welcome :D

---

### Post by mörgæs on 2010-02-24
Does this describe your problem?
[https://bugs.launchpad.net/ubuntu/+bug/197762?comments=all](https://bugs.launchpad.net/ubuntu/+bug/197762?comments=all)

In that case, you can be assured that there is attention on it. I don't know of a fix, sorry.

---

### Post by tribaldata on 2010-02-25
Yes it does look like my issue...

Ohh well thanks for the info, i'll submit my result to them so they have more to work with.


Thanks =)

---

### Post by Dangger on 2010-05-18
Having the same issue. This is hardly solved.

---

### Post by syborfical on 2010-12-03
This has not been solved... please remove the solved tag from Thread or post a working solution.

11mbps off a usb2 drive is NOT SOLVED. 

This has been an issue with ubuntu since 9.04

---

### Post by syborfical on 2011-03-23
> **syborfical said:**
> This has not been solved... please remove the solved tag from Thread or post a working solution.

11mbps off a usb2 drive is NOT SOLVED. 

This has been an issue with ubuntu since 9.04

After doing some testing my issue is related to slow transfer from ext to NTFS.

I formatted my external to ext2 and get around 40mb.

---

