---
title: "Problem with Logitech QuickCam Express"
date: 2008-10-04
forum: General Help
---

### Post by xeddog on 2008-10-04
Hi all,

I have been trying to get my camera working in both Ubuntu Hardy, and Ubuntu Intrepid (Beta) with no luck.  I have seen a couple of tutorials on this forum and have gone through them as well as I can.  I have also seen a post or two where people have said that their QuickCam Express worked right out of the box.  The tutorials are old in computer terms (1 to 2 years), and everything in the tutorials seems to be already in place.  I want the camera for Gyachi IM client, but I have tried Camorama and Cheese too.  In all cases, the camera is not detected by the program.  If I run a lsusb command, the camera is detected and I get:

Bus 004 Device 005: ID 046d:0870 Logitech, Inc. QuickCam Express

in the list of devices.  The camera is attached to a USB hub that works for other USB devices including a dvd burner (just for testing), usb stick, and an external usb hard drive.

I know the camera works because I can spin around and connect it to my Windows XP machine and it works perfectly.

Any ideas where I can go from here??

Thanks,

xeddog

---

### Post by mindoms on 2008-10-04
please plug your webcam in. if it is already plugged, plug it out, then in again.
then run the following in a terminal and post the output:
```

dmesg | tail -n15
ls -l /dev/video*

```

---

### Post by xeddog on 2008-10-05
dmesg | tail -n15
[   60.976507] ip_tables: (C) 2000-2006 Netfilter Core Team
[   61.425722] No dock devices found.
[   62.954801] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   62.954809] apm: overridden by ACPI.
[   63.161677] ppdev: user-space parallel port driver
[   63.470852] audit(1223228815.562:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5099 profile="/usr/sbin/cupsd" namespace="default"
[   68.989729] eth0: no IPv6 routers present
[  179.989038] usb 4-5.4.3: new full speed USB device using ehci_hcd and address 6
[  180.081638] usb 4-5.4.3: configuration #1 chosen from 1 choice
[  180.207240] Linux video capture interface: v2.00
[  180.231068] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[  180.231078] quickcam: Kernel:2.6.24-19-generic bus:4 class:FF subclass:FF vendor:046D product:0870
[  180.233496] quickcam: Sensor HDCS-1020 detected
[  180.233916] quickcam: Registered device: /dev/video0
[  180.233945] usbcore: registered new interface driver quickcam



and:

 ls -l /dev/video*
crw-rw---- 1 root video 81, 0 2008-10-05 10:48 /dev/video0


Thanks,

xeddog

---

### Post by mindoms on 2008-10-05
were gonna install another program, just to see if the drivers work.
```

sudo apt-get install xawtv

```

lets try it out (and catch some more information
please post any output
```

v4l-info
xawtv

```

---

### Post by xeddog on 2008-10-05
I  installed xawtv.  It looks like everything installed ok but late in the install process there were some messages about reselecting previously de-selected packages.  But they did appear to install properly.

Here is the v4l-info results:

 v4l-info

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
        name                    : "Logitech QuickCam USB"
        type                    : 0x201 [CAPTURE,SUBCAPTURE]
        channels                : 1
        audios                  : 0
        maxwidth                : 352
        maxheight               : 292
        minwidth                : 32
        minheight               : 32

channels
    VIDIOCGCHAN(0)
        channel                 : 0
        name                    : "Camera"
        tuners                  : 0
        flags                   : 0x0 []
        type                    : CAMERA
        norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
        brightness              : 32768
        hue                     : 32768
        colour                  : 32768
        contrast                : 32768
        whiteness               : 32768
        depth                   : 24
        palette                 : RGB24

buffer
    VIDIOCGFBUF
        base                    : (nil)
        height                  : 0
        width                   : 0
        depth                   : 0
        bytesperline            : 0

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 352
	height                  : 292
	chromakey               : 0
	flags                   : 524288



and as for xawtv results:  

This is what I get before the welcome window opens:

 xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-19-generic)
xinerama 0: 1152x864+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_QUERYCAP(driver="";card="";bus_info="";version=0.0.0;capabilities=0x0 []): Unknown error 515
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOCSYNC(int=0): No space left on device
ioctl: VIDIOCMCAPTURE(frame=0;height=32;width=48;format=15): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=32;width=48;format=9): Invalid argument
v4l: timeout (got SIGALRM), hardware/driver problems?
ioctl: VIDIOCSYNC(int=0): Interrupted system call
v4l: timeout (got SIGALRM), hardware/driver problems?
ioctl: VIDIOCSYNC(int=0): Interrupted system call
v4l: timeout (got SIGALRM), hardware/driver problems?
ioctl: VIDIOCSYNC(int=0): Interrupted system call
v4l: timeout (got SIGALRM), hardware/driver problems?
ioctl: VIDIOCSYNC(int=0): Interrupted system call

When I click the OK button there are no new messages, but I get a new window that just has "???" in the middle of the title bar and a black window.

I will send this now and if anything happens from this point on I will add another reply.  Last time I closed the xawtv window, the machine went waaaay south.  A complete system hang with unresponsive mouse, etc.  The only thing I could see was the Caps Lock and Scroll Lock indicator lights flashing together about once per second.  When I turned off the power and then restarted, the permissions on my .dmrc file are screwed.  I'll fix that too.

Thanks,

xeddog

---

### Post by loell on 2008-10-05
this could be one of the drawbacks of intrepid, since spca5xx driver is already on the kernel and not just as a separate module.

to make the webcam work again, you need to install libv4l on intrepid

it's available at Stéphane's PPA

[https://launchpad.net/~stemp/+archive]("https://launchpad.net/~stemp/+archive")


then preload it

```
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so 
```

then try any webcam application.

---

### Post by xeddog on 2008-10-05
This time when I closed the black window I got two more lines of output for xawtv:

no way to get: 384x288 32 bit TrueColor (LE: bgr-)
Segmentation fault


But at least my machine didn't crap out on me this time.  The first time I closed the window using the icon in the upper LEFT corner of the window.  This time I used the "X" in the upper RIGHT corner, if that should make any difference.

May be worthy of note - I am running Ubuntu 8.04 on an Intel 2.4Ghz processor with 1GB ram.  The video card is knock off of an nVidia GeForce FX 5200 card, and I have the nvidia 173 driver installed.  I am running 1152x864 resolution and a 24 bit color depth.  For devices, I have one internal cd burner, one internal dvd burner, and one external USB dvd burner (connected to a USB port on the motherboard and not to a hub).  Disk drives are both IDE (one 320GB and one 200GB) and other than that there isn't anything special about the machine.

I think I mentioned this in a earlier post, but the camera is connected to a USB 2.0 hub.  The hub is then attached to the other USB port on the motherboard.  Other USB devices work when attached to this hub using the same port.



Thanks again,

xeddog

---

### Post by xeddog on 2008-10-05
Thanks for your reply Loell.  But I guess you just missed my post where I said I am having this issue with Hardy too.  I'll check into it for my Intrepid release though, so thank you.

Side question for you.  I have seen your replies to people regarding Gyachi and you have been VERY helful there.  Is there a particular thread or other forum where I could go to ask some questions about that product, or should I open a thread here??  

Thanks,

xeddog

---

### Post by loell on 2008-10-05
yeah.. :) 

you can ask at
[http://gyachi.sourceforge.net/forums.shtml]("http://gyachi.sourceforge.net/forums.shtml")


in there, you can have direct answers from the developer. :)

---

