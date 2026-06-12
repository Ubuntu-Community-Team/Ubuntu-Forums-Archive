---
title: "USB flash drive not detected"
date: 2008-06-08
forum: Hardware
---

### Post by Rhapsody on 2008-06-08
I have recently purchased an 8GB USB flash drive with the intention of transferring data from one PC (with Kubuntu 7.10 and no internet connection) to another (with Kubuntu 8.04 and an internet connection). Unfortunately, neither PC seems to detect it.

The box for the flash drive says it should work with Linux 2.4 and above, but lsusb on the Kubuntu 8.04 PC doesn't list the flash drive at all:

Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 003: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I don't mind having to mount this thing manually, but why can't the system even see it?

---

### Post by seren6ipity on 2008-11-24
Hi,
I'd the same issue with Ubuntu as well as now Xubuntu. Please check if you have usbmount installed [credit ROE : [http://ubuntuforums.org/showthread.php?t=120492]](http://ubuntuforums.org/showthread.php?t=120492]) Installing it worked like a treat for me.

**Workaround:**

You can try following commands. 

Using following command should help OS recognize your USB - 
sudo rmmod ehci_hcd  ---> This will change USB 2.0 to USB 1.0

Begin transfer. When done use following command - 
sudo modprobe ehci-hcd ---> This will revert the above change

Both of these commands should be used in conjunction. This change makes the transfer extremely slow.

---

