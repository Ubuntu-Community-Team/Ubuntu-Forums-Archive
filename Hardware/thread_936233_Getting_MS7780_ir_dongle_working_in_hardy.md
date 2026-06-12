---
title: "Getting MS7780 ir dongle working in hardy?"
date: 2008-10-02
forum: Hardware
---

### Post by mma8x on 2008-10-02
i just purchased a new ir usb dongle, and am having trouble getting it working--it doesn't appear that a device node is created for whatever reason.
dmesg:

```
[ 5322.117963] usbcore: registered new interface driver mcs7780
[ 6036.538920] usb 1-1: USB disconnect, address 3
[ 6036.563160] MCS7780 now disconnected.
[ 6321.071516] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 6321.188894] usb 1-1: configuration #1 chosen from 1 choice

```
lsusb:
```
Bus 001 Device 004: ID 9710:7780 MosChip Semiconductor MS7780 4Mbps Fast IRDA Adapter

```
iwconfig:
```
irda0     no wireless extensions.

```
lsmod|grep ir
```
irda                  222956  1 mcs7780
crc_ccitt               3584  2 mcs7780,irda

```
all the ir info i can find is ancient or regarding lirc.  there was talk about having to compile the mcs7780 driver on earlier releases, but this was supposedly fixed in gutsy, and it appears that there is a module loaded.  so where's my device, and how can i use it?

---

### Post by Thorney on 2008-11-20
Did you get this going? I have the same problem.

---

### Post by freakalad on 2009-04-18
Having similar issue & located the following info:
driver: [http://cateee.net/lkddb/web-lkddb/MCS_FIR.html](http://cateee.net/lkddb/web-lkddb/MCS_FIR.html)
debian db: [http://wiki.debian.org/DeviceDatabase/USB](http://wiki.debian.org/DeviceDatabase/USB)

referred to as MS7780 or MSC7780

if someone could please help with getting the driver loaded, that would help a bunch (not quite my forte)

---

### Post by freakalad on 2009-08-05
found the following resource (unfortunately in italian, so you may need to run it through google's translator):
[http://forum.ubuntu-it.org/index.php?topic=182671.msg2035286](http://forum.ubuntu-it.org/index.php?topic=182671.msg2035286)

the author seems to indicate that it's all good, but I've yet to get it going OK

---

### Post by ray420 on 2011-05-31
google translates the commands and messes them up you have to enter them as they are originaly  posted

---

