---
title: "Webcam on Asus T91 Netbook"
date: 2009-08-27
forum: Hardware
---

### Post by Leed on 2009-08-27
I have got nearly everything running real smooth on my new T91, display drivers and wireless weren't easy, but solved.

What I'm still missing is support for the Webcam, can someone help. I'm not sure what details you guys would need, but I'll follow any instructions you give on this matter, so that anyone else who finds this thread will hopefully have a solution at hand.

So what do I need in order to find the correct drivers (or anything else) for my webcam?

---

### Post by Leed on 2009-08-27
This is the data I've collected from the System Check application in UNR

USB 2.0 Camera
Property	Value
info.subsystem	usb_device
info.product	USB 2.0 Camera
info.vendor	IMC Networks
info.parent	/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7
info.linux.driver	usb
info.udi	/org/freedesktop/Hal/devices/usb_device_13d3_509b_noserial
usb_device.linux.sysfs_path	/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7
usb_device.linux.device_number	5
usb_device.is_self_powered	False
usb_device.vendor_id	5075
usb_device.vendor	IMC Networks
usb_device.product_id	20635
usb_device.device_protocol	1
usb_device.device_revision_bcd	775
usb_device.device_subclass	2
usb_device.speed	480.0
usb_device.configuration_value	1
usb_device.bus_number	1
usb_device.product	USB 2.0 Camera
usb_device.num_configurations	1
usb_device.version	2.0
usb_device.num_ports	0
usb_device.max_power	98
usb_device.device_class	239
usb_device.can_wake_up	False
usb_device.num_interfaces	2
linux.device_file	/dev/bus/usb/001/005
linux.hotplug_type	2
linux.subsystem	usb
linux.sysfs_path	/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7

---

### Post by Leed on 2009-08-28
I've also done

dmesg | grep uvcvideo

and received

[    7.839086] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (13d3:509b)
[    7.860547] usbcore: registered new interface driver uvcvideo
[   48.279016] uvcvideo: Failed to query (135) UVC control 4 (unit 3) : -32 (exp. 2).

---

### Post by Perig on 2009-11-09
Hi - Have you tried Kamoso? I don't use it for chatting, just for taking pictures and little videos. It worked just fine, no special fine tuning needed.
- Ubuntu 9.10 -

---

### Post by LukeKendall on 2009-12-15
> **Perig said:**
> Hi - Have you tried Kamoso? I don't use it for chatting, just for taking pictures and little videos. It worked just fine, no special fine tuning needed.
- Ubuntu 9.10 -

I followed your tip, and it basically worked fine, but the kamoso window doesn't seem to be resizable, which makes it very tricky to operate - if you visit the website and watch the video, you'll be able to guess what the top sliver of the widgets at the bottom of the screen are, and with that knowledge you should be able to use it more or less.

(Thanks for the tip!)

I should probably add, that in contrast, the "Cheese" camera application doesn't work (won't take a photo or a video).

luke

---

