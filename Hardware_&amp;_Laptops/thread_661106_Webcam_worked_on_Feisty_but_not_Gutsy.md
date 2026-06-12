---
title: "Webcam worked on Feisty but not Gutsy"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by Tatty on 2008-01-07
Hey there,

I bought a Creative Live! Cam Notebook Pro webcam a few months ago because the hardware support wiki page said it was supported out of the box - [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasCreative]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasCreative")

As promised i plugged it into my laptop with Feisty installed and it worked with no configuration needed.

After several months of being unused, i dug it out and plugged it into a Gutsy machine.  This time, failure, it doesnt seem to work.  I tried camorama but it came up with the error message "could not connect to video device (/dev/video0)".

I tried both easycam and easycam2, but neither of those yeilded any results.  I then went back and looked at the wiki hardware support entry (above) and saw that the driver it uses is "gspca".  so i loaded synaptic and searched for gspca.  I found an entry for gspca-source, which i installed.  But sadly when i tried to load the readme file that is mentioned in the description, it appears no such file exists.

Does anyone know why the webcam was supported in Feisty but not Gutsy?  More importantly does anyone know how to get the webcam working?

Or am i just doing something really dumb?

output of lsusb:
```
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 005 Device 002: ID 2040:9950 Hauppauge
Bus 004 Device 003: ID 050d:705c Belkin Components
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 003: ID 1631:5002
Bus 002 Device 002: ID 1631:5400
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 041e:4051 Creative Technology, Ltd
Bus 001 Device 001: ID 0000:0000

```

Many Thanks,

---

### Post by Tatty on 2008-01-07
*shamelss bump* :popcorn:

---

### Post by zanoman on 2008-01-22
SAme for me
I have 3 (same) webcams, they worked on edgy and feisty and NOT on gusty.
It's "no name" cameras, but with 3, I can say that the camera is not at fault
when plugged in, log show that a webcam was plugged in:
```
Jan 22 19:31:24 localhost kernel: [37104.089819] usb 1-2: new full speed USB device using ohci_hcd and address 6
Jan 22 19:31:24 localhost kernel: [37104.302246] usb 1-2: configuration #1 chosen from 1 choice
Jan 22 19:31:24 localhost kernel: [37104.305229] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
Jan 22 19:40:40 localhost kernel: [37659.771838] usb 1-5: new full speed USB device using ohci_hcd and address 7
Jan 22 19:40:40 localhost kernel: [37659.984673] usb 1-5: configuration #1 chosen from 1 choice
Jan 22 19:40:40 localhost kernel: [37659.987653] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
```

---

### Post by owen5 on 2008-01-25
I have the same problem.

lsmod, lsusb, and dmesg all report that the webcam/drivers are loaded and detected, but camorama, cheese, and xawtv all report that no device is present.


I believe theres a problem connecting the gspca driver to the device node video0, perhaps major/minor number error?  but I have no idea how to fix that.  Currnetly, major node is 81, minor is 0.

---

### Post by zanoman on 2008-01-26
I never heard about major and minor node, what is it?

I found the bug for me, try to start your webcam viewer (camorama for instance) as root:
gksu camorama

if it works, it's a permission problem, like me:
your /dev/video0 is owned by "root" and "video" group, but "video" doesn't exists as a group (or at least, it's not listed in groups)!!

I created a "video" group, made my user part of it, restarted (necessary to apply new group creation and users) and it worked!!

But weird enough, after a few shutdown (to save energy at night), video group had disappeared!
Almost all groups present in /dev don't exist in the groups I can manage as root!

Do I miss something or there's a big glitch in groups management in Gutsy?

I also had problems when I plugged 2 webcams (/dev/video0 and /dev/video1), even seeing just one of them (/dev/video0) doesn't work.

---

### Post by zanoman on 2008-01-26
I finally tried by plugging one webcam THEN another one.
The first one I see is ok, but the second doesn't work (a green dot going left-right tries to make the video at snail speed).
So forget about having more than one webcam with the same gpsca driver .

---

### Post by owen5 on 2008-01-27
The major node number  is used by the kernel to identify which device files go with which driver.  The minor is used by the driver to distinguish different devices.```
  ls -l /dev/video0
``` outputs something like 

```
crw-rw---- 1 root video 81, 0 2008-01-27 00:57 /dev/video0
```

in my case, /dev/video0 is the node, 81 is the major number and 0 is the minor number.   

Thats about all that I've been able to find out about it, mostly while trying to get my webcam to work, so I don't know how to make sure all the numbers match what they should be.


Trying to run as root didn't work for me, but thanks for posting your solution

---

### Post by Tatty on 2008-02-11
Well after more research I discovered that the gspca driver doesnt appear to be loading.

So i tried to manually load it with sudo modprobe gspca, but that simply returned an error:

```
tatty@MythServer:~$ sudo modprobe gspca
FATAL: Error inserting gspca (/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Anyone with any ideas?

---

### Post by Tatty on 2008-02-11
after reading lots of websites on the above error, it appears that it is most often caused by conflicting kernel headers and images.

uname -r shows that i am running kernel version 2.6.22-14

In synaptic that image and all its headers are installed fine, but I also have linux-image-2.6.22-16-generic installed as well - could this be causing a problem?

I dont understand how the kernel works too well so i am hesitant to go ahead and mess with it without advice...

---

