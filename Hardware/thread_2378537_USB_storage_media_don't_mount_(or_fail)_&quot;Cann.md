---
title: "USB storage media don't mount (or fail): &quot;Cannot enable.&quot; / &quot;unable to enumerate&quot;"
date: 2017-11-24
forum: Hardware
---

### Post by usbvictim on 2017-11-24
Hi all,

for a while now I've been having trouble mounting USB storage media under Xubuntu 17.04. They either don't mount at all, only after several tries, of if they do mount then they often fail after a few seconds.

_ It happens..._
[LIST]
[*]with USB sticks, an e-reader, a tablet, an SD card reader 
[*]with both USB 2.0 and USB 3.0 devices 
[*]with every USB port of my computer (2.0/3.0, front/back, directly or via USB 3.0 extension) 
[/LIST]

_ However, I have no issues..._
[LIST]
[*]with two USB 3.0 external HDDs I own (WD and Toshiba) 
[*]with any of the devices when using Windows on the same PC, or when using Windows on a different computer; leading me to believe that it might be more of a driver than hardware issue 
[*]with non-storage devices, both keyboard and mouse always work fine 
[/LIST]

This is tail **/var/log/syslog** when I mount a device (essentially the same every time the issue appears):

```
Jul 25 19:16:29 pc2015 kernel: [ 1309.907743] usb usb3-port11: Cannot enable. Maybe the USB cable is bad?
Jul 25 19:16:29 pc2015 kernel: [ 1310.799734] usb usb3-port11: Cannot enable. Maybe the USB cable is bad?
Jul 25 19:16:30 pc2015 kernel: [ 1311.691704] usb usb3-port11: Cannot enable. Maybe the USB cable is bad?
Jul 25 19:16:31 pc2015 kernel: [ 1312.583727] usb usb3-port11: Cannot enable. Maybe the USB cable is bad?
Jul 25 19:16:31 pc2015 kernel: [ 1312.583745] usb usb3-port11: unable to enumerate USB device
```

Then, **lsusb** will not show any new device. Sometimes (especially in the case of the e-reader) the device will be shown in gparted regardless, but can't then be mounted ("no Media").

In very rare cases (I'd say 1 out of 20) I can successfully mount, but then sometimes it fails and gets unmounted. I think this log message relates to it:

```
 Jul 25 19:02:56 pc2015 colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
```

I have a Gigabyte Z97-HD3 mainboard and updated it to the most recent version. (Unless there's a fix already for the Intel ME issues...)

Does anyone have any idea what's causing this and how I can fix it?

Thanks!

---

