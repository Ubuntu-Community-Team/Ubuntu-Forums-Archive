---
title: "Canon Pixma iP4200 Bad-URI"
date: 2009-08-07
forum: Hardware
---

### Post by c-2501 on 2009-08-07
I've been trying all day to install my Canon iP4200 printer using the guide i found here:

[http://ubuntuforums.org/showthread.php?t=204853](http://ubuntuforums.org/showthread.php?t=204853)

I can get as far as trying to add the printer using the CUPS web interface.  I go through all the steps, giving the printer a name, location etc. but when it comes to actually selecting the printer driver I am presented with the following error from cups:

```
Bad device-uri "cnij_usb:/dev/usb/lp0"!
```

Now as far as I can tell the system is correctly detecting and creating devices for the printer:

```
dmesg | tail
[ 2325.052529] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 2325.186692] usb 1-1: configuration #1 chosen from 1 choice
[ 2325.188063] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10A2

```

```
lsusb
Bus 001 Device 005: ID 04a9:10a2 Canon, Inc. iP4200

```

```
ls -la /dev/usb/
crw-rw----+  1 root lp   180,  0 2009-08-07 15:13 lp0

```

I'm really not sure what the problem is here.  Can someone shed light on the situation?

Thanks,

**Edit:** Ok think i've made some progress on this issue, when i chown the device lp0 to lp:lp i can now successfully select it from the devices list.  the problem is when the device is created each time the permissions are root:lp  how do i give cups access to this, or make the device create each time with lp:lp permissions?

---

