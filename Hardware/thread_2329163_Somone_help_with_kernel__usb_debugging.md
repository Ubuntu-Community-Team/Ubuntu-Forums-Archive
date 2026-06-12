---
title: "Somone help with kernel / usb debugging?"
date: 2016-06-28
forum: Hardware
---

### Post by cathect2 on 2016-06-28
I'm plagued by a usb problem. I have an external soundcard--a [Topping VX2]("http://www.tpdz.net/en/products/vx2/index.htm")--that connects via usb. Under Ubuntu 15.04 and 15.10, the device worked as expected. But under Ubuntu 16.04, it causes severe problems:

1. When plugged in, the device often interferes with boot. Unplug the device, and Ubuntu boots as expected.
2. If left plugged in while booting/rebooting, upon successful login, all desktop icons and other theme-based decoration is reverted to the default Ubuntu settings.
3. If plugged in after successful boot and login, the device seems to nuke Pulseaudio: it wipes out **all** devices in "Sound Settings," giving the impression that there are no sound cards in the machine. Remove the usb cord, and all is well--my devices all return.
4. During a reboot with the device plugged in, Ubuntu seems to hang and gives -110 USB errors.

* Thinking I had  a defective unit, I returned this device for another one. However, the new device causes the exact same problems. 

* The VX2 uses Via Technologies VT 1620A USB audio controller. 

Could someone help me debug this and help me file the information as a bug against the kernel? I'm not sure how to go about this. 

A portion from my kernel log:

```
kernel: [  318.180047] usb 3-12: new full-speed USB device number 10 using xhci_hcd
Jun 28 13:51:11 Rufus kernel: [  318.408031] usb 3-12: New USB device found, idVendor=040d, idProduct=3400
Jun 28 13:51:11 Rufus kernel: [  318.408036] usb 3-12: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 28 13:51:11 Rufus kernel: [  318.408039] usb 3-12: Product: VX2
Jun 28 13:51:11 Rufus kernel: [  318.408041] usb 3-12: Manufacturer: TOPPING
Jun 28 13:51:12 Rufus kernel: [  318.955602] input: TOPPING VX2 as /devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12:1.2/0003:040D:3400.000A/input/input23
Jun 28 13:51:12 Rufus kernel: [  319.008253] hid-generic 0003:040D:3400.000A: input,hidraw7: USB HID v1.00 Device [TOPPING VX2] on usb-0000:00:14.0-12/input2
Jun 28 13:51:12 Rufus mtp-probe: checking bus 3, device 10: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-12"
Jun 28 13:51:12 Rufus mtp-probe: bus: 3, device: 10 was not an MTP device
Jun 28 13:51:21 Rufus org.gtk.vfs.Daemon[1944]: ** (gvfsd:1995): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection timed out
Jun 28 13:51:21 Rufus org.gtk.vfs.Daemon[1944]: ** (process:2686): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jun 28 13:51:22 Rufus kernel: [  329.060630] usb 3-12: 1:1: usb_set_interface failed (-110)
Jun 28 13:51:22 Rufus pulseaudio[2191]: [alsa-source-USB Audio] ratelimit.c: 1096 events suppressed
Jun 28 13:51:22 Rufus pulseaudio[2191]: [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally
Jun 28 13:51:27 Rufus kernel: [  334.060518] usb 3-12: 1:1: usb_set_interface failed (-110)
Jun 28 13:51:23 Rufus pulseaudio[2191]: message repeated 10 times: [ [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally]
Jun 28 13:51:27 Rufus pulseaudio[2191]: [alsa-source-USB Audio] ratelimit.c: 114 events suppressed
Jun 28 13:51:27 Rufus pulseaudio[2191]: [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally
Jun 28 13:51:32 Rufus kernel: [  339.060521] usb 3-12: 1:1: usb_set_interface failed (-110)
Jun 28 13:51:28 Rufus pulseaudio[2191]: message repeated 10 times: [ [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally]
Jun 28 13:51:32 Rufus pulseaudio[2191]: [alsa-source-USB Audio] ratelimit.c: 114 events suppressed
Jun 28 13:51:32 Rufus pulseaudio[2191]: [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally
Jun 28 13:51:37 Rufus kernel: [  344.060559] usb 3-12: 1:1: usb_set_interface failed (-110)
Jun 28 13:51:33 Rufus pulseaudio[2191]: message repeated 10 times: [ [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally]
Jun 28 13:51:37 Rufus pulseaudio[2191]: [alsa-source-USB Audio] ratelimit.c: 114 events suppressed
Jun 28 13:51:37 Rufus pulseaudio[2191]: [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally
Jun 28 13:51:42 Rufus kernel: [  349.060535] usb 3-12: 1:1: usb_set_interface failed (-110)
Jun 28 13:51:38 Rufus pulseaudio[2191]: message repeated 10 times: [ [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally]
Jun 28 13:51:42 Rufus pulseaudio[2191]: [alsa-source-USB Audio] ratelimit.c: 115 events suppressed
Jun 28 13:51:42 Rufus pulseaudio[2191]: [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally
Jun 28 13:51:47 Rufus kernel: [  354.060528] usb 3-12: 1:1: usb_set_interface failed (-110)
Jun 28 13:51:43 Rufus pulseaudio[2191]: message repeated 10 times: [ [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally]
Jun 28 13:51:47 Rufus pulseaudio[2191]: [alsa-source-USB Audio] ratelimit.c: 115 events suppressed
Jun 28 13:51:47 Rufus pulseaudio[2191]: [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally
Jun 28 13:51:52 Rufus kernel: [  359.060519] usb 3-12: 1:1: usb_set_interface failed (-110)
Jun 28 13:51:48 Rufus pulseaudio[2191]: message repeated 10 times: [ [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally]
Jun 28 13:51:52 Rufus pulseaudio[2191]: [alsa-source-USB Audio] ratelimit.c: 114 events suppressed
Jun 28 13:51:52 Rufus pulseaudio[2191]: [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally
Jun 28 13:51:57 Rufus kernel: [  364.060528] usb 3-12: 1:1: usb_set_interface failed (-110)
Jun 28 13:52:02 Rufus kernel: [  369.060563] usb 3-12: 1:1: usb_set_interface failed (-110)
Jun 28 13:52:02 Rufus kernel: [  369.069799] usb 3-12: USB disconnect, device number 10
Jun 28 13:52:02 Rufus kernel: [  369.070133] usb 3-12: 1:1: usb_set_interface failed (-71)
Jun 28 13:51:58 Rufus pulseaudio[2191]: message repeated 15 times: [ [alsa-source-USB Audio] asyncq.c: q overrun, queuing locally]
Jun 28 13:52:02 Rufus acpid: input device has been disconnected, fd 20
Jun 28 13:52:19 Rufus dbus[924]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service'

```
Thank you.

---

### Post by cathect2 on 2016-06-29
Bump

---

### Post by jeremy31 on 2016-06-29
If you want to file a bug report see [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

In step # 1 use ```
ubuntu-bug linux
```

And go from there.  I tried a internet search on the device and couldn't find any recent fixes

---

