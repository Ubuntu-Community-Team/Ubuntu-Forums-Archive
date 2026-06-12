---
title: "USB HDD, unable to enumerate USB device. 10.04"
date: 2010-11-08
forum: Hardware
---

### Post by Little Blue on 2010-11-08
Hi,

I just tried to fire up an externally powered 500GB USB hardrive but it doesn't seem to want to connect. Looking at dmesg I get

```
[ 1025.017052] usb 2-1.3: new low speed USB device using ehci_hcd and address 18
[ 1025.088891] usb 2-1.3: device descriptor read/64, error -32
[ 1025.264407] usb 2-1.3: device descriptor read/64, error -32
[ 1025.439870] usb 2-1.3: new low speed USB device using ehci_hcd and address 19
[ 1025.511760] usb 2-1.3: device descriptor read/64, error -32
[ 1025.687285] usb 2-1.3: device descriptor read/64, error -32
[ 1025.862843] usb 2-1.3: new low speed USB device using ehci_hcd and address 20
[ 1026.269544] usb 2-1.3: device not accepting address 20, error -32
[ 1026.341593] usb 2-1.3: new low speed USB device using ehci_hcd and address 21
[ 1026.752282] usb 2-1.3: device not accepting address 21, error -32
[ 1026.752524] hub 2-1:1.0: unable to enumerate USB device on port 3

```

And lsusb gives

```
Bus 002 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 003: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0182 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I've had a look around for similar topics but I can't seem to find any solutions that work for me. Even things like 'sudo modprobe usb_storage' (something I found in [http://ubuntuforums.org/showthread.php?t=1471736](http://ubuntuforums.org/showthread.php?t=1471736)), do nothing... I don't really know why its not working as I've not mistreated the disk or anything, so I am kind of concerned...

Any help would be really appreciated.

Cheers.

---

### Post by Little Blue on 2010-11-08
Ok, never mind... I tried changing the port on my machine, tried different OS's, and no luck. Then I stumbled upon an unused USB cable and decided to try it out (I didn't realise I had any spare before), and it works!

Trying the original cable on an old usb drive I've had lying around and that didn't work, so I'm going to guess my cable's a write off. It works enough to detect that there's a device attached but doesn't really connect...

I wonder what can damage an unused cable so much in only month or so to prevent it working?

Oh well, nevermind!

---

### Post by dabl on 2010-11-08
> **Little Blue said:**
> 

I wonder what can damage an unused cable so much in only month or so to prevent it working?



A ****-poor QA process at the manufacturer?   :guitar:

---

