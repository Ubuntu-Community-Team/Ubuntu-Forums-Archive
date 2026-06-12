---
title: "usb 1-1: device not accepting address 2, error -71"
date: 2008-08-27
forum: Hardware
---

### Post by mattybats on 2008-08-27
I'm interested in getting rid of this error message.  I understand that it does not affect the working order of anything, but it does seem to slow down the boot process.  I tried blacklisting ehci_hcd and uhci_hcd in /etc/modprobe.d/blacklist and then adding them to modules with ehci_hcd first in the list.  

[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17573.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17573.html))
[http://www.jasonparekh.com/?page_id=9](http://www.jasonparekh.com/?page_id=9)
(Scroll to Trackpad / Touchpad Section)

This did not work.  The error still comes up during boot.  It seems to be the first thing loaded.  I'm not sure if this has something to do with udev.  I started reading the man page on udev and looking at the rules files in /etc/udev but I don't understand all of it, and I'm not sure where hotplug fits into this, if at all.  Does anyone know how to get rid of this error message on Xubuntu Hardy Heron 8.04?

---

### Post by chuckcastle on 2008-08-29
I am having a similar problem (though I believe mine to be a failed drive).  I receive:

```
152.426574 USB 1-2: Device not accepting address 2, error -71
```

When booting into 8.04.1.  I have tried multiple Windows machines and receive a "USB Device not recognized" error and the drive fails to mount.  I tried running TestDisk but it, too, fails to recognize the drive.

I am a UNIX newb and ended up installing Hardy Heron after some successful data recovery with Knoppix.

*update*
After playing around a bit, I decided to go poking around in /var/log/messages:

```
Aug 29 16:02:07 ubuntu kernel: [ 1612.431117] usb 5-8: new high speed USB device using ehci_hcd and address 7
Aug 29 16:02:07 ubuntu kernel: [ 1612.639457] usb 5-8: configuration #1 chosen from 1 choice
Aug 29 16:02:07 ubuntu kernel: [ 1612.643299] scsi8 : SCSI emulation for USB Mass Storage devices
Aug 29 16:02:19 ubuntu kernel: [ 1624.240890] usb 5-8: reset high speed USB device using ehci_hcd and address 7
Aug 29 16:02:29 ubuntu kernel: [ 1634.493334] usb 5-8: reset high speed USB device using ehci_hcd and address 7
Aug 29 16:02:30 ubuntu kernel: [ 1634.772850] usb 5-8: reset high speed USB device using ehci_hcd and address 7
Aug 29 16:02:40 ubuntu kernel: [ 1645.025318] usb 5-8: reset high speed USB device using ehci_hcd and address 7
Aug 29 16:02:40 ubuntu kernel: [ 1645.175623] scsi 8:0:0:0: Device offlined - not ready after error recovery

```

---

### Post by jpeery on 2008-09-08
I get something similar when I try to access/use my thumbdrive (8gb)  Only my error code is -110, after I insert the stick, if I check dmesg this is what I get:

[15973.477743] usb 2-6: new high speed USB device using ehci_hcd and address 24
[15978.693488] usb 2-6: device not accepting address 24, error -110

All I can gather is ehci_hcd is having problems, how to address it I've no idea.  All I know is this is as much as I can dig up, and I can't access my thumbdrive, even though it works on my MAC and my Intel PC running Ubuntu.  Just doesn't like this laptop...

Hope someone reads this that knows more about it than I.
JP

---

### Post by jpeery on 2008-09-08
reading another thread I did this:
sudo modprobe -r ehci_hcd

Works now

---

### Post by registrator on 2008-09-21
I got similar problem too.
ehci_hcd is for USB 2.0 device, and i don't want to remove it.
i also changed the order(ehci first, then uhci..still not working).
some forum said that you have to update the initrd using mkinitrd, but this command is not found in my xubuntu 8.04..
[https://bugzilla.redhat.com/show_bug.cgi?id=213411]("https://bugzilla.redhat.com/show_bug.cgi?id=213411")

i tried using update-initramfs too..still not working
sorry for my bad english..

---

### Post by Kernel_Krunch on 2008-09-24
Removing ehci_hcd only leaves you with USB1.0 speed.  The new kernel in Intrepid solved the problem for me.

---

