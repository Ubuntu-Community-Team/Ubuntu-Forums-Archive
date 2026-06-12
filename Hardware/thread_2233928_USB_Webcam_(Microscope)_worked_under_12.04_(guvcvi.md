---
title: "USB Webcam (Microscope) worked under 12.04 (guvcview) but not with 14.04"
date: 2014-07-11
forum: Hardware
---

### Post by Camy on 2014-07-11
Hi All
I was using a USB microscope in Linux using 'guvcview' under 12.04 LTS. A few days ago I installed 14.04 LTS but now I'm getting a black screen in guvcview.
I installed the latest version of guvcview (1.7.3) by adding a PPA but it still didn't solve the issue.
After a couple of hours searching and trying things, I did a system test on the Microscope (USB Webcam) and got the following results.
 
camera/detect
[I][B]/dev/video0: OK 
name : Camera-X3 
driver : uvcvideo 
version: 3.13.11 
flags : 0x84000001 [ CAPTURE STREAMING ] 
Format: YUYV (YUV 4:2:2 (YUYV)) Resolutions: 1024x768,640x480,320x240,2048x1536,800x600,1280x1024 [/B][/I]

camera/display
***libv4l2: error turning on stream: Broken pipe ***

camera/still
***Fontconfig warning: ignoring C.UTF-8: not a valid language tag ***


So does that mean I have to wait for the guvcview team to get this fixed. 
Cheese doesn't work either. I think it used to work in 12.04 (not sure)

Am I going to have to go through VirtualBox to get it to work?

Thanks

---

### Post by tgalati4 on 2014-07-11
Open a terminal, plug the camera in and post the output of:

```
dmesg | tail -50
```

Just post the camera-related stuff.

Prepare a USB Boot stick with 12.04 (or create a virtual machine with 12.04, but that may not work) on it because you will need it to compare the behavior between the two.  Unfortunately regressions happen and it requires quite an effort to troubleshoot.

---

### Post by Camy on 2014-07-11
dmesg | tail -50

> 
[   10.220686] usbcore: registered new interface driver usbhid
[   10.220688] usbhid: USB HID core driver
[   10.396243] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9.3/3-9.3:1.0/input/input10
[   10.396327] hid-generic 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:14.0-9.3/input0
[   10.825351] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   11.319998] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.647852] init: failsafe main process (598) killed by TERM signal
[   12.507498] Bluetooth: Core ver 2.17
[   12.507510] NET: Registered protocol family 31
[   12.507511] Bluetooth: HCI device and connection manager initialized
[   12.507517] Bluetooth: HCI socket layer initialized
[   12.507519] Bluetooth: L2CAP socket layer initialized
[   12.507521] Bluetooth: SCO socket layer initialized
[   12.510566] Bluetooth: RFCOMM TTY layer initialized
[   12.510574] Bluetooth: RFCOMM socket layer initialized
[   12.510578] Bluetooth: RFCOMM ver 1.11
[   12.642385] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.642387] Bluetooth: BNEP filters: protocol multicast
[   12.642394] Bluetooth: BNEP socket layer initialized
[   13.053254] init: cups main process (732) killed by HUP signal
[   13.053262] init: cups main process ended, respawning
[   13.682078] r8169 0000:03:00.0 eth0: link down
[   13.682098] r8169 0000:03:00.0 eth0: link down
[   13.682792] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.683050] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.402517] vboxdrv: module verification failed: signature and/or  required key missing - tainting kernel
[   14.403970] vboxdrv: Found 2 processor cores.
[   14.404904] vboxdrv: fAsync=0 offMin=0x1ac offMax=0x874
[   14.405433] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   14.405435] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
[   14.416908] vboxpci: IOMMU not found (not registered)
[   15.335336] init: plymouth-upstart-bridge main process ended, respawning
[   15.376610] r8169 0000:03:00.0 eth0: link up
[   15.376617] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   15.436357] init: plymouth-upstart-bridge main process ended, respawning
[   42.805159] audit_printk_skb: 174 callbacks suppressed
[   42.805162] type=1400 audit(1405114125.620:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2423 comm="apparmor_parser"
[   42.805166] type=1400 audit(1405114125.620:71): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2423 comm="apparmor_parser"
[   42.805414] type=1400 audit(1405114125.620:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2423 comm="apparmor_parser"
[  113.122871] usb 3-4: new high-speed USB device number 4 using xhci_hcd
[  113.171914] usb 3-4: New USB device found, idVendor=0ac8, idProduct=3370
[  113.171922] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  113.171927] usb 3-4: Product: Camera-X3
[  113.171932] usb 3-4: Manufacturer: Vimicro Corp.
[  113.171936] usb 3-4: SerialNumber: MI1320_SOC
[  113.189911] Linux video capture interface: v2.00
[  113.196812] uvcvideo: Found UVC 1.00 device Camera-X3 (0ac8:3370)
[  113.198751] input: Camera-X3 as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input11
[  113.198846] usbcore: registered new interface driver uvcvideo
[  113.198848] USB Video Class driver (1.1.1)


---

### Post by Camy on 2014-07-11
It's working :p

I plugged it into a usb 2.0 hub and it is working. Before it was plugged into the back of my motherboard. When I switched it back to the motherboard it didn't work again. Then I had to logout and back in again for it to work in the usb 2.0 hub. The hub is also plugged into the back of my motherboard but the hub specifically has USB 2.0 on it and I know that the microscope specifically says you need a USB 2 port but I thought that if it was a USB 3 it would be downward compatible. 

Oh well, thanks for your help just the same .
 				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar241895_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=241895") 				 				 					 						 	[**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895")

---

### Post by Camy on 2014-07-12
Sorry I forgot to mention that I also changed my motherboard and cpu when I switched from 12.04 to 14.04.

---

### Post by Camy on 2014-07-13
Just incase any one else runs into this. Cheese, and Kamerka also work with the Microscope. guvcview has the most settings and is the best one to use. The only thing is, every now and then it will hang on Ubuntu 14.04LTS and the only way I can get it going again, is to reboot.

---

### Post by nscbabu on 2015-07-09
USB microscope seem to be very interesting. I will try to get one and test with my QtCam application.

---

