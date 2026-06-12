---
title: "Motorola Razr V3a with Bitpim"
date: 2009-03-31
forum: Hardware
---

### Post by talon314 on 2009-03-31
I could not find any direct documentation on using a V3a with Bitpim in Ubuntu, so this is how I got it working:

SilentDissonance's excellent post here- [http://ubuntuforums.org/showthread.php?t=556191](http://ubuntuforums.org/showthread.php?t=556191) explains in depth the method for getting a /dev device assigned to your phone. Read step 1 of his directions for a detailed explanation. The short version:

WITHOUT PHONE CONNECTED-

```
~$ cat /proc/bus/usb/devices > devices
```

WITH PHONE CONNECTED-

```
~$ diff /proc/bus/usb/devices devices | grep Vendor
```

Should give output similar to

```
~$ diff /proc/bus/usb/devices devices | grep Vendor
< P:  Vendor=22b8 ProdID=2ac4 Rev= 0.01
```

Fill this information in the following command:
```
~$ sudo modprobe usbserial vendor=0x22b8 product=0x2ac4
```

Then check dmesg for the device-

[CODE]~$ dmesg | tail
[33058.073215] usb 5-2: new full speed USB device using uhci_hcd and address 11
[33058.309091] usb 5-2: configuration #1 chosen from 1 choice
[33058.311589] usbserial_generic 5-2:1.0: generic converter detected
[33058.311837] usb 5-2: generic converter now attached to ttyUSB2
[33058.315584] usbserial_generic 5-2:1.1: generic converter detected
[33058.315758] usb 5-2: generic converter now attached to ttyUSB3[\CODE]

Now, launch Bitpim as root. Open the settings, change the phone type to V3cm (others may work, I haven't tested). Beside com port, click browse and select the device that matches the dmesg output from earlier (you may need to refresh). Click OK for both open dialogs and click the information icon at the top. If it returns your phone information, then Bitpim is working.

Bitpim's support for V3a's is very limited at present; some things work, but others will require you to reconnect your phone (selecting a different com port; use dmesg). You will have to run the modprobe command at reboot, which you may add as a startup script (or perhaps you may add it to /etc/modules.conf? not tested). Use at your own risk.

---

