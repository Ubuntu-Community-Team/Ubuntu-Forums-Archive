---
title: "Webcam wont work at all."
date: 2008-08-30
forum: Hardware
---

### Post by pankirk on 2008-08-30
I bought a logitech quickCam connect (e 2500) today and nothing I do seems to make it work well. On the back it says "QC Connect 960-000217" just above the bar code but thats about all I can find about this camera. I searched all over google and yahoo, but no help. So how can I get this working? Thanks. I'm using Ubuntu 8.04, if it's needed.

---

### Post by Cresho on 2008-08-30
post your lspci here.  you get the info in terminal.  type lspci and hit enter.  what your looking for is your cam.  we will use this as a refference but do not use the instructions just yet.  we need to see if your post has any relevent info. [http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)

---

### Post by Crafty Kisses on 2008-08-30
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2) if working with the settings does not work or help.
Post the results of the command > lsusb

---

### Post by Cresho on 2008-08-30
> **Codename said:**
> You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2) if working with the settings does not work or help.
Post the results of the command > lsusb

ya ignore my top post, I meant lsusb .  this guy is correct.

---

### Post by pankirk on 2008-08-30
Okay okay, heres lsub:

> 
patrick@patrick-desktop:~$ lsusb
Bus 002 Device 006: ID 1687:0163  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 007: ID 046d:c315 Logitech, Inc. 
Bus 001 Device 010: ID 046d:089d Logitech, Inc. 
Bus 001 Device 009: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 001 Device 001: ID 0000:0000  
patrick@patrick-desktop:~$ 


I'm guessing that one of these is the USB webcam:
> 
Bus 001 Device 007: ID 046d:c315 Logitech, Inc.
Bus 001 Device 010: ID 046d:089d Logitech, Inc. 


because this is my wireless mouse:
> 
Bus 001 Device 008: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver


and the others are bluetooth, ect...

---

### Post by pankirk on 2008-08-30
It seems i got the webcam working for the website "stickam.com" but I still cant seem to figure out how to get it working in cheese? Can anyone help get it set up to work with cheese? I'm pretty sure i'd rather have it working in cheese than stickam.com

---

### Post by scalywag66 on 2008-08-30
Same problem but for different webcam

I have some cheap PoS, the ever so amazing Dynex DT-CAM !!! w00t!!! \o/

It was working ok at first on Windows, but then came a known problem with DT-CAM in which it went from showing actual picture to just showing a black screen.  The mic would work and all, but video capabilities were hindered somehow.  

Come Ubuntu, I install the proposed software Camorama and whatnot, and the error I get is

[IMG]http://img120.imageshack.us/img120/6445/screenshoterrorcamoramata8.png[/IMG]

typing "lsusb" in Root Terminal gives this output

> Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 0c45:60fb Microdia 
Bus 001 Device 007: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000what have I done wrong?

---

### Post by Cresho on 2008-08-30
i don't have cheese but I can sort of guide you.  in terminal, type cheese --help

post the output here.  I am curious to see what options it gives you.

---

### Post by scalywag66 on 2008-08-30
Cheese just gives me the colored bars and the one static screen, what now?

---

### Post by Cresho on 2008-08-30
do a ls -l /dev/dvb/adapter0

or a ls -l /dev/video0

replace the 0 with 0, 1, 2, 3

i am curios to see where your video adaptor is at.

output should say something like 

crw-rw----+ 1 root video 212, 4 2008-08-30 00:29 demux0
crw-rw----+ 1 root video 212, 5 2008-08-30 00:29 dvr0
crw-rw----+ 1 root video 212, 3 2008-08-30 00:29 frontend0
crw-rw----+ 1 root video 212, 7 2008-08-30 00:29 net0


of course my output is my video card output.  it should work similar to the cam

---

### Post by pankirk on 2008-08-30
Okay, it says:
> 
patrick@patrick-desktop:~$ ls -l /dev/video0
crw-rw---- 1 root video 81, 0 2008-08-30 11:24 /dev/video0
patrick@patrick-desktop:~$ 



---

### Post by IntuitiveNipple on 2008-08-30
Let us have the output of:
```

udevinfo --query=all --name=/dev/video0 --attribute-walk

```

---

### Post by pankirk on 2008-08-30
Sure thing, here you go:

> 
patrick@patrick-desktop:~$ udevinfo --query=all --name=/dev/video0 --attribute-walk

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:0a.0/usb2/2-6/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{dev}=="81:0"
    ATTR{name}=="GSPCA USB Camera"
    ATTR{stream_id}=="JPEG"
    ATTR{model}=="Logitech QuickCam E2500"
    ATTR{pictsetting}=="force_rgb=0, gamma=1, OffRed=0, OffBlue=0, OffGreen=0, GRed=256, GBlue=256, GGreen= 256 "

  looking at parent device '/devices/pci0000:00/0000:00:0a.0/usb2/2-6/video4linux':
    KERNELS=="video4linux"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0a.0/usb2/2-6':
    KERNELS=="2-6"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:132"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 3"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="25796"
    ATTRS{idVendor}=="046d"
    ATTRS{idProduct}=="089d"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="5"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:0a.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:128"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="89"
    ATTRS{idVendor}=="0000"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="10"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.24-19-generic ohci_hcd"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{serial}=="0000:00:0a.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:0a.0':
    KERNELS=="0000:00:0a.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x036c"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x8223"
    ATTRS{class}=="0x0c0310"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v000010DEd0000036Csv00001043sd00008223bc0Csc03i10"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""



---

### Post by pankirk on 2008-08-30
Yep, there is what happens when I type that code! Any help from anyone? :guitar:

---

### Post by Cresho on 2008-08-30
alt+f2 and type gstreamer-properties and hit enter.

then click on video tab.  under default input, select "test input" and click on test.  If it works, it is a cheese bug and you will need to submit a bug.  I am assuming that this is the only video you have going in.

---

### Post by pankirk on 2008-08-31
Yes, it shows up fine in "gstreamer-properties"... But when starting up gstreamer-properties I get this error:

> 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'


but i'm not sure if it matters because the application starts up and i can test everything fine... Anyway, the webcam works as it should in the application testing.

---

### Post by Cresho on 2008-08-31
those errors are typical.  So what you are saying is you can see the video from the webcam in the gstreamer properties but not in cheese?

If so, then you may need to install the latest packages or build one from source. [http://www.gnome.org/projects/cheese/](http://www.gnome.org/projects/cheese/)

current version from ubuntu is 2.22.3 but they have an unstable version out which is 2.23.9

---

### Post by VMC on 2008-08-31
I have the exact same issues. Everything works just the same as pankirk's. Sometimes the Cheese works sometimes not. the same as Ekiga. The only that constantly works everytime  is LUVCVIEW. Also Skype video testing works everytime.

This message:
udevinfo --query=all --name=/dev/video0 --attribute-walk

Gave me a lot more info, thanks.

---

### Post by pankirk on 2008-08-31
Well, of course I have to buy the web cam that wont work D:. Anyway, your saying if I compild a new one from source it should work?

---

### Post by pankirk on 2008-08-31
Well, I downloaded cheese 2.23.90 and compiled it and now its telling me i dont even have a camera connected but I have one connected and it's working fine in gstream-properties

---

### Post by Cresho on 2008-08-31
Then this is a bug in cheese.  The other guys says that his works sometimes and then sometimes it doesnt.  I am curious to see if his video0 switches to video1 at times?  I had to configure my 2 video cards from being switched around because ubuntu starts them up randomly.

Here is a post fix I did a while back, it could help someone maybee here if video is switching around.  

Im just wondering if  you guys have multiple tv tuner cards.

[http://ubuntuforums.org/showthread.php?t=739824&highlight=tv+time](http://ubuntuforums.org/showthread.php?t=739824&highlight=tv+time)

---

### Post by IntuitiveNipple on 2008-08-31
To solve the naming issue the best (and *recommended*) way to do it is a udev rule.

This works quite simply. When a new device is detected by the kernel it sends a notification that is picked up by udev. The notification contains fields of unique values that udev can use to identify the device.

For each video input device you can create a rule that is tied to these unique values and ensures that a particular device always gets the same /dev/videoX assignment.

If gstreamer or vlc and other applications can *talk* to the camera then it is fine - the camera works.

The issue then is not the 'camera not working' but an application - in this case maybe cheese - 'not working'.

I've just installed and tested cheese here and by default it doesn't talk to a webcam using a V4L2 (Video4Linux version 2) driver but it will find a camera using a V4L (Video4Linux version 1) driver, even when gstreamer-properties Video > Default Input has been configured and tested with both cameras and set with the default device to be the V4L2 camera.

Reading a video device requires two things:
[list]
[*] Access the camera using V4L2 or V4L2 with the V4L1 compatibilty interface (V4L1 was deprecated and removed from the kernel)
[*] Ability to understand a range of chroma formats (the way the picture is encoded for compression)
[/list]
It looks as if cheese, via gstreamer, can't handle some chroma formats.

---

### Post by pankirk on 2008-08-31
But in gstreamer it tells me that it's v4l not v4l2

---

### Post by IntuitiveNipple on 2008-08-31
> **pankirk said:**
> But in gstreamer it tells me that it's v4l not v4l2
Is the camera also listed as a V4L2 device?

There are three situations to deal with whilst older V4L1 drivers and programs are being updated to support V4L2:
[list=a]
[*] driver only supports V4L1
[*] driver supports V4L2, but also supports the V4L1 compatibility interface
[*] driver only supports V4L2
[/list]

If the camera is listed as both V4L1 and V4L2 then its driver will be a type (b) in the list above.

If it only lists as V4L1 then it is type (a).

If cheese can't support it then that is because it doesn't have the code to support the particular chroma (video format) being delivered by the driver.

---

### Post by IntuitiveNipple on 2008-08-31
> **Cresho said:**
> I had to configure my 2 video cards from being switched around because ubuntu starts them up randomly.

Here is a post fix I did a while back, it could help someone maybee here if video is switching around.


Cresho, here's the best way to deal with video device naming. Create a udev rule similar to this:
```

SUBSYSTEM=="video4linux", BUS=="usb", SYSFS{idVendor}=="054c", SYSFS{idProduct}=="0154", NAME="video5"

```
It is saved as "**/etc/udev/rules.d/25-name-video-devices.rules**" (requires sudo/gksudo privileges to write the file).

Take notice of == being used to ***test*** existing values passed through udev, and = being used to ***assign*** a new value. 

In this case it is tied to a USB device with the PCI ID 054C:0154 (A Sony Playstation EyeToy camera) using a match with idVendor and idProduct. It will be given the name **video5** which will end up as /dev/video5.

See the udev manual page for more details:
```

man udev

```
To identify the values being passed through udev you would run the udevmonitor just before plugging the device in:
```

sudo udevmonitor --environment | tee video-udev.log

```
This command writes the output to screen but also saves it to the file "video-udev.log" since there can sometimes be a lot of output that needs examining carefully to find the correct attributes to use to recognise the device.

Here's an extract of a part of the log that I used in this example:
```

UEVENT[1220172826.231984] add      /devices/pci0000:00/0000:00:1d.1/usb2/2-1 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb2/2-1
SUBSYSTEM=usb
MAJOR=189
MINOR=131
DEVTYPE=usb_device
DEVICE=/proc/bus/usb/002/004
PRODUCT=54c/154/100
TYPE=0/0/0
BUSNUM=002
DEVNUM=004
SEQNUM=3875

...

UEVENT[1220172826.711537] add      /devices/pci0000:00/0000:00:1d.1/usb2/2-1/video4linux/video1 (video4linux)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/video4linux/video1
SUBSYSTEM=video4linux
MAJOR=81
MINOR=1
SEQNUM=3879

```
Notice how PRODUCT contains the PCI device ID without leading zeros.

If it is a built-in device that can't be unplugged then you identify the driver that handles it, and unload the driver, then reload it with udevmonitor running. In the case of the EyeToy camera here, the driver is ov51x-jpeg, so (if it were built-in) I'd do:
```

sudo modprobe -r ov51x-jpeg
sudo udevmonitor --environment | tee video-udev.log&
sudo modprobe ov51x-jpeg
fg

```
Now press Ctrl+C to interrupt udevmonitor and return to the command-line.

**Note:** There will be some output as soon as udevmonitor starts but ignore it and go ahead typing the next command even though the input prompt appears to be missing. The "&" at the end of the udevmonitor command puts the process into the background and returns to the command-line immediately.

---

### Post by VMC on 2008-08-31
> **IntuitiveNipple said:**
> ...
It is saved as "**/etc/udev/rules.d/25-name-video-devices.rules**" (requires sudo/gksudo privileges to write the file).
...

Thank you for this post. I've read before about using the "rules.d" procedure. Where did you get the '25' from?

I think this all boils down to getting the right webcam in the first place. Mine is a Logitech ID:046d:09c1, which only works using V4L2. 

I'm not trying to hijack this topic but just keep it open. I've learned more from this topic than all the others combined. Sadly Windows XP-SP3 works flawless with this webcam. Which just tells me it's a driver issue. Nothing to do with Windows per say.

---

### Post by IntuitiveNipple on 2008-08-31
> **VMC said:**
> Thank you for this post. I've read before about using the "rules.d" procedure. Where did you get the '25' from?

Rules files have a precedence. Rules often need to be executed in a particular order. Numbering is a straight-forward way of making the sequence of the rules clear to computer and human alike.
I chose 25 so that it comes just after the system's standard naming rules (20-*) and before any other rules that might want to claim the device and give it a name or otherwise affect it. Also, using a number in the 20-29 range infers, from the system rules, that it is a naming rule.

> **VMC said:**
> 
I think this all boils down to getting the right webcam in the first place. Mine is a Logitech ID:046d:09c1, which only works using V4L2. 

Forget the *only*. The **only** video support in Linux is now V4L2 - as I said before, V4L1 was deprecated and removed over a year ago now I think. There was warning of the removal for a year before that.

Device-driver maintainers are expected to update drivers to ensure they remain compatible with the kernel. Unfortunately there are still a fair number that haven't managed that, one of the headaches of drivers that aren't part of the kernel itself.

However, the biggest issue until very recently has been that the application programmers haven't been updating their camera interface libraries and functions to use V4L2.

> **VMC said:**
> 
I'm not trying to hijack this topic but just keep it open. I've learned more from this topic than all the others combined. Sadly Windows XP-SP3 works flawless with this webcam. Which just tells me it's a driver issue. Nothing to do with Windows per say.
The issue is the device manufacturers and chip-set providers who don't see the small percentage of Linux users as worth supporting with drivers, and won't/don't provide open documentation for others to do so either.

Windows went through a period of about 4 years with a similar change in kernel APIs from the old VFW (video for windows) to the WDM (Windows device management). The thing with Windows is, it has the monopoly to force the manufacturers to update the drivers immediately otherwise they'd noticeably lose sales. There was still about a year where support for video devices was like rolling a dice, though.

---

### Post by Cresho on 2008-08-31
> **IntuitiveNipple said:**
> Cresho, here's the best way to deal with video device naming. Create a udev rule similar to this:
```

SUBSYSTEM=="video4linux", BUS=="usb", SYSFS{idVendor}=="054c", SYSFS{idProduct}=="0154", NAME="video5"

```
It is saved as "**/etc/udev/rules.d/25-name-video-devices.rules**" (requires sudo/gksudo privileges to write the file).

Take notice of == being used to ***test*** existing values passed through udev, and = being used to ***assign*** a new value. 

In this case it is tied to a USB device with the PCI ID 054C:0154 (A Sony Playstation EyeToy camera) using a match with idVendor and idProduct. It will be given the name **video5** which will end up as /dev/video5.

See the udev manual page for more details:
```

man udev

```
To identify the values being passed through udev you would run the udevmonitor just before plugging the device in:
```

sudo udevmonitor --environment | tee video-udev.log

```
This command writes the output to screen but also saves it to the file "video-udev.log" since there can sometimes be a lot of output that needs examining carefully to find the correct attributes to use to recognise the device.

Here's an extract of a part of the log that I used in this example:
```

UEVENT[1220172826.231984] add      /devices/pci0000:00/0000:00:1d.1/usb2/2-1 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb2/2-1
SUBSYSTEM=usb
MAJOR=189
MINOR=131
DEVTYPE=usb_device
DEVICE=/proc/bus/usb/002/004
PRODUCT=54c/154/100
TYPE=0/0/0
BUSNUM=002
DEVNUM=004
SEQNUM=3875

...

UEVENT[1220172826.711537] add      /devices/pci0000:00/0000:00:1d.1/usb2/2-1/video4linux/video1 (video4linux)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/video4linux/video1
SUBSYSTEM=video4linux
MAJOR=81
MINOR=1
SEQNUM=3879

```
Notice how PRODUCT contains the PCI device ID without leading zeros.

If it is a built-in device that can't be unplugged then you identify the driver that handles it, and unload the driver, then reload it with udevmonitor running. In the case of the EyeToy camera here, the driver is ov51x-jpeg, so (if it were built-in) I'd do:
```

sudo modprobe -r ov51x-jpeg
sudo udevmonitor --environment | tee video-udev.log&
sudo modprobe ov51x-jpeg
fg

```
Now press Ctrl+C to interrupt udevmonitor and return to the command-line.

**Note:** There will be some output as soon as udevmonitor starts but ignore it and go ahead typing the next command even though the input prompt appears to be missing. The "&" at the end of the udevmonitor command puts the process into the background and returns to the command-line immediately.

I was just wondering if your post also cover device boot priority or better, yet, with 2 tv cards, which one if forced to use video0 at boot?  This will be very usefell when I add a cam to my pc.  I have one but I'm looking for better.  My problem was that my 2tv cards, 1 webcam was fighting over video0 and randomized "take-over" of video0 at boot.  this was evidenced with tv time. so I then created this thread back then. [http://ubuntuforums.org/showthread.php?t=739824&highlight=kworld](http://ubuntuforums.org/showthread.php?t=739824&highlight=kworld) as well as this [http://ubuntuforums.org/showthread.php?t=752341](http://ubuntuforums.org/showthread.php?t=752341) which lead me to creat e "force executable command" here tvtime --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC


these commands or the scripts i put up use transcode and force tvtime to do what I wanted.  I can record current channel with one button from tvtime or stop recording.  NOW to get back with cheese.

I was hoping this method or if cheese had an implimentation of forcing video to a certain device but we now know it is a bug or a not so compatible webcam or also, what v4l version is its prefference.

---

### Post by IntuitiveNipple on 2008-08-31
> **Cresho said:**
> I was just wondering if your post also cover device boot priority or better, yet, with 2 tv cards, which one if forced to use video0 at boot?  This will be very usefell when I add a cam to my pc.

That is precisely what udev rules are good for. First you identify the unique attributes of each device, then you create a rule similar to my example above, one rule for each device. The rules can all be in one file.
When the system starts each device discovery causes the same udev rules to be processed as when a device is inserted later.

> **Cresho said:**
> 
...if cheese had an implimentation of forcing video to a certain device but we now know it is a bug or a not so compatible webcam or also, what v4l version is its prefference.
The issue with this camera and cheese appears to be cheese lacking support for the chroma (video-format) output by the camera. It *is* possible to write a gstreamer pipeline to transcode from the camera drivers chroma output to one cheese understands.

From what I can gather from my brief investigation, cheese uses whatever the gstreamer default device is, without paying attention to whether the device is V4L2 or V4L1, so configuring the default device in gstreamer-properties is required if there is more than one video device in the system.

---

### Post by pankirk on 2008-08-31
So, how will this make my web cam work with cheese?

---

### Post by keplerspeed on 2008-09-01
Ive had a similar issue with my logitech webcam. I use the gspca driver. It seems like both scalywag66 and pankirk dont have the driver for their cam. I think the gspca driver works for a lot of cams, but it shoudl be install already. Otherwise, have a search for the correct driver, and make sure the module is loaded by:

sudo modprobe {module name}

my issue is that I have a tv tuner using the em28xx driver, and i have to reload each module to make the respective device work... but thats a separate issue.

I used this how to to get my logitech cam working:
[http://ubuntuforums.org/showthread.php?t=651375](http://ubuntuforums.org/showthread.php?t=651375)

my webcam is /dev/video0, and my tv tuner is /dev/dvb/adapter0

---

### Post by pankirk on 2008-09-01
I installed all the drivers, still doesnt work.

---

### Post by IntuitiveNipple on 2008-09-01
> **pankirk said:**
> So, how will this make my web cam work with cheese?
That's the wrong question. The correct question is: "How will this make cheese work with my web-cam?". The problem is with cheese, not the camera.

Does gstreamer-properties show a test preview from the camera? If so, Cheese has a bug in that it doesn't support the chroma output of the camera.

---

### Post by pankirk on 2008-09-01
Ok, I start up gstreamer-properties and then go to the video tab...

there are 4 options for "Default input"
> 
test input
video for linux
video for linux 2
and
custom.

heres what they do when i check them:
**test input**
i get the same image i see when i start up cheese. that's the image with the colorwd bars and in the bottom right corner, a static box.

**video for linux (v4l)**
I test it and it shows: me, sitting there with a frustrated look wanting cheese to work :P

**video for linux 2 (v4l2)**
i click the test button and it shows this:
> Video for Linux 2 (v4l2): Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver.

**custom**
when clicking thte test button it shows this error
> 
Custom: Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver.


Hmm.. maybe theres something with the v4l and v4l2?

---

### Post by IntuitiveNipple on 2008-09-01
> **pankirk said:**
> Ok, I start up gstreamer-properties and then go to the video tab...

there are 4 options for "Default input"

heres what they do when i check them:
**test input**
i get the same image i see when i start up cheese. that's the image with the colorwd bars and in the bottom right corner, a static box.

This is simply the test-pattern generated by software; nothing to do with the camera
> **pankirk said:**
> 
**video for linux (v4l)**
I test it and it shows: me, sitting there with a frustrated look wanting cheese to work :P

:D That proves V4L v1 likes you and is supported by gstreamer.

> **pankirk said:**
> 
**video for linux 2 (v4l2)**
i click the test button and it shows this:


**custom**
when clicking thte test button it shows this error

Confirms the driver in use doesn't support V4L2.

So, the applications you are trying to use don't have support for the camera's video formats (chroma). The camera itself is fine.

---

### Post by VMC on 2008-09-01
> **IntuitiveNipple said:**
> This is simply the test-pattern generated by software; nothing to do with the camera

:D That proves V4L v1 likes you and is supported by gstreamer.


Confirms the driver in use doesn't support V4L2.

So, the applications you are trying to use don't have support for the camera's video formats (chroma). The camera itself is fine.

This is interesting. I thought that V4L2 superseded V4L1 and that V4L1 was depreciated. Mine works the opposite, V4L2 works and V4L1 doesn't. I'm puzzled why he would still have drivers for V4L1?

---

### Post by pankirk on 2008-09-01
I see I see... Well, I guess I will just have to wait until cheese dev's decide to update cheese and make it work with my camera :D unless theres something I can do? Probably not...

---

### Post by IntuitiveNipple on 2008-09-01
> **pankirk said:**
> I see I see... Well, I guess I will just have to wait until cheese dev's decide to update cheese and make it work with my camera :D unless theres something I can do? Probably not...
Report it as a bug to the cheese bug-tracker or forums, so they know.

---

### Post by ElTimo on 2008-09-11
> **pankirk said:**
> It seems i got the webcam working for the website "stickam.com" 

How did you get it to work? I have the exact same model and I can't even get Hardy to figure out that it's a webcam.

Sorry for digging up an old thread, but this has me perplexed, and I just want even the slightest sign of hope that it may work.

---

