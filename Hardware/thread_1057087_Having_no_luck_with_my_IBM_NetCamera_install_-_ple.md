---
title: "Having no luck with my IBM NetCamera install - please help."
date: 2009-02-01
forum: Hardware
---

### Post by Visible Spirit on 2009-02-01
---
[B][COLOR="DarkRed"]This thread was started to draw attention to this specific mdl/brand camera.
Originally posted [comment](http://ubuntuforums.org/showthread.php?t=1028559) got no response[/COLOR].[/B]
---


Greetings all,


I'm having no luck with my webcam situation. :(

I have an "Xirlink, Inc. IBM NetCamera" I'd like to use. It's the only webcam I have currently and I'm running [[COLOR="DimGray"]Ubuntu Studio[/COLOR]](http://ubuntustudio.org/) v8.04-(Hardy Heron). My webcam isn't recognized at all and I'm completely lost here. I'm learning Ubuntu as we go, although I can find my way around *somewhat* already. Going on two "looooong days" of research with this project prior to this posting and gotten nowhere yet.

I've installed "Cheese" and "Camera Monitor" just to see if the system would recognize it, but no luck. Otherwise, I haven't installed anything else and I'm sure I need to find a driver to install for it as well. I have the latest Kernel update which is version 2.6.24-23-rt .

The USB list output is as follows: (webcam in red)

```
XXXXXXXXXX@ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
[COLOR="Red"]Bus 003 Device 002: ID 0545:8002 Xirlink, Inc. IBM NetCamera[/COLOR]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 059b:0032 Iomega Corp. Zip 250 (Ver 2)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 001 Device 001: ID 0000:0000  
XXXXXXXXXX@ubuntu:~$
```

If anyone can help me figure this out and get it working it would be *greatly* appreciated. ;)


Regards,
Visible Spirit........


[COLOR="Red"]-------[/COLOR]
For anyone interested in the correct software and driver pkg to work correctly on a Windows XP 32bit system for the IBM PC Camera, NetCamera, or NetCameraPro, you can dwnld and install the file listed at DriverGuide.com labeled *XirlinkWinXP.exe [[COLOR="DimGray"]here[/COLOR]](http://members.driverguide.com/driver/detail.php?driverid=126571). This file was _updated *by* IBM_. This is _*not* a hacked file_. You'll need to register an account there to dwnld any files, which only requires an email account and a screen name.

*Clean file -- no viri found at time of dwnld using latest free version of [[COLOR="DimGray"]Avast AV for Windows[/COLOR]](http://www.avast.com/eng/download-avast-home.html).
 Free [[COLOR="DimGray"]Linux version[/COLOR]](http://www.avast.com/eng/download-avast-for-linux-edition.html) of Avast AV is available also.
[COLOR="Red"]-------[/COLOR]

-----
Note - All links are too their respective dwnld page. Nothing will be dwnldd too your computer. ;)
-----

---

### Post by Visible Spirit on 2009-02-01
Bump

---

### Post by Visible Spirit on 2009-02-03
BUMP

Just bumping this thread up in the hopes that *someone* out there might be able to help me get this webcam working. If anyone knows where I can find a driver that will work for this camera or can help me compile one that may work, it would be *very much* appreciated. Thanks.


Regards,
Visible Spirit

---

### Post by Visible Spirit on 2009-02-06
BUMP


Any help out there please!

---

### Post by waketech66 on 2009-02-16
I too have an IBM web cam that Ubuntu doesn't recognize.
here is the output
Bus 002 Device 002: ID 0545:8080 Xirlink, Inc. IBM C-It WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04b3:310c IBM Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

any ideas out there?

---

### Post by AMSlider on 2009-03-10
Did you try:

```
$ sudo modprobe ibmcam
```

also, what is in your dmesg output? here's mine:

```

[422826.112058] usb 1-2: new full speed USB device using uhci_hcd and address 3
[422826.281239] usb 1-2: configuration #1 chosen from 1 choice
[423041.015632] usb 1-2: IBM PC Camera USB camera found (model 2, rev. 0x030a)
[423041.015817] usb 1-2: ibmcam on /dev/video2: canvas=352x240 videosize=352x240
[423041.015884] usbcore: registered new interface driver ibmcam

```

and my lsusb output:

```

$ lsusb | grep IBM
Bus 001 Device 003: ID 0545:8080 Xirlink, Inc. IBM C-It WebCam

```

It seems to work fine for me, "cheese" popped right up.  Here's a good resource if you need more assistance:

[http://conshell.net/wiki/index.php/User:Fostermarkd/IBM_PC_Camera]("http://conshell.net/wiki/index.php/User:Fostermarkd/IBM_PC_Camera")

---

