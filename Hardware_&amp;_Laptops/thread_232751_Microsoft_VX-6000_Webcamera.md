---
title: "Microsoft VX-6000 Webcamera"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by Krislarsen on 2006-08-09
Hello!

I have a megapixel Microsoft VX-6000 webcamera.. This is a relatively new model, and I can't get it to work.

dmesg printout:

[17179842.684000] usb 5-5: new high speed USB device using ehci_hcd and address 6
[17179843.236000] 6:2:1: cannot get freq at ep 0x84
[17179843.244000] usbcore: registered new driver snd-usb-audio

The built-in mic seems to be recognized, but not the camera/video device itself.

Any suggestions?

---

### Post by Krislarsen on 2006-08-10
Nothing to do with it? Where should I post a request for this camera driver to be added?

I guess this will be one of the most popular webcams the next year(s), so it's importent to get a Linux driver for it... I can maybe write it myself, but not before one month or two from now.

---

### Post by liquilife on 2006-10-02
I have the VX-3000 variant of the same wecamera and same thing, it can recognize the microphone but not the camera it's self. I would also be very welcome of any such ideas on how to get this camera to work.

---

### Post by aeolos on 2006-11-09
I have a ViewMate webcam, and it gives the same error. I can't seem to find a driver for this webcam, so right now I'm a bit stuck with it. Does anybody have a clue where to go from here?

---

### Post by Donald on 2006-12-20
Newer Webcams seem to use the UVC driver. I would suggest to try
the following directions with the NX 6000:
[http://www.ubuntuforums.org/showthread.php?t=241681&highlight=webcam+uvc](http://www.ubuntuforums.org/showthread.php?t=241681&highlight=webcam+uvc)

---

### Post by Krislarsen on 2006-12-21
> **Donald said:**
> Newer Webcams seem to use the UVC driver. I would suggest to try
the following directions with the NX 6000:
[http://www.ubuntuforums.org/showthread.php?t=241681&highlight=webcam+uvc](http://www.ubuntuforums.org/showthread.php?t=241681&highlight=webcam+uvc)
Have you tried this driver with a MS cam? It seems to be a little bit Logitechish..

---

### Post by Donald on 2006-12-31
No, i have not tried it, i am looking for a good webcam which works with linux myself.
Although the uvc drivers were written with logiech cams in mind they should support
other uvc complient devices:

From the projects web-site:

"The goal of this project is to provide all necessary software components to fully support UVC compliant devices in Linux."

"The USB Device Class Definition for Video Devices, or USB Video Class, defines video streaming functionality on the Universal Serial Bus. Much like nearly all mass storage devices (USB flash disks, external IDE disk enclosures, ...) can be managed by a single driver because they conform to the USB Mass Storage specification, UVC compliant peripherals only need a generic driver."

So it might work for you if MS adheres to the uvc standard, but from what i read compiling
the drivers could be bit troublesome.

Further the uvc drivers work only with v4l2 compliant software, a lot of linux webcam software is
still based on v4l. It should work with "ekiga" though, which uses v4l2.

---

### Post by tweedy83 on 2007-01-09
I have tried the UVC drivers for the M$ VX6000 as suggested following the instructions on the referenced forum. But to no avail. Looking at the code it does look very logitech oriented and i guess further driver development will have to be made before this webcam works... :-(

Please find bellow my dmesg output after load the uvcvideo module with ```
$ sudo modprobe uvcvideo
``` and plugin in the Webcam

```

[17264196.392000] Linux video capture interface: v1.00
[17264196.416000] usbcore: registered new driver uvcvideo
[17264196.416000] USB Video Class driver (v0.1.0)
[17264351.100000] usb 5-5: new high speed USB device using ehci_hcd and address 3
[17264351.232000] usb 5-5: configuration #1 chosen from 1 choice
[17264351.816000] 3:2:1: cannot get freq at ep 0x84
[17264351.824000] usbcore: registered new driver snd-usb-audio
```

---

### Post by jamesjfa on 2007-01-15
I to have one of these camera's along with the laptop one nx-6000 and would love to get these working under linux. I have read and tried various posts but still can't get them to work. Hopefully somebody somewhere will have success. I really don't want to go back to windows...

---

### Post by Krislarsen on 2007-01-15
Almost a year since the first VX-cams shipped from factory now, and still no driver. I tried to open it to get any clues on the manufactor, but nothing interesting inside...

---

### Post by clint1010 on 2007-06-04
I have also purchased a VX-6000 webcam, probably should have looked at Linux compatability first, oh well.

I am very interested to hear if anyone has got this camera working with Linux

Cheers








I like :popcorn:

---

### Post by vivalant on 2007-10-26
From an old news, it seems this webcam is supported by the Generic SN9CXXX (not SN9C1xx), closed source driver at [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by the8thstar on 2007-11-09
I downloaded the package (.deb) for U7.04, but I couldn't install it because my kernel is U7.10. Is there a way to solve the problem?

---

### Post by the8thstar on 2007-11-13
Bump

---

### Post by the8thstar on 2007-11-25
Hello,

I could use some help... please?

---

### Post by bakadude on 2007-11-27
[http://www.linux-projects.org/modules/mydownloads/visit.php?cid=7&lid=54](http://www.linux-projects.org/modules/mydownloads/visit.php?cid=7&lid=54)

Did you try the one from the link above?

---

### Post by the8thstar on 2007-12-01
Okay, thanks for the link Bakadude. The driver installed perfectly. My webcam is now listed in the Skype video type, however when I hit the 'test' button the output is an ugly green screen with static on top... :( I wonder if there's a way to solve that.

---

### Post by vivalant on 2007-12-03
From the FAQ at [http://www.linux-projects.org](http://www.linux-projects.org), it seems that Skype 2 BETA does not support any video formats provided by the driver, so the bug is in the application.

---

### Post by Fullofit on 2008-01-08
I recently received a Logitech QuickCam Fusion and set about install it (Acer Travelmate 4502LCi) on Dapper (2.6 kernel). I tried the spca5xx dirver but had no luck. After a couple of different methods, I found out how to install the UVC generic driver, and it works.
Click [_[COLOR="Navy"]here[/COLOR]_]("https://help.ubuntu.com/community/UVC#head-5b809a5ceda87b4d0178626cf333c6865f975a60") for install instructions for linux-uvc. Note that you will also need build essential ($sudo apt-get install build-essential) in order to use the make command. Important! when you install the driver with make install, be sure that you are root; otherwise permissions will be denied to write to the installation directory.
Your webcam should work properly after inserting the modules. I guess you should add an entry in your /etc/apt/sources.list in order to ensure the module is in the kernel each time you start. I have not had a chance to test this yet so try without first as it may cause problems otherwise.
Note that the linux-uvc driver is compatible only with v4l2, not v4l1. This is important in the configuration of Ekiga. I tried using Camorama to capture video but could not open it. It appears that Camorama (possibly other programs as well) works with v4l1 and not v4l2. If anyone knows of a capture program (one for video together with sound and one for pictures or one for the lot) that works with v4l2 I would really like to know.

---

### Post by silverguy on 2008-01-21
iam using my vx6000

on ubuntu giesty 7.10

in amsn 


i installed some driver set its meantioned on this thread spc2001?

well restart your pc after this and mine worked
its blocky and not great but well it works.

---

### Post by Fullofit on 2008-01-24
Silverguy. Does the Microsoft VX-6000 Webcam use V4L1 or 2? If 2, did you have to open ports on your router for video connection? I have a Topcom Skyracer  254G and am limited in the amount of ports that I can open and wonder if I really have to permit UDP traffic as well as TCP.
Anyway, It appears that the mvcvideo module needs to be added each time a boot. Further, after a new kernel, my webcam no longer works. It's possible that making the driver is dependent on your kernel.

---

