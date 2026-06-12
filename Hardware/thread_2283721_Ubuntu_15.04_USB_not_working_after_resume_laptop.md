---
title: "Ubuntu 15.04 USB not working after resume laptop"
date: 2015-06-24
forum: Hardware
---

### Post by 7-webmaster on 2015-06-24
My laptop suspended due to inactivity.  When I came back and pressed the power button the system resumed and everything worked except the mouse, which was the only USB attached device.  I tried unplugging and plugging the mouse.  I tried plugging in a different mouse.  I plugged in my e-reader and the system did not see it. When I look at dmesg it does not show any messages related to any of the devices I plugged in.  I am going to power off now.

[161394.418072] usb 6-3: Manufacturer: CKFA228h475010006CQ0
[161394.420234] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (05ca:181d)
[161394.422860] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:13.2/usb6/6-3/6-3:1.0/input/input47
[161394.535207] usb 6-5: new high-speed USB device number 67 using ehci-pci
[161394.683995] usb 6-5: New USB device found, idVendor=0bda, idProduct=0138
[161394.684007] usb 6-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[161394.684014] usb 6-5: Product: USB2.0-CRW
[161394.684019] usb 6-5: Manufacturer: Generic
[161394.684023] usb 6-5: SerialNumber: 20090516388200000
[161394.691032] ums-realtek 6-5:1.0: USB Mass Storage device detected
[161394.714699] scsi host37: usb-storage 6-5:1.0
[161394.715330] usb 6-5: USB disconnect, device number 67
[161395.386455] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[161395.424198] ata3.00: configured for UDMA/133
[161395.900708] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[161396.041418] r8169 0000:01:00.0 eth0: link down
[161397.464498] atkbd serio0: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
[161397.464511] atkbd serio0: Use 'setkeycodes e00d <keycode>' to make it known.
[161398.407294] r8169 0000:01:00.0 eth0: link up

---

### Post by 7-webmaster on 2015-07-10
Further information, this is on a Dell Vostro 3555, approximately a 4 year old device, so not exactly a bleeding edge piece of hardware.  Also sometime the network manager icon does not appear after resume and I cannot access wi-fi.  However at least the display hardware now works thanks presumably to the improvements in support for AMD graphics in kernel 3.19 and maybe also to Systemd handling of resume.

---

