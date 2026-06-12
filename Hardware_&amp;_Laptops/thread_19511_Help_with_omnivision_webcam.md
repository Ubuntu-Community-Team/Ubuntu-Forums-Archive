---
title: "Help with omnivision webcam"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by ahood on 2005-03-12
I could use a bit of help with an omnivision webcam that uses the OV7620AE sensor.

**System Specs**
OS Distribution: Ubuntu (Warty)
Linux version: 2.6.8.1
CPU: AMD Athlon
CPU Speed: 2200+ (1.8 Ghz)
USB: ohci_hcd

**Modules/Packages Installed and Running**
video4linux
ovcamchip
videodev
ov511
Gnomemeeting
Streamer
Camstream
Xawtv

**Commands Used**
sudo modprobe videodev
sudo modprobe ovcamchip
sudo modprobe ov511

**The Problem**
It seems that video4linux does not see the webcam because no device is listed in Gnomemeeting (wizard or preferences). No video either in xawtv, camstream or streamer.

I get a clue as to the problem when I start xawtv with the following parameters 
xawtv -noxv 

This is xawtv-3.93, running on Linux/i686 (2.6.8.1-4-386)
can't open /dev/video0: Function not implemented
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Function not implemented
v4l2: open /dev/video0: Function not implemented
v4l: open /dev/video0: Function not implemented
no video grabber device available

Note that the device manager does recognize the USB cambera as an omnidivision device. 

I have come to the conclusion that I have to point the video0 device to video4linux. But how do I do this? Maybe there is something else I need to do?

Any suggestion or help will be greatly appreciated.

With kind regards,

Al Hood

---

### Post by Staesys on 2005-05-21
I have much the same problem in Hoary. If someone could help us figure this problem out, I'd be very gratefull!

-Paul

---

### Post by ozt on 2005-06-27
I haven't yet made my cam work, but run 'dmesg' and see if you get "drivers/usb/media/ov511.c: No decompressor available"

The only problem with that is that the decompressor is built in and enabled ( "Jun 27 11:55:41 localhost kernel: drivers/usb/media/ov511.c: Compression required with OV518...enabling" )

I doubt this will help.. .But at least shed some light over it...

---

### Post by yyagol on 2005-08-03
I try to make it work under Fedora as well but so far nothing
 ](*,)

---

### Post by foolsh on 2005-11-13
[http://home.insightbb.com/~foolsh/]("http://home.insightbb.com/~foolsh/")

---

