---
title: "USB 3.0 doesn't work on USB 3.0 port"
date: 2016-03-08
forum: Hardware
---

### Post by galapogos on 2016-03-08
Hi,

I have Ubuntu 14.04.4 LTS installed on a system with an intel H77 chipset with USB 3.0 support. I tried connecting a USB 3.0 hard drive to the USB 3.0 port, and it does not get detected by fdisk. Connecting it to a USB 2.0 port works though. The USB 3.0 port is working as it detects other USB 2.0 drives and smartphones.

What's up? Do I need to install some driver?

Thanks.

---

### Post by Yellow Pasque on 2016-03-08
What's lsusb say?
```
sudo update-usbids
lsusb
```

---

### Post by gordintoronto on 2016-03-08
I experienced exactly the same thing, but it works nicely with 15.10.

---

### Post by galapogos on 2016-03-11
> **Temüjin said:**
> What's lsusb say?
```
sudo update-usbids
lsusb
```

lsusb detects the device when connected to either the USB 2.0 or USB 3.0 port, i.e. it shows the device USB PID/VID.

---

### Post by Neill_R on 2016-03-22
Hi gord in toronto 

 Thought you might have had a solution for me but I find what you say is (for me) untrue. I have a dell Optiplex 360 and it does not support USB 3 but I have a USB 3.0 PCI express card which is recognised. With Lubuntu 15:10 run as a try me liveCD I see the USB flash on and then off again.


lubuntu@lubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 002: ID 047d:2043 Kensington 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub

**Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub**

Bus 001 Device 003: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lubuntu@lubuntu:~$

---

### Post by Neill_R on 2016-03-22
when will USB 3 work for Lubuntu Ubuntu?

---

### Post by gordintoronto on 2016-03-22
When you say "flash on and then off again," do you mean that is what happens when you plug in a USB 3 flash drive? Was your lsusb output produced with a USB 3 flash drive plugged in?

I don't think the desktop environment determines USB 3 support. Your Lubuntu 15.10 is probably using the same kernel as my Xubuntu, and I think that is the main factor. However, your 7-year-old computer might also be a factor.

---

### Post by Neill_R on 2016-03-24
other than 

[B]Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

and the light on the USB stick flashing on momentarily There is noo sign of live. Yet the USB will work in USB 2 port on this machine or others.
Can't do anything about the PC being old 
[/B]

---

### Post by mörgæs on 2016-03-26
How does it work for 16.04?

---

