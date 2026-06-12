---
title: "Aiptek T20 USB Projector Not Working on Linux"
date: 2010-08-17
forum: Hardware
---

### Post by qumah on 2010-08-17
This device is a pocket projector. Unlike most 'normal' projectors you connect it to the computer via USB not VGA port from your graphic card. It works properly on Windows, but doesn't work on Linux (Ubuntu 10.04 LTS - the Lucid Lynx ).

This device works in two modes, "Auto Installation" and "Projection". You switch between them by flipping a switch at the back of the projector.

On "Auto Installation" mode a new disk appears with Windows drivers. Running setup.exe in wine runs the Windows installer but it's useless.

On "Projection" mode nothing happens. When I do "lsusb" the device is listed as "Bus 001 Device 007: ID 08ca:2137 Aiptek International, Inc."

This is what appears in "dmesg" after plugging in the projector:

[  188.253026] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  188.404660] usb 1-3: configuration #1 chosen from 1 choice

Is there any way one can make this device work without being a programmer? I know how to use a computer via command line in Bash but that's as far as it goes.

---

### Post by Fafler on 2010-08-17
You need a Linux driver. Theres a good chance it's already supported, but because it identifies itself against the computer with USB vendor and device ID's, the kernel might not know which driver to use.

The default driver for this device is (atleast that i know of) sisusbvga, so what i suggest you do is to look at the sourcecode for sisusbvga (it's included in your kernel, just apt-get install the source) and look for either the email for on of the authors or a mailing list and get in contact with the correct people. They might help you out.

---

### Post by rogerdean on 2010-08-24
Hi qumah

Please let us know if you get this working - I'm considering one myself. I know it's a handheld and we should have low-ish expectations, but does it work well enough under windows? For movies as well as stills?

Cheers
Roger

---

### Post by qumah on 2010-08-30
Hi Rodger,

I bought two of these devices and created a 3d projector that works with polarized glasses one can purchase in cinemas supporting RealD 3D.

[IMG]http://user.xthost.info/cowtoons/random/pyromania/projector.jpg[/IMG]

[http://www.youtube.com/watch?v=Y4MIGqflk6M](http://www.youtube.com/watch?v=Y4MIGqflk6M)

I never managed to make it work on Linux. Unfortunately I'm not skilled enough to mess with system files. I know Bash pretty well, and I'm not a complete Linux noob. However becoming a programmer isn't the ultimate goal in my life and unfortunately I can't spend my whole week reading documentation, rendering the system unusable several times and doing all kinds of other frustrating stuff that is very unlikely to help anyway.

I set up the projectors in windows, they worked instantly after plugging in. I spent my time on learning stereoscopy and making a 3d short film instead of compiling experimental software.

These projectors are very weak because they are powered trough USB. If you want to use one of those for entertainment, you _**won't**_ be very satisfied with the brightness. I managed to achieve good quality (but nothing compared to cinema) by employing few tricks.

I eliminated any light in the room that doesn't come from the projectors (buy using them at night. ;) -- The eyes adjust for low brightness. The other trick is to create a silver screen (like ppl used in the old days for cinema) that reflects light much better than a white wall. I would say it's a 50% increase in brightness. In my case I had to use a silver screen anyway because only one like that reflects polarized light. You can use the matte side of tin foil one can buy in a supermarket or create a fancy screen by spray painting the wall (or screen, whatever) with a layer of black and than silver paint. I wouldn't consider buying one its like 3000€, you can make the same thing at home for less than 20€.

The further you place the projector from the screen, the bigger the picture will be. And of course with size brightness decreases. The best compromise between screen size and brightness for me was a 3 meter wide screen.

The picture is a slightly dark, but I don't care much about that. I tried every possible method for viewing 3D and this is the most comfortable way to do it. There's no ghosting between 2 pictures (cross chatter,) it's in natural full color unlike red/cyan crap and there's no psychedelic flickering like in shutter-glasses.

If you're thinking about making your own 3D projector I wouldn't recommend it unless you also create your own content to watch. It's pretty hard to find 3D films on the internet. I made a projector for myself because I do CGI. If you make computer animated short films it's not that hard for you to create a stereoscopic camera and have your content exported in full 3d.

---

### Post by rogerdean on 2010-09-01
qumah that's very impressive indeed. sorry it's not yet supported under linux, but i guess it'll be soon enough. have fun with your DIY 3D cinema!

---

### Post by alex.wifiguy on 2010-09-17
I own an Aiptek V10Plus Pocket Projector with S-video/Composite/Audio in and audio out. After finally finding a firmware update (it wasn't on there US site) I have the ability to project via USB. It enters "installation mode" by plugging it into the computer while the projector is powered off, with the option to project through USB within the on screen display
The device is listed as ID 08ca:2140 Aiptek International, Inc.

"Is there any way one can make this device work without being a programmer?"
Defiantly at first glance I thought this looked easy, I thought of it like a tv tuner card. We just have to know where and how to shoot that video thought the right USB port.
After analyzing the situation and digging around a little, with Fafler's hint at sisusbvga, it looks like there is indeed a driver out there already.
Take a look over here [http://ubuntuforums.org/showthread.php?t=260863](http://ubuntuforums.org/showthread.php?t=260863) and here [https://help.ubuntu.com/community/USB2VGA](https://help.ubuntu.com/community/USB2VGA).
sudo modprobe sisusbvga did nothing for me but I have yet to edit xorg.conf so it will detect it as a secondary monitor, it's 2 in the morning here I'm going to bed.
EDIT
It didn't work, it seems it may not use a sis chip at all, I'm not 100% sure about that.
My projector is model RVT+ V10Plus so I'm guessing it use's something made by rvtsystems [http://www.rvtsystems.com/](http://www.rvtsystems.com/).
I have not taken it apart to try and identify what chip it responsible for USB video.

---

### Post by harbaum on 2010-10-22
This device does not use a displaylink chip nor one of the sis/plc pairs used in some older usb2vga solutions. 

The aiptek t20 isn't supported by any linux driver today.

---

### Post by qumah on 2011-01-03
Thanks folks for help. I heard from a friend that most processors are clones these days and after like experimenting a week with different drivers it may be possible to make this work. I have absolutely no patience for that.

---

### Post by gopa on 2011-02-08
It seems to me that there is no driver available for this unit under Linux. And AIPTEK people are 
not planning to release one for Linux. Unfortunately, I bought one recently. I am going to send it 
back. I don't want to keep a hardware which is not supported under linux.

---

### Post by qumah on 2011-02-09
Nothing is supported on Linux, are you going to send everything back?

---

### Post by paulohahn on 2011-02-23
I have one RVT6 or T20, and I will make it work on linux... if I have specifications from Aiptek or other source.

If any one have news about its projectors please email me.

---

### Post by ellaivarios on 2011-06-18
I have the exact same problem.

I created a new thread, my apologies, although I searched extensively the forum, it is only now I stumbled upon this page (it was on the 6th page of my results)

[http://ubuntuforums.org/showthread.php?t=1785843&highlight=aiptek](http://ubuntuforums.org/showthread.php?t=1785843&highlight=aiptek)

has anyone found a way to edit Xorg.conf or make the drivers for this USB projector work?

It's a pitty Linux's lack of drivers forces us to use windows.

---

