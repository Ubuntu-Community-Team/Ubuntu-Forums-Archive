---
title: "Creative Live Ultra! Webcam on Ubuntu?"
date: 2008-05-24
forum: Hardware
---

### Post by m0u53m4t on 2008-05-24
Anyone got a clue how I could get this running?

My lsusb returns:

```
Bus 005 Device 008: ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra

```

So its definitely recognized, but still not showing up in skype...

The last few lines of dmesg are:

```
[14720.229812] usb 5-8: USB disconnect, address 5
[16334.178770] usb 5-8: new high speed USB device using ehci_hcd and address 8
[16334.319768] usb 5-8: configuration #1 chosen from 1 choice
[16374.937622] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

```

Any ideas?

---

### Post by guleblanc on 2008-07-11
I just saw this.  I'm struggling with a creative live! im webcam myself, though it has a different product id.  It looks to me here as if the driver is not installed.  This is what dmesg looked like before I installed the driver.

You might look at either gspca or else ov51x.  You will have to google to find them, though.  Installation of the latter is pretty easy.

---

### Post by fonkamex on 2009-11-28
Hi!

I have a creative nx ultra with the same problem, but now is solved with help from skype forums here:


[http://forum.skype.com/index.php?showtopic=252681&st=0](http://forum.skype.com/index.php?showtopic=252681&st=0)

good luck!

---

### Post by GaryUK on 2009-11-28
> **fonkamex said:**
> Hi!

I have a creative nx ultra with the same problem, but now is solved with help from skype forums here:


[http://forum.skype.com/index.php?showtopic=252681&st=0](http://forum.skype.com/index.php?showtopic=252681&st=0)

good luck!

Hi,

I have exactly the same webcam and I can tell you from experience (and I have been looking for 2 years) that this webcam is not supported in Ubuntu as far as I am aware and this skype post will not help you.

Try searching on "Creative Webcan Live Ultra" and you may get some more info specific to your camera (this is what you need as the chip in your camera is totally different to the others mentioned in this thread).

I found most threads on the subject ended up here:

[http://gkall.hobby.nl/sq930x.html](http://gkall.hobby.nl/sq930x.html)

And I seem to remember that someone was, at one time, offering money for someone to work out how to get this webcam to work in Ubuntu but to no avail...

Sorry cannot be more help...

Gary.

---

### Post by Raiser on 2010-01-24
> **GaryUK said:**
> Hi,

I have exactly the same webcam and I can tell you from experience (and I have been looking for 2 years) that this webcam is not supported in Ubuntu as far as I am aware and this skype post will not help you.

Try searching on "Creative Webcan Live Ultra" and you may get some more info specific to your camera (this is what you need as the chip in your camera is totally different to the others mentioned in this thread).

I found most threads on the subject ended up here:

[http://gkall.hobby.nl/sq930x.html](http://gkall.hobby.nl/sq930x.html)

And I seem to remember that someone was, at one time, offering money for someone to work out how to get this webcam to work in Ubuntu but to no avail...

Sorry cannot be more help...

Gary.

Hello,

The driver sq930x in the page you given works with kernel 2.6.17 - 2.6.23. So, I have the same webcam (041e:403c) and managed to make the device recognized by using this driver. The dmesg output is as below:

```
[ 4337.031543] sq930-1: sq930_control_dma: read 001f/0000 8
[ 4337.032252] sq930-1: Product: USB 2.0 PC camera 
[ 4337.032256] sq930-1: Device model: Creative WebCam Live! Ultra
[ 4337.032259] sq930-1: Chip: 930b FW: 12
[ 4337.032263] sq930-1: sq930_control_dma: write 3101/00f0 0
[ 4337.049678] sq930-1: Sensor: Sharp LZ24BP CCD
[ 4337.049690] sq930-1: sq930_control_dma: write 5401/0003 21
[ 4337.057678] sq930-1: sq930_control_dma: write 0305/fd00 0
[ 4337.061676] sq930-1: sq930_control_dma: write 0105/ff00 0
[ 4337.117651] sq930-1: sq930_control_dma: write 0105/fc00 0
[ 4337.129650] sq930-1: sq930_control_dma: write 0105/fe00 0
[ 4337.141633] sq930-1: sq930_control_dma: write 0105/ff00 0
[ 4337.153641] sq930-1: sq930_control_dma: write 0105/fb00 0
[ 4337.257608] sq930-1: registered as video0
``` 

I tried a program called motion and the led on the cam is on. But the frame it captured is a blank screen. Also I tried the camorama and the output is like this:

```
VIDIOCGCAP
device name = sq930 USB Camera #2
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 640
max height = 480
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 320
height = 240
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 320
height = 240
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 0
hue = 0
colour = 0
contrast = 0
whiteness = 0
colour depth = 24

VIDIOCGMBUF
mb.size = 2097152
mb.frames = 2
mb.offset = 1048576
Unable to capture image (VIDIOCMCAPTURE).
```

What am I doing wrong? Is there anybody got an image from this camera?

Thanks.

---

