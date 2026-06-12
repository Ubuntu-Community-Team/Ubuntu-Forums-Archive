---
title: "Logitech C920 Webcam &quot;No Device Found&quot; Cheese"
date: 2017-08-09
forum: Hardware
---

### Post by zalkota on 2017-08-09
Hi,

I am fairly new to Linux and I am trying to get my Logitech C920 webcam to work with Cheese. 

The webcam is not broken, as it works on my windows 7 operating system, but Ubuntu will not detect the USB when I run "lsusb" in the terminal.

[http://imgur.com/a/jlJcx](http://imgur.com/a/jlJcx)

[IMG]http://imgur.com/a/jlJcx[/IMG]

This is what is returned when I run lsusb

I tried changing what usb port it was connected to as well with no avail.



Dom

---

### Post by vocx on 2017-08-10
> **zalkota said:**
> Hi,

I am fairly new to Linux and I am trying to get my Logitech C920 webcam to work with Cheese. 

The webcam is not broken, as it works on my windows 7 operating system, but Ubuntu will not detect the USB when I run "lsusb" in the terminal.

[http://imgur.com/a/jlJcx](http://imgur.com/a/jlJcx)


This is what is returned when I run lsusb

I tried changing what usb port it was connected to as well with no avail.
Dom
Please never take a picture of terminal output. Since the terminal shows plain text, you can just post it here in nice "CODE" tags so it retains the formatted spaces.
```

Bus 001 Device 005: ID 1997:2433  
Bus 001 Device 007: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp. SMSC9512/9514 Fast Ethernet Adapter
Bus 001 Device 002: ID 0424:9514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Cheese may be expecting a standard device name "/dev/video0".  When you connect your camera, the created device may actually have another name. So, instruct cheese to use this other device name.
```

cheese -d /dev/video1

```

Connect your camera and then see the last few lines from the kernel messages to see if there is any error.
```

dmesg | tail -50

```

```

[530334.990010] [<804f6744>] (put_device) from [<7f0b5518>] (v4l2_release+0x60/0x84 [videodev])
[530334.990123] [<7f0b5518>] (v4l2_release [videodev]) from [<802720f0>] (__fput+0x9c/0x1e8)
[530334.990138] [<802720f0>] (__fput) from [<802722ac>] (____fput+0x18/0x1c)
[530334.990152] [<802722ac>] (____fput) from [<8013ab9c>] (task_work_run+0xcc/0xfc)
[530334.990168] [<8013ab9c>] (task_work_run) from [<8010b838>] (do_work_pending+0xcc/0xd0)
[530334.990184] [<8010b838>] (do_work_pending) from [<801080e8>] (slow_work_pending+0xc/0x20)
[530334.990191] ---[ end trace 287403e265328cd7 ]---
[530335.075538] usb 1-1.2: new high-speed USB device number 6 using dwc_otg
[535308.144427] usb 1-1.2: new high-speed USB device number 7 using dwc_otg
[535309.426439] usb 1-1.2: New USB device found, idVendor=046d, idProduct=082d
[535309.426454] usb 1-1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=1
[535309.426462] usb 1-1.2: Product: HD Pro Webcam C920
[535309.426470] usb 1-1.2: SerialNumber: A49338EF
[535309.427581] uvcvideo: Found UVC 1.00 device HD Pro Webcam C920 (046d:082d)
[535309.431108] uvcvideo 1-1.2:1.0: Entity type for entity Processing 3 was not initialized!
[535309.431127] uvcvideo 1-1.2:1.0: Entity type for entity Extension 6 was not initialized!
[535309.431138] uvcvideo 1-1.2:1.0: Entity type for entity Extension 12 was not initialized!
[535309.431150] uvcvideo 1-1.2:1.0: Entity type for entity Camera 1 was not initialized!
[535309.431161] uvcvideo 1-1.2:1.0: Entity type for entity Extension 8 was not initialized!
[535309.431172] uvcvideo 1-1.2:1.0: Entity type for entity Extension 9 was not initialized!
[535309.431205] uvcvideo 1-1.2:1.0: Entity type for entity Extension 10 was not initialized!
[535309.431216] uvcvideo 1-1.2:1.0: Entity type for entity Extension 11 was not initialized!
[535309.431851] input: HD Pro Webcam C920 as /devices/platform/soc/3f980000.usb/usb1/1-1/1-1.2/1-1.2:1.0/input/input4

```

---

### Post by vasa1 on 2017-08-10
> **vocx said:**
> Please never take a picture of terminal output. Since the terminal shows plain text, you can just post it here in nice "CODE" tags so it retains the formatted spaces.
...
+1

Posting your terminal output between code tags rather than as an image also allows others to copy part of the output when responding to you.

---

