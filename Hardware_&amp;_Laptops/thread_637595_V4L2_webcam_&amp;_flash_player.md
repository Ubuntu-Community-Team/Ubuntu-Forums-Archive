---
title: "V4L2 webcam &amp; flash player"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by olavjunior on 2007-12-11
So do I get this right: there's no way of getting to use the built in webcam on my hp dv2130 to work with flash on web-pages cause flash player linux doesn't support V4L2 drivers?

---

### Post by Kheops_74 on 2008-01-23
Do you find an answer to your question?  I tried these sites [bad links removed] and it didn't work.

Thanks

K

---

### Post by olavjunior on 2008-01-24
I don't think it's possible, no... Webcameras is a troubled issue in Linux.

---

### Post by billih on 2008-03-19
Try this for time being...until Adobe comes with a clean solution. It worked for me:
[http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html](http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html)

---

### Post by kung fu buntu on 2008-03-24
I can't get it to work...
I posted there 2 messages... but will post them here as well


Before any vloopback and flashcam I have:
crw-rw---- 1 root video 81, 0 2008-03-23 20:50 /dev/video0
crw-rw---- 1 root video 81, 1 2008-03-24 03:20 /dev/video1

video0 is my tv card and video1 is my Logitech Quickcam Fusion.

#modprobe vloopback inminor=9
#ls -l /dev/video*
crw-rw---- 1 root video 81, 0 2008-03-23 20:50 /dev/video0
crw-rw---- 1 root video 81, 1 2008-03-24 03:33 /dev/video1
crw-rw---- 1 root video 81, 2 2008-03-24 03:34 /dev/video2
crw-rw---- 1 root video 81, 9 2008-03-24 03:34 /dev/video9

#dmesg
usb 7-2: new high speed USB device using ehci_hcd and address 5
usb 7-2: configuration #1 chosen from 1 choice
uvcvideo: Found UVC 1.00 device [unnamed] (046d:08ca)
vloopback: Video4linux loopback driver v1.1.1
vloopback: Loopback 0 registered, input: video9,output: video2

I start flashcam as user:
$./flashcam -d /dev/video1 -l /dev/video9
Input device: /dev/video1
Size = 160 x 120

I remind that /dev/video1 is my webcam.

I try to use your flash application to test the webcam and the list of devices there is the following:
- none
- BT878 video (my tv card)
- UVC camera
- 2, undefined,

I select the last one, which according to you should say "Video loopback 0 output" and this is what I get:

#dmesg
ioctl32(operapluginwrap:7965): Unknown cmd fd(4) cmd(803c7601){00} arg(ffa66b68) on /dev/video2
ioctl32(operapluginwrap:7965): Unknown cmd fd(4) cmd(800e7606){00} arg(ffa66ba6) on /dev/video2
ioctl32(operapluginwrap:7965): Unknown cmd fd(4) cmd(80207609){00} arg(ffa6699c) on /dev/video2
ioctl32(operapluginwrap:7965): Unknown cmd fd(4) cmd(803c7601){00} arg(ffa67b78) on /dev/video2
ioctl32(operapluginwrap:7965): Unknown cmd fd(4) cmd(800e7606){00} arg(ffa67bb6) on /dev/video2
ioctl32(operapluginwrap:7965): Unknown cmd fd(4) cmd(80207609){00} arg(ffa67abc) on /dev/video2
ioctl32(firefox-bin:8279): Unknown cmd fd(60) cmd(803c7601){00} arg(ff860fe8) on /dev/video2
ioctl32(firefox-bin:8279): Unknown cmd fd(60) cmd(800e7606){00} arg(ff861026) on /dev/video2
ioctl32(firefox-bin:8279): Unknown cmd fd(60) cmd(80207609){00} arg(ff860e1c) on /dev/video2
ioctl32(firefox-bin:8279): Unknown cmd fd(61) cmd(803c7601){00} arg(ff862128) on /dev/video2
ioctl32(firefox-bin:8279): Unknown cmd fd(61) cmd(800e7606){00} arg(ff862166) on /dev/video2
ioctl32(firefox-bin:8279): Unknown cmd fd(61) cmd(80207609){00} arg(ff86206c) on /dev/video2

As you can see, I tried 2 different browsers and they both fail.

My linux system:
Linux stardust 2.6.21-2-amd64 #1 SMP





I have now tried to compile and run flashcam in the chrooted system and this is what I get:

$./flashcam -d /dev/video1 -l /dev/video9
ioctl VIDIOCSPICT
Error[Invalid argument]

#dmesg
ioctl32(flashcam:11455): Unknown cmd fd(3) cmd(400e7607){00} arg(ffcc2b3a) on /dev/video9

I no longer know if flashcam should run in chroot or not. But results seemed to be better in 64bits.
In 32bits chroot, flashcam halts at open_loop()

If it matters, I can run lucvview either in jpg or yuv capture modes.

And I checked Debian site [http://merkel.debian.org/~jurij/](http://merkel.debian.org/~jurij/) for the kernel config and it says the kernel supports V4L1, V4L1_COMPAT and V4L2.


I'm out of ideas... :(



Any help?
Thank you very much.

---

### Post by jaiball on 2008-03-25
I used the above link(swifthumors)  and got my webcam to work, definitely the best(only?) workaround to get v4l2 webcams to play nice with Flash 9. 

J

---

### Post by kung fu buntu on 2008-03-25
I got it working with the author's help.

The vloopback code required a fix to work with amd64 systems.

---

### Post by imon9 on 2008-03-30
as many linux user notice, flash perviously only supported v4l webcam, while most of the new distro is using v4l2 as standard driver and v4l2 is also the standard driver embedded in the kernel.

So, most of us who has new webcam (especially those build-in) are using v4l2 driver and dont have the opportunity to use webcam based flash sites like:
[www.mebeam.com](www.mebeam.com)
[www.flixn.com](www.flixn.com)


NOW YOU CAN!!!

a developer wrote a loopdriver for webcam, you can get it from his website:
[http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/)

---

