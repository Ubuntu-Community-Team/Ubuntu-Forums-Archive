---
title: "Logitech QuickCam Express"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by BlueNoteMKVI on 2006-01-25
I'm trying to get my Logitech QuickCam express working under Linux, it's giving me fits.

Using the lsusb command, I see that I have:
```
Bus 001 Device 003: ID 046d:0870 Logitech, Inc. QuickCam Express
```

When I connect it, it's recognized and a module is loaded.  Here's the relevant portion of dmesg:
```
Jan 25 14:22:35 localhost kernel: [4294710.518000] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.3 $Date: 2005/04/15 19:32:49 $)
Jan 25 14:22:35 localhost kernel: [4294710.518000] quickcam: Kernel:2.6.12-10-386 bus:1 class:FF subclass:FF vendor:046D product:0870
Jan 25 14:22:35 localhost kernel: [4294710.559000] quickcam: Sensor VV6410 detected
Jan 25 14:22:35 localhost kernel: [4294710.577000] quickcam: Registered device: /dev/video0
Jan 25 14:22:35 localhost kernel: [4294710.577000] usbcore: registered new driver quickcam
Jan 25 14:23:40 localhost kernel: [4294781.360000] quickcam: frame lost
Jan 25 14:23:40 localhost kernel: [4294781.520000] quickcam: frame lost
Jan 25 14:23:40 localhost kernel: [4294781.680000] quickcam: frame lost
Jan 25 14:23:40 localhost kernel: [4294781.840000] quickcam: frame lost
Jan 25 14:23:40 localhost kernel: [4294782.000000] quickcam: frame lost
Jan 25 14:23:40 localhost kernel: [4294782.054000] quickcam: frame lost
Jan 25 14:45:24 localhost kernel: [4296086.153000] quickcam: Control URB error -2

```

I try running xawtv (or any other camera software) and I see a black box where the image should be.  Running xawtv from a terminal gives me this output:

```
chris@coltrane:/var/log$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.12-10-386)
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_QUERYCAP(driver="";card="";bus_info="";version=0.0.0;capabilities=0x0 []): Unknown error 515
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOCSYNC(int=0): Invalid exchange
ioctl: VIDIOCMCAPTURE(frame=0;height=32;width=48;format=15): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=32;width=48;format=9): Invalid argument
ioctl: VIDIOCSYNC(int=0): Invalid exchange
ioctl: VIDIOCSYNC(int=0): Invalid exchange
ioctl: VIDIOCSYNC(int=0): Invalid exchange
ioctl: VIDIOCSYNC(int=0): Invalid exchange
no way to get: 384x288 32 bit TrueColor (LE: bgr-)

```

The camera itself is fine, I pulled it from a Windows box on the other side of the room where it was working just fine.  It also runs on my old Windows laptop.  I've tried several USB ports and they all give me the same results, even in ports that had other things successfully connected.

Where should I be looking next?

Where should I look to get this thing working?

---

### Post by linuxden on 2006-01-25
[http://ubuntuforums.org/showthread.php?t=119596&highlight=webcam](http://ubuntuforums.org/showthread.php?t=119596&highlight=webcam)

Have a look at that...

---

### Post by BlueNoteMKVI on 2006-01-25
Thanks for the link.  That's a different model of camera completely, I don't think it even uses the same driver.  I'm downloading a liveCD of Ubuntu now to see if the camera will work under Gnome.

Here's some more information that might be useful:

-Kernel version:
```
chris@coltrane:~$ uname -r
2.6.12-10-386

```

-Running an AMD64 processor, but 32 bit software (64 was too buggy).  I do still have Kubuntu AMD64 installed on another partition so maybe I'll try it one of these days.

-Currently running Kubuntu 5.10 with all the latest updates (as of today, 1/25/06)

---

### Post by linuxden on 2006-01-25
my logitech quickcam express works using that thread...

have you just tried pluging it in and then following the setup from gnome-meeting? It worked for me 1st time round... How ever i havent tried using my cam with someone... i dont use the cam anymore these days...

---

### Post by BlueNoteMKVI on 2006-01-25
GnomeMeeting has a million dependencies that have to be installed if you're not running Gnome already (which would be me).  I'll give it a whirl from the liveCD and see if it works there.

---

### Post by BlueNoteMKVI on 2006-01-30
I booted into an Ubuntu liveCD (5.10) and tried GnomeMeeting.  My camera was detected and modules were loaded, but the camera image was nothing but a green screen.

Anyone have an idea to try next?

---

