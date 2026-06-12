---
title: "Persistent USB boot Anomalies"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by slikwill on 2009-09-29
I have successfully built 9.04 persistent USB boot on a 2 gb SD card using directions at the pendrive website.

There are two operational anomalies that are present:

1.  If I have an additional USB drive or an internal data partition mounted and I shut down without manually unmounting them, the system will not unmount it and on reboot it cannot be mounted in the new boot.  This means that access to this device is permanently lost.  A complete rebuild of the USB boot must be done to access that device again.

2.  A secure wireless network connection needs a keyring password entered to establish a connection at boot time.  If I remember correctly, this was true in ubuntu 7.04 (or 7.10), but has definitely not been required for automatic connect under ubuntu 8.04.

These anomalies also exist in the Linux Mint 7 Persistent USB boot.

Other than this, it seems to be fully functional for my needs.

---

### Post by Mighty_Joe on 2009-09-30
> **slikwill said:**
> 
1.  If I have an additional USB drive or an internal data partition mounted and I shut down without manually unmounting them, the system will not unmount it and on reboot it cannot be mounted in the new boot.  This means that access to this device is permanently lost.  A complete rebuild of the USB boot must be done to access that device again.


Is Grub set up to use the the device/partition number?  Like this:
```
root   (hd0,0)

```
The boot order of plug-in devices can obviously change.  The [Live USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator") on the Live CD uses the devices UUID for this reason.  
If you are using a casper-rw partition to save your changes, there is a [known problem]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702") where those partitions are not unmounted cleanly.

---

### Post by slikwill on 2009-09-30
Thanks.  That's good to know.

---

