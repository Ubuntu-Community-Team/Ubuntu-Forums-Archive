---
title: "Unplugged USB flash mem without unmounting"
date: 2008-07-21
forum: General Help
---

### Post by FIONEX on 2008-07-21
Hi,

my USB drive no longer works because I unplugged it too many times without unmounting.  Or that's what I think anyways.
basically, i get the following messages in the logs when I plug it in:
```

Jul 21 20:44:25 fionex-d kernel: [ 2026.327393] usb 8-1: new high speed USB device using ehci_hcd and address 120
Jul 21 20:44:27 fionex-d kernel: [ 2027.752547] usb 8-1: new high speed USB device using ehci_hcd and address 127
Jul 21 20:44:27 fionex-d kernel: [ 2028.239556] usb 8-1: new high speed USB device using ehci_hcd and address 3
Jul 21 20:44:28 fionex-d kernel: [ 2029.101827] usb 8-1: new high speed USB device using ehci_hcd and address 7

```
and it just keeps doing that over and over.  I figured I could somehow use dd on it to try and restore the driver or something, but I dont even know what the path to the device.  Any ideas?

---

### Post by Taxman415a on 2008-07-21
You have to at least be able to get the driver to load in order to run tools like dd ddrescue, etc. I'll save you the lecture about unmounting cleanly, I think you got that message ;)

I can't think of any other things to try off the top of my head beside rebooting into a live rescue cd of some variety and seeing what it does with the flash drive.

---

### Post by poofyhairguy on 2008-07-22
Hmm....the drive might be gone. I have killed many flash drives with use.

The best bet to try to fix it is to use add/remove programs to install gparted (which will show up under system/administration/partition editor) and reformat the drive.

Be careful with gparted though, as you could erase your main drive with it if you are not careful. Double check the size of the drive you are formatting.

---

