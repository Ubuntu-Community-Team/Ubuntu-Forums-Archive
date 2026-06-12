---
title: "USB drive isn't recognized"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by Phantom784 on 2007-03-27
I have an 1 gig LG usb drive, but it won't I can't get it to mount under linux.  I typed in "lsusb" and saw that it was listed as an attached usb device.  However, when I typed in "ls /dev/sd*" I only saw the one device, which I know is my SATA harddrive.  Any ideas?

Edit: I should add that the device worked just fine on Windows XP, and I've had it working on Linux before.

---

### Post by simonn on 2007-03-27
1) Unplug the drive.

2) Plug in the drive

3) Wait a few seconds

4) Post the output of dmesg here.

---

### Post by Phantom784 on 2007-03-28
```

[18038796.596000] eth0: link up.
[18038796.600000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[18038806.944000] eth0: no IPv6 routers present
[18038813.264000] eth0: link down.
[18038816.304000] eth0: link up.
[18038816.304000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[18038822.872000] usb 2-10.2: new full speed USB device using ohci_hcd and address 3
[18038822.992000] usb 2-10.2: configuration #1 chosen from 1 choice
[18038823.548000] Linux video capture interface: v1.00
[18038823.576000] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.3 $Date: 2005/04/15 19:32:49 $)
[18038823.576000] quickcam: Kernel:2.6.17-11-generic bus:2 class:FF subclass:FF vendor:046D product:0850
[18038823.616000] quickcam: Sensor VV6410 detected
[18038823.624000] quickcam: Registered device: /dev/video0
[18038823.624000] usbcore: registered new driver quickcam
[18038823.776000] usbcore: registered new driver snd-usb-audio
[18038833.432000] eth0: no IPv6 routers present
[18053353.048000] usb 2-10.4: new full speed USB device using ohci_hcd and address 4
[18053353.160000] usb 2-10.4: not running at top speed; connect to a high speed hub
[18053353.180000] usb 2-10.4: no configuration chosen from 1 choice
[18053424.944000] cramfs: wrong magic
[18053424.948000] VFS: Can't find ext3 filesystem on dev sda.
[18053425.084000] UDF-fs: No partition found (1)
[18053425.096000] Unable to identify CD-ROM format.
[18053448.736000] FAT: invalid media value (0x00)
[18053448.736000] VFS: Can't find a valid FAT filesystem on dev sda.
[18053489.604000] FAT: invalid media value (0x00)
[18053489.604000] VFS: Can't find a valid FAT filesystem on dev sda.
[18053501.036000] usb 2-10.4: USB disconnect, address 4
[18053504.476000] usb 2-10.3: new full speed USB device using ohci_hcd and address 5
[18053504.580000] usb 2-10.3: not running at top speed; connect to a high speed hub
[18053504.596000] usb 2-10.3: no configuration chosen from 1 choice
[18053511.212000] usb 2-10.3: USB disconnect, address 5
[18053821.928000] usb 2-10.3: new full speed USB device using ohci_hcd and address 6
[18053822.032000] usb 2-10.3: not running at top speed; connect to a high speed hub
[18053822.048000] usb 2-10.3: no configuration chosen from 1 choice
[18053880.824000] usb 2-10.3: USB disconnect, address 6
[18053887.908000] usb 2-10.3: new full speed USB device using ohci_hcd and address 7
[18053888.020000] usb 2-10.3: not running at top speed; connect to a high speed hub
[18053888.040000] usb 2-10.3: no configuration chosen from 1 choice
[18054318.492000] usb 2-10.3: USB disconnect, address 7
[18054369.280000] usb 2-10.4: new full speed USB device using ohci_hcd and address 8
[18054369.388000] usb 2-10.4: not running at top speed; connect to a high speed hub
[18054369.404000] usb 2-10.4: no configuration chosen from 1 choice
[18059472.756000] ISO 9660 Extensions: Microsoft Joliet Level 3
[18059472.792000] ISO 9660 Extensions: RRIP_1991A
[18125130.640000] usb 2-10.4: USB disconnect, address 8
[18125164.144000] usb 2-10.4: new full speed USB device using ohci_hcd and address 9
[18125164.256000] usb 2-10.4: not running at top speed; connect to a high speed hub
[18125164.276000] usb 2-10.4: no configuration chosen from 1 choice

```

i cut most of the output off, assuming the stuff at the end is important.  since it said connect to a high speed hub, i plugged it in the back of my computer directly and it worked.  However, I'm pretty sure I've had it working on this hub before.

---

### Post by louisgag on 2007-04-08
" no configuration chosen from 1 choice"

same problem here with my 2gb mp3 player

---

