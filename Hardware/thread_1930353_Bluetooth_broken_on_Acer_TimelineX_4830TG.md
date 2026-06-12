---
title: "Bluetooth broken on Acer TimelineX 4830TG"
date: 2012-02-23
forum: Hardware
---

### Post by iuiz on 2012-02-23
Hi,

I have a Acer TimelineX 4830TG laptop and just installed Ubuntu 11.10 Oneiric. However the Bluetooth adapter is not working, even though the Bluetooth icon is displayed and it says that Bluetooth is activated. I cannot discover any devices and checked with another device that they could be discovered.

Here are my Bluetooth informations (if you need more informations please say so).
tim@ubuntu:~$ sudo dmesg | grep -i blue
[   24.026112] Bluetooth: Core ver 2.16
[   24.026221] Bluetooth: HCI device and connection manager initialized
[   24.026223] Bluetooth: HCI socket layer initialized
[   24.026225] Bluetooth: L2CAP socket layer initialized
[   24.028798] Bluetooth: SCO socket layer initialized
[   24.042974] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   26.305464] Bluetooth: RFCOMM TTY layer initialized
[   26.305473] Bluetooth: RFCOMM socket layer initialized
[   26.305475] Bluetooth: RFCOMM ver 1.11
[   26.307990] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.307993] Bluetooth: BNEP filters: protocol multicast
[  558.935244] Bluetooth: HIDP (Human Interface Emulation) ver 1.2


tim@ubuntu:~$ lspci | grep -i blue
Returns no result.

tim@ubuntu:~$ lsusb | grep -i blue
Returns no result.

The Bluetooth adapter is working under Windows.

Thanks for your help.

---

### Post by ahallubuntu on 2012-02-23
You need to figure out the exact bluetooth card you have first.

Try lsusb (and lspci) again and look for output with Broadcom or Atheros in it, try to figure out if one if them is your bluetooth card even though it doesn't say "bluetooth."

Or boot into Windows and figure out the bluetooth hardware information from that.

Then you can search for Linux support for that specific bluetooth device, not just the Acer model.

---

### Post by iuiz on 2012-02-24
Thx for your help.

I could identify this with "lsusb":
Bus 001 Device 004: ID 0489:e03c Foxconn / Hon Hai

(It is only shown after I pressed "fn + f3" until the Bluetooth icon appears.)

There is currently this bug describing my problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898826](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/898826)

Now I play the waiting game :(.

---

### Post by irielion on 2012-04-20
I am experiencing the same issue. I wrote the linux wireless mailing list ([http://www.spinics.net/lists/linux-wireless/msg88664.html](http://www.spinics.net/lists/linux-wireless/msg88664.html)) and reported a bug at kernel.org ([https://bugzilla.kernel.org/show_bug.cgi?id=43134](https://bugzilla.kernel.org/show_bug.cgi?id=43134))

---

