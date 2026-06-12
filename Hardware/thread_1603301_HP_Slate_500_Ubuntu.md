---
title: "HP Slate 500 Ubuntu"
date: 2010-10-22
forum: Hardware
---

### Post by serverfarm on 2010-10-22
HP just came out with a tablet pc [http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/321957-321957-64295-3841267-3955550-4332585.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/321957-321957-64295-3841267-3955550-4332585.html)
I am very interested in it, but would like to stay open source... any chance it will work on ubuntu?  How do most tablets connect their touchscreen, a USB HID perhaps?  I would be willing to help develop Ubuntu for the slate 500.  It just sounds like a cool device to me.

---

### Post by Fafler on 2010-10-22
In hardware terms, it's just a generic netbook with touchscreen instead of keyboard.
The touchscreen could give you some trouble, but it seems to be a priority for the developers. And yes, it's a USB device, but not HID. Theres a specific touchscreen driver for that.

---

### Post by serverfarm on 2010-10-22
> And yes, it's a USB device, but not HID. Theres a specific touchscreen driver for that.How good are the Ubuntu touchscreen drivers and its general support of these features?  Even though I run Linux on everything I'm a complete stranger to touch-screens especially on Linux.

Thanks

---

### Post by davim on 2010-10-23
the touch screen seams to be a N-trig and there is a N-trig driver for ubuntu ([https://launchpad.net/~utouch-team/+archive/utouch](https://launchpad.net/~utouch-team/+archive/utouch))

---

### Post by serverfarm on 2010-10-23
Well its great that there is some support for touchscreens,  now if I buy a tablet I'll feel much better about using it with Ubuntu if Windows 7 is as bad as I expect.  Thanks for the help!

---

### Post by bryanagee on 2010-10-25
Will you post on here if/when you actually try Ubuntu on the Slate? I would love to look at these for my field guys; a tablet like this could be realistic for filing out forms, whereas laptops tend to intimidate clients and netbooks are somewhat impracticle.

---

### Post by jkayner on 2011-02-02
We just got the slate for testing at work.  I tried to run 10.10 netbook version from a usb thumbdrive.  I get the following message when booting on it. 

(initramfs) Unable to find a medium containing a live file system

the boot process halts at this point.  Any help is appreciated.

PS i am very noob on ubuntu.

---

### Post by serverfarm on 2011-02-03
Hi, so I was wondering if you could bring up windows and get to the device manager to tell us what type of drive controller was being used?

---

### Post by rothgar on 2011-02-04
> **jkayner said:**
> We just got the slate for testing at work.  I tried to run 10.10 netbook version from a usb thumbdrive.  I get the following message when booting on it. 

(initramfs) Unable to find a medium containing a live file system

the boot process halts at this point.  Any help is appreciated.

PS i am very noob on ubuntu.

I have a HP slate too and am trying with Ubuntu 11.04 alpha 2. I was getting the same error you had and I reformatted my USB drive, downloaded the latest unetbootin, and re-created the USB drive and it will get to grub but Ubuntu won't load. It keeps dumping me off to a command prompt with no error message.

I will follow this thread so if anyone has something they want me to try or get information for I will gladly help.

I am trying to get it to load with the alternate CD too but so far haven't had any luck.

I just tried again with the alternate install CD and it looks like it hangs when it tries to detect the installation "cd". I also tried burning a CD and plugging it in with a USB CD drive but the BIOS would never detect the USB cd drive as a boot device.

---

### Post by serverfarm on 2011-02-04
What kind of command lines does it leave you at?  Is it a real Ubuntu one or some limited thing.  If its a real command line its probably a video card/driver problem.

---

### Post by rothgar on 2011-02-04
It does not appear to detect the broadcom crystal HD for 3d acceleration and then it looks to be a full command line. It sometimes stops at ubuntu@ubuntu prompt and sometimes says> (initramfs) Unable to find a medium containing a live file system

Ubuntu 10.10 loaded for me but the touch screen didn't work, 3d support didn't work, and the login sound kept looping the entire time I tried to use it.

---

### Post by serverfarm on 2011-02-04
Can you post a grep output if any touchscreen is even recognized?  I forgot to add a couple things.  I believe, although I'm not sure the touchscreen was a Wacom one, there is Ubuntu support for it [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom).  If 10.10 worked graphically I would start out with that, do the USB ports work, because than you  could use a mouse and a keyboard to try the Wacom drivers.  As for the logon sound, I'll look into that.

UPDATE:  It's not a permanate solution but System>Administration>Login Screen> Uncheck "Play login sound"

---

### Post by Favux on 2011-02-04
Hi,

A couple of reviews said it was an N-Trig touchsmart digitizer.  I guess some of the early ones said Wacom.

Let's go with N-Trig.  It should work out of the box in Maverick.  The touch is on the evdev driver and the stylus on the Wacom driver.  However if touch is single finger touch it won't work in Maverick.  They goofed and left out single finger touch support.  We have a patch for that.  The other possibility is the match line in 50-wacom.conf doesn't work for you because your digitizer is the first model of the N-Trig with a different product ID.

So is it suppose to be multi-finger touch with a stylus?

Let's look at the output in a terminal of:
```
lsusb
```
and
```
xinput list
```

---

### Post by serverfarm on 2011-02-04
Oh, I've been must have missed that information.  Just as a warning, I do not have an HP Slate, I almost bought one and than I decided to wait.  I'm still happy to help out with this project because if it all works out I'll probably get one too.

---

### Post by rothgar on 2011-02-05
I'll get the output for you guys later this weekend. I will go back to 10.10 just so I can get something to load and then we will work our way to something more functional.

The USB does work (although there is only 1 port). What I have been doing is plugging in a Mac keyboard and using the 2 USB ports on the keyboard for the USB flash drive and mouse.

---

### Post by jkayner on 2011-02-09
ok here is the N-trig info for the tablet:
 
N-Trig DuoSense Digitizer
driver version:  1.26.8.45
Firmware version:  4.7.27.24.15
Software bundle version:  3.46
 
i haven't had a chance to try anything yet but i figured i would post this up in the meantime.

---

### Post by Favux on 2011-02-09
Hi jkayner,

Is that the latest from the HP site?

Currently in the Maverick 50-wacom.conf at /usr/share/X11/xorg.conf.d/ is the following N-Trig snippet:
```
Section "InputClass"
 	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
 	MatchDevicePath "/dev/input/event*"
 	Driver "wacom"
	Option "Button2" "3"
EndSection
```
That puts your stylus on the Wacom driver and let's touch fall through to the evdev driver.  To decode a little the N-Trig usb kernel driver/module is called hid-ntrig.ko.  The Vendor ID = 1b96 and up till now the Product ID = 0001.  If you look at the 'xinput list' output you'll see the reason for 'N-Trig Pen' in the match line.  It specifies just the stylus and excludes the touch entry or entries.

So we want to find what the Product ID is with 'lsusb'.  Hopefully that will tell us and tell us if it has changed.  And of course we want to know what the 'xinput list' output looks like.

---

### Post by jkayner on 2011-02-10
sorry for any confusion.  that was the info from Windows 7.  I checked the n-trig site and they only list windows drivers for download.  Also that driver was from the disc that comes with the device.  I had to reinstall Win7 and HP provides a disc that restores all of the tablet drivers/apps back.
 
i haven't been able to successfully run 10.10 from a USB drive as of yet.

---

### Post by Favux on 2011-02-10
Hi jkayner,

> sorry for any confusion. that was the info from Windows 7.
No confusion, that's what we want to see.  We've been using the Windows version of the firmware etc. to figure out where folks are.  You need Windows to update the firmware & BIOS, etc.

In Windows, you should be able to go to the control panel and click on the N-trig stylus and touch. There should be an About tab or button that will provide the firmware version.

In linux the firmware might be listed in dmesg:
```
dmesg|grep -i ntrig
```
or
```
dmesg|grep -i 'n-trig'
```
depending on where Rafi Rubin is in putting reporting into the hid-ntrig.ko.  He was planning on doing that.

Rafi is one of the more active developers of the hid-ntrig.ko and is also involved in Ubuntu multi-touch.  He sometimes drops by in the forum.

---

### Post by jkayner on 2011-02-10
i posted the firmware version previously...
 
> ok here is the N-trig info for the tablet:

N-Trig DuoSense Digitizer
driver version: 1.26.8.45
Firmware version: 4.7.27.24.15
Software bundle version: 3.46



i also tried unetbootin and had the same boot issue

---

### Post by gonehiking on 2011-02-20
I have been running Lucid on slate 500 for couple of months. The trick to getting ubuntu booted was to create custom boot ISO with xhci driver available for install kernel. USB will not work without xhci driver. I did upgrade to Maverick at one point but Maverick did not work well at all, so I went back to Lucid. Onboard keyboard crashes gnome too often. I installed florence keyboard and it is working quite well. With Lucid, the hp slate works well enough for daily use.

---

### Post by rothgar on 2011-02-21
Do you have a walk through on how to create an iso with the xhci driver loaded in the kernel?

---

### Post by gunkzmile on 2011-02-22
> **jkayner said:**
> We just got the slate for testing at work.  I tried to run 10.10 netbook version from a usb thumbdrive.  I get the following message when booting on it. 

(initramfs) Unable to find a medium containing a live file system

the boot process halts at this point.  Any help is appreciated.

PS i am very noob on ubuntu.

Don't use unetbootin instead just using "[COLOR=Red]start up disk creator[/COLOR]" which come default with ubuntu installation. Coz I got this similar problem when try to create usb-live of Ubuntu 10.04-alternate-32bit. After googling it for awhile some guys advice me to use "start up disk creator". And it did solved my problem. :D

---

### Post by gonehiking on 2011-02-23
> **rothgar said:**
> Do you have a walk through on how to create an iso with the xhci driver loaded in the kernel?

I followed the instructions at [https://help.ubuntu.com/community/LiveCDCustomization ]("https://help.ubuntu.com/community/LiveCDCustomization"). I needed to unpack casper/initrd.lz, add lib/modules/2.6.32-24-generic/kernel/drivers/usb/host/xhci.ko from another machine running Lucid, then repack initrd and create a new boot CD. Instructions for modifying initrd are in the section "Removing the (Casper) Autologin". xhci driver will automatically be loaded when install kernel boots up.

I have uploaded the custom boot CD I created at [http://aziz65.home.comcast.net/~aziz65/ubuntu-10.04.1-desktop-i386-slate.iso]("http://aziz65.home.comcast.net/~aziz65/ubuntu-10.04.1-desktop-i386-slate.iso"). I will delete this ISO around March 15 since I do not have much space available to me on that server.

You will have to install wifi driver manually after Lucid install and here are instructions on how to do that:

To get wifi working, plug the bootable USB drive or SD card that you created back in. Open a gnome-terminal and &#8220;cd&#8221; to the USB drive/SD card. Install packages as follows:
[LIST]
[*]dpkg -i pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb
[*]dpkg -i pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb
[*]dpkg -i pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb
[*]dpkg -i pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb
[*]Reboot and wifi should be functional now
[/LIST]

---

### Post by ioxon on 2011-02-28
> **gonehiking said:**
> I followed the instructions at [https://help.ubuntu.com/community/LiveCDCustomization ]("https://help.ubuntu.com/community/LiveCDCustomization"). I needed to unpack casper/initrd.lz, add lib/modules/2.6.32-24-generic/kernel/drivers/usb/host/xhci.ko from another machine running Lucid, then repack initrd and create a new boot CD. Instructions for modifying initrd are in the section "Removing the (Casper) Autologin". xhci driver will automatically be loaded when install kernel boots up.

I have uploaded the custom boot CD I created at [http://aziz65.home.comcast.net/~aziz65/ubuntu-10.04.1-desktop-i386-slate.iso]("http://http://aziz65.home.comcast.net/%7Eaziz65/ubuntu-10.04.1-desktop-i386-slate.iso"). I will delete this ISO around March 15 since I do not have much space available to me on that server.

You will have to install wifi driver manually after Lucid install and here are instructions on how to do that:

To get wifi working, plug the bootable USB drive or SD card that you created back in. Open a gnome-terminal and &#8220;cd&#8221; to the USB drive/SD card. Install packages as follows:
[LIST]
[*]dpkg -i pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb
[*]dpkg -i pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb
[*]dpkg -i pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb
[*]dpkg -i pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb
[*]Reboot and wifi should be functional now
[/LIST]


You are a God-send for setting that up. I was able to get 10.04 on my slate because of you. Thanks!

I just never seem to find the time to run through the steps it takes to do one myself but I want to. I'd love to get 10.10 (which you can get Unity on) working in the same way you got 10.04. I tried 10.10 and couldn't boot but maybe one of these days I can pull away from things and spend time compiling the kernel appropriately.

I also didn't mention that a custom kernel like makes the upgrade process from 10.04 to 10.10 not work unfortunately.

If by some crazy chance you have already done the same thing for 10.10, let me know.

Thanks!

---

### Post by gonehiking on 2011-03-01
> **ioxon said:**
> 
I also didn't mention that a custom kernel like makes the upgrade process from 10.04 to 10.10 not work unfortunately.

If by some crazy chance you have already done the same thing for 10.10, let me know.

Thanks!

Keep in mind, what I created was a custom install CD, not custom kernel. The kernel that will be installed is the standard Lucid kernel. All upgrades have worked smoothly for me.

I installed the netbook interface (aptitude install ubuntu-netbook) which is pre-Unity interface. From looking at screenshots and reviews, I have a feeling I wouldn't like Unity interface as much and so have stayed away from installing Unity from PPA.

Once you have installed Lucid, you can easily upgrade to Maverick without having to create a custom Maverick install CD. This is what I did and did not create a custom Maverick install CD. First problem I had after booting into Maverick was touchscreen was non-responsive. I simply went back to Lucid instead of trying to figure out why touchscreen was not working. Recently I read somewhere that single touch does not come up enabled on Maverick while multi-touch is enabled. One has to go through some push-ups to re-enable single touch. This may explain why touchscreen did not seem to work after upgrade to Maverick. I have not gone back to trying Maverick again. At this point, I am considering trying out Natty instead once Beta 1 comes out.

---

### Post by ioxon on 2011-03-02
Thanks for the info.

I'll go ahead and reinstall Lucid with your custom boot CD and try again. I'm not sure why it gave me the message it did when I initially tried. Of course I only tried it once and never got a chance to try again because I tried updating to the latest Poulsbo driver which broke everything it seemed even when I was able to recover from that.

I will actually be trying to upgrade to Natty alpha 3 that is scheduled for release tomorrow. I'll give an update on my findings after trying that.

---

### Post by ttohumcu on 2011-03-05
Khalid,

Thank you for posting this. I've done every step with the lucid 10.04.2 version but I could not come up with the same result. The iso link you have provided does not seem to work anymore. If you don't mind can you send the link via dropbox or box.net? I've spent so much time on this and it is getting frustrated after doing everything people suggested. Your solution was the only one that did make sense and I've tried and failed it. 

Thanks in Advance..
Tolga

---

### Post by gonehiking on 2011-03-06
> **ttohumcu said:**
> Khalid,

Thank you for posting this. I've done every step with the lucid 10.04.2 version but I could not come up with the same result. The iso link you have provided does not seem to work anymore. If you don't mind can you send the link via dropbox or box.net? I've spent so much time on this and it is getting frustrated after doing everything people suggested. Your solution was the only one that did make sense and I've tried and failed it. 

Thanks in Advance..
Tolga

Tolga,

Somehow I had managed to mess up the link hiding in my posting. If you cut and pasted from my post, it worked fine but if you simply clicked on it, it wouldn't work. I have fixed the link in my original post. Try it again.

---

### Post by Naughty Monkey on 2011-03-09
> **gonehiking said:**
> Tolga,

Somehow I had managed to mess up the link hiding in my posting. If you cut and pasted from my post, it worked fine but if you simply clicked on it, it wouldn't work. I have fixed the link in my original post. Try it again.

gonehiking, it worked great for me. Thanks so much for posting you ISO!

Also, to enable wifi, I just went into Hardware Drivers and enabled the Broadcom STA wireless driver (ran fine from the LiveCD, I haven't installed to the hd yet). Worked like a charm!

NM

---

### Post by aquarat on 2011-04-26
I installed Lucid using a USB-CDROM drive, I then installed the Broadcom wireless drivers. The pen digitiser worked fine out of the box, but the touch interface didn't.

There were three significant issues for me after installation :
1) 3D acceleration didn't work.
2) Touch didn't work (which was actually kind of nice? it would be nice to be able to toggle this on and off in future for writing)
3) Video/CrystalHD acceleration didn't work. (mmm Youtube is tasty)

**Issue 1 :**
This page helped quite a lot when it came to 3D acceleration : [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

The PSB/Poulsbo driver is rated as "excellent" across all fields for 9.10/Karmic and the EMGD driver is rated reasonably well on Maverick. I tried installing PSB on both Lucid and Maverick; both resulted in a black screen where the logon screen would normally be. I removed PSB and installed EMGD instead... and that works quite well. An issue has been logged with the PSB team regarding the black screen on the HP Slate.

I learnt a new shortcut key : ALT+SYSRQ+E and/or ALT+SYSRQ+S (could be wrong, I'll check). These shortcuts drop you to a shell... I've always wanted to know how to do that.

I'm getting around 385 fps on glxgears.

So issue 1 is fixed... for now.

**Issue 2** : I added the utouch PPA repository, I installed hid-ntrig-dkms and utouch using aptitude. Neither the pen nor the touch capabilities work now... whoops. I have no idea how to get back to pen functionality.

[FONT="System"]xinput list :

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Comfort Curve Keyboard 2000     id=8    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                         id=9    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                        id=10   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                         id=12   [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                         id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Microsoft Comfort Curve Keyboard 2000     id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                            id=14   [slave  keyboard (3)][/FONT]

So not fixed.

and **Issue 3 :** CrystalHD support

I compiled libVA and the crystalHD drivers... downloaded mplayer-vaapi and compiled gstreamer-vaapi. vainfo returns this :

libva: libva version 0.31.1-sds1
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/emgd_drv_video.so
Intel(R) Embedded Media and Graphics Driver 1.5 Build 1816
Using XCB based dispatch table.
libva error: Failed to define max_display_attributes in init
libva error: /usr/lib/va/drivers/emgd_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

I was getting segmentation faults earlier, not sure what changed.

FFMPEG with --enable-vaapi on configure gives this error on make :
/home/aquarat/work/ffmpeg/libavcodec/libavcodec.a(crystalhd.o): In function `decode':
/home/aquarat/work/ffmpeg/libavcodec/crystalhd.c:814: undefined reference to `DtsTxFreeSize'

Any help would be most appreciated.

Thanks to gonehiking for hosting the custom ISO... I didn't use it but I will in future if I need to re-install.

---

### Post by Favux on 2011-04-26
Hi aquarat,

The N-Trig Pen should be on the Wacom X driver.  Let's check.  Enter in a terminal:
```
xinput list-props "N-Trig Pen stylus"
```
And post the output.  Inspecting the Xorg.0.log in /var/log should also help you determine what's going on.

---

### Post by aquarat on 2011-04-26
Hey Favux

I'm not sure what happened, but I rebooted and the pen input started working again.

But here's the output from that command anyway, maybe it will help someone else in future :
```

Device 'N-Trig Pen stylus':
	Device Enabled (120):	1
	Coordinate Transformation Matrix (122):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (241):	0
	Device Accel Constant Deceleration (242):	1.000000
	Device Accel Adaptive Deceleration (243):	1.000000
	Device Accel Velocity Scaling (244):	10.000000
	Wacom Tablet Area (264):	0, 0, 9600, 7200
	Wacom Rotation (265):	0
	Wacom Pressurecurve (266):	0, 0, 100, 100
	Wacom Serial IDs (267):	1, 0, 2, 0
	Wacom TwinView Resolution (268):	0, 0, 0, 0
	Wacom Display Options (269):	-1, 0, 1
	Wacom Screen Area (270):	0, 0, 1024, 600
	Wacom Proximity Threshold (271):	42
	Wacom Capacity (272):	-1
	Wacom Pressure Threshold (273):	27
	Wacom Sample and Suppress (274):	2, 4
	Wacom Enable Touch (275):	0
	Wacom Hover Click (276):	1
	Wacom Enable Touch Gesture (277):	0
	Wacom Touch Gesture Parameters (278):	50, 20, 250
	Wacom Tool Type (279):	"STYLUS" (281)
	Wacom Button Actions (280):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)


```

---

### Post by cheshirekow on 2011-05-16
Hey all, 

I just got my HP slate delivered today. I recall reading that the graphics hardware (the Intel chip and the media accelerator) both had drivers... but now I can't find the thread. Anyway, before I try to install Ubuntu on this thing, are there any suggestions other than creating a custom install cd including xhci?

What versions work the best? I've been sticking to 10.04 on my other machine(s) because some things seem to break with 10.10. I haven't tried 11.04 yet on anything. 

Thanks for any input.

Edit: OMG I'm retarded. Ok, so thanks aquarat for posting the info about the drivers (two posts above). Any news on utouch or the crystalHD driver?

---

### Post by aquarat on 2011-05-16
Hey cheshirekow

I've just settled for using the bundled Windows install for now... I love Ubuntu, I run it on my HP TC1100 and laptop but it's just not feasible on the Slate (for me, for now).

The major hurdles that need to be overcome before Ubuntu becomes usable are Wifi issues and CrystalHD support. 

I've found that the wifi connection stops working after a few minutes under Ubuntu on the Slate... it has done this with my Android phone as an AP and my home wifi.

The lack of the CrystalHD decoder means the machine gets hotter quicker, the battery doesn't last as long and quite a few media types won't play without skipping frames.

I also haven't been able to get the touch panel capabilities working under Ubuntu.

Let me know if you find a way of getting around these issues.

---

### Post by cheshirekow on 2011-05-16
> **aquarat said:**
> Hey cheshirekow
The major hurdles that need to be overcome before Ubuntu becomes usable are Wifi issues and CrystalHD support. 


I haven't noticed any problems with the WiFi yet. It seems to be working fine with the broadcom proprietary driver that comes in the repositories.

I installed the CrystalHD driver and library and I'm currently trying to build XBMC which is evidently the only media player that supports the CrystalHD. I'll also try mplayer-vaapi if this works and see if I can spot anything that might be causing your trouble. I can't seem to get XBMC to compile though because it needs libva-glx which I cannot find... any idea?

I've discovered some other drawbacks so far:
The intel EMGD driver doesn't seem to support xrandr so you can't rotate the screen in a live X session. You can still change the xorg.conf and restart X but normally I would want to flip portrait to landscape without losing my session. 

Next, the n-trig seems to be working but does not seem to be using the wacom drivers. lsmod | grep wacom shows nothing, and xsetwacom list shows nothing as well. I'll have to look into this, because I definately need to be able to turn on/off touch while writing. Also, I need to rotate the input if I change to portrait.

However, I think I will stick to ubuntu instead of going back to windows 7. The main reason I bought this slate is because I'm addicted to xournal (or, more generally, digital ink). In windows, the pen input is really slow. The strokes lagged far behind where my hand was and it would frequently drop strings of input all together (clearly, the hardware can't keep up). I tried evernote, the windows input tools, and xournal and they were all like that. However, in ubuntu, xournal is perfectly smooth.

---

### Post by aquarat on 2011-05-17
Hey Cheshirekow

yes, Xournal is fantastic and so is cellwriter, I use CW on my tc1100.

How did you get the touch interface to work ? It'd be really cool if it the touch interface could be turned on and off.

I've still got Ubuntu installed my machine, when I've got more time I'll try and work on the issues some more (but I'm no expert on any of them).

I never tried getting Xrandr working, it's not really an issue for me.

I tried mplayer-vaapi... the issue wasn't with the media player but rather with the driver for the crystalHD... If I remember correctly I compiled Broadcom's Linux drivers and then I had to move various files from the compile folders to various parts of the system. One of those files initially didn't load at all, then I managed to get it load but it would give errors shortly after loading. I never achieved playback.

---

### Post by cheshirekow on 2011-05-17
> **aquarat said:**
> Hey Cheshirekow
How did you get the touch interface to work ? It'd be really cool if it the touch interface could be turned on and off.


So it "just worked" for me. At least single finger touch. I'm working on getting the multi-touch to work now. I've got a ton of threads to finish reading through, but it's not promising. The N-trig seems to be getting picked up by the evdev driver, but multi-touch doesn't seem to be working. 

Also, I can't figure out why the pen is actually working. I reinstalled with 11.04 and I can't get the xf86-input-wacom for some reason (at least not from the repositories, I'll try compiling it later). From xinput list-props the pen is mapped to the evdev driver (not the wacom driver).

You can turn on/off touch (I believe) by disabling it with the xinput command. The command is something like 

```

xinput set-prop <device id> 'Device Enabled' 0

```

where <device id> is found by executing

```

xinput list

```

and looking for the N-Trig lines.

I plan to write a script to toggle that and bind it to one of the external keys if I can map them (or a touch gesture if I get ginn to work).

> 
I never tried getting Xrandr working, it's not really an issue for me.


Well, I think we're stuck with that one. There's a bug open on launchpad but it's up to Intel whether or not they'll fix that for us. That's what you get with closed source software. It "just works", except when it doesn't.

> 
I tried mplayer-vaapi... the issue wasn't with the media player but rather with the driver for the crystalHD... If I remember correctly I compiled Broadcom's Linux drivers and then I had to move various files from the compile folders to various parts of the system. One of those files initially didn't load at all, then I managed to get it load but it would give errors shortly after loading. I never achieved playback.

I see. I compiled the drivers from here: [http://code.google.com/p/crystalhd-for-osx/]("http://code.google.com/p/crystalhd-for-osx/")     

So I found the drivers in three places:
[LIST=1]
[*][http://www.broadcom.com/support/crystal_hd/]("http://www.broadcom.com/support/crystal_hd/")
[*][http://git.wilsonet.com/crystalhd.git/]("http://git.wilsonet.com/crystalhd.git/")
[*][http://code.google.com/p/crystalhd-for-osx/]("http://code.google.com/p/crystalhd-for-osx/")
[/LIST]

It's my understanding that (1) is the crystalHD manufacturer implementation. (2) is a modified/patched version of that which is part of the linux project (the so-called 'upstream source'). (3) is a patched version by a guy on the XBMC project. If you look at the main page for (3) he says to use (2) for the most up-to-date linux drivers. However I found on some other forums that (2) may be unstable, so that you should use (3). Anyway, that's what I'm using. I'm not sure why XBMC's configure script cant find the library, I've checked and it's in /usr/lib (and named exactly as the library that the configure script can't find). 

Did you get mplayer-vaapi from the repositories or somewhere else?

I'll post again to this thread (or maybe start a new one to work out a how to) if I make any more progress (though it'll be another day before I do... got a deadline to make first)

---

### Post by aquarat on 2011-05-17
Hey cheshirekow

Wow, you've been busy!

Mplayer-vaapi : I compiled from the source at this link : [http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/mplayer-vaapi-latest-FULL.tar.bz2](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/mplayer-vaapi-latest-FULL.tar.bz2)

The directory it's in is browse-able. I found quite a few resources via Google on Splitted-Desktop.

Also of interest on Splitted-Desktop is [http://www.splitted-desktop.com/~gbeauchesne/gstreamer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/gstreamer-vaapi/)

VAAPI-driver : I've only attempted compiling the original Broadcom drivers ([http://www.broadcom.com/support/crystal_hd/](http://www.broadcom.com/support/crystal_hd/)), which compiled successfully, but as I said threw errors shortly after load. Placing the files in the correct system folders was guess work... and may not have been done properly (possibly causing the errors after load).

I'll definitely try and compile option 2 in a few minutes, thanks for the links.

Touch : "but multi-touch doesn't seem to be working"
Single touch is fine by me :) Thanks for the hints I'll try and implement that shortly too.

I'll continue to post to this thread.

Update :

With emgd_drv_video.so in /usr/lib/va/drivers (libcrystalhd.so* is in the same folder) :
```

aquarat@slatrat:~/work/crystal2$ vainfo
libva: libva version 0.31.1-sds1
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/emgd_drv_video.so
Intel(R) Embedded Media and Graphics Driver 1.5 Build 1816
Using XCB based dispatch table.
libva error: Failed to define max_display_attributes in init
libva error: /usr/lib/va/drivers/emgd_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

emgd_drv_video.so removed but libcrystalhd still present :

```

aquarat@slatrat:~/work/crystal2$ vainfo
libva: libva version 0.31.1-sds1
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/emgd_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

It's specifically looking for the EMGD driver. I'm a bit confused but it looks like vaapi functions are present in both the crystalhd card and the poulsbo chipset?

[http://www.freedesktop.org/wiki/Software/vaapi](http://www.freedesktop.org/wiki/Software/vaapi) references both EMGD and CrystalHD.

A guide to getting vaapi going using splitted-desktop binaries but it relies on the PSB driver (which caused my machine not to start the last time I tried it) :
[http://linux-tipps.blogspot.com/2009/12/vaapi-accelerated-hd-video-on-msi-wind.html](http://linux-tipps.blogspot.com/2009/12/vaapi-accelerated-hd-video-on-msi-wind.html)

---

### Post by aquarat on 2011-05-17
I see someone else has encountered the same issue with EMGD drivers :

[http://ubuntuforums.org/showthread.php?t=1229345&page=307](http://ubuntuforums.org/showthread.php?t=1229345&page=307)

Scroll down to post #3065

---

### Post by Favux on 2011-05-17
Hi,

I'm a little puzzled as to why you can't use multi-touch in Maverick or Natty.  Aren't you able to place the N-Trig touch on evdev and use ginn as described on the [N-Trig HOW TO]("http://ubuntuforums.org/showthread.php?t=1252492")?

Does your N-Trig digitizer have a different Product ID?  The others have a Product ID of 1.  What does *lsusb* in a terminal show for Vendor and Product ID?

---

### Post by cheshirekow on 2011-05-17
> **Favux said:**
> Hi,
I'm a little puzzled as to why you can't use multi-touch in Maverick or Natty.  Aren't you able to place the N-Trig touch on evdev and use ginn as described on the [N-Trig HOW TO]("http://ubuntuforums.org/showthread.php?t=1252492")?

Does your N-Trig digitizer have a different Product ID?  The others have a Product ID of 1.  What does *lsusb* in a terminal show for Vendor and Product ID?

Hi Favux. I was totally going to PM you and ask you to join this thread since you've been the go-to-guy in at least 10 other threads I've read (lol). 

I'm not sure why it isn't working yet as I've only just started to diagnose the issue. I have looked at xinput list-props for the multi-touch device and it has several evdev properties (I'm assuming that means the evdev driver is picking it up). 

The N-trig how to is where I got a lot of the info so far, but to be honest I haven't completely read the whole thing. I only looked at it for about an hour last night (it's quite comprehensive!)

I will post more details and answer your questions when I get more time to look at it, but one thing that was puzzling me was that in Natty, I don't seem to have a wacom driver installed. There's no wacom_drv.so in /usr/lib/xorg/modules/input (like there is on my Lucid laptop, but I'm pretty sure I put that there after compiling it myself for my wacom Bamboo). Nor is there a 50-wacom.conf (or any ##-wacom.conf) in xorg.conf.d. My plan was to compile from source and get those in there for the digitizer.

As far as the multi-touch, I tried doing multiple finger gestures but they always just turn into a single finger mouse movement. I'm not exactly sure how to use ginn yet though. When I run it, I get a bunch of output to the terminal (it looks like it's regarding the parsing of the configuration file) but touching the screen and doing gestures with multiple fingers still just moves the mouse to one of the finger locations.

Once again, I'll post more details soon... but thanks.

---

### Post by Favux on 2011-05-17
Hi cheshirekow,

lol  Well I'm a poor substitute for Ayuthia or Rafi, but I'll try to help.

The xf86-input-wacom X driver should be installed by default.  But it seems to have not been for at least a few other folks.  Check if you have the xserver-xorg-input-wacom package installed.  That's the default xf86-input-wacom-0.10.11 and xsetwacom along with the .conf file.  If you compiled a newer one it will overwrite it.

For multi-touch I'm wondering if it is a firmware issue like the older firmware for the other N-Trig tablets.  I would think yours would be similar.  We can get a clue from the output of *xinput list* in a terminal and:
```
dmesg | grep ntrig
```
or something close to ntrig like n-trig.

---

### Post by cheshirekow on 2011-05-18
> **Favux said:**
> Hi cheshirekow,
The xf86-input-wacom X driver should be installed by default.  But it seems to have not been for at least a few other folks.  Check if you have the xserver-xorg-input-wacom package installed.


That's what I thought. xserver-xorg-input-wacom is not installed. When I try to install it I get:

```

:~$ sudo apt-get install xserver-xorg-input-wacom 
...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-input-wacom : Depends: xorg-input-abi-12
E: Broken packages

```

So, let's try to get the missing package.
```

:~$ sudo apt-get install xorg-input-abi-12
...
Package xorg-input-abi-12 is a virtual package provided by:
  xserver-xorg-core 2:1.10.1-1ubuntu1 [Not candidate version]

E: Package 'xorg-input-abi-12' has no installation candidate

```

Hm... that's weird. Here's what I think happened: when I installed the EMGD driver, it removed a bunch of the xorg packages and replaced all of them. I'm guessing they didn't provide something that is needed inorder for the wacom input driver. It might be time to try something other then EMGD.

Ok, let's look at some of the usuals
```

:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 1267:0103                           	id=9	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; HID 1267:0103                           	id=8	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=15	[slave  keyboard (3)]

```

```

:~$ xinput list-props 10
Device 'N-Trig Pen':
	Device Enabled (120):	1
	Coordinate Transformation Matrix (122):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (240):	0
	Device Accel Constant Deceleration (241):	1.000000
	Device Accel Adaptive Deceleration (242):	1.000000
	Device Accel Velocity Scaling (243):	10.000000
	Evdev Axis Inversion (244):	0, 0
	Evdev Axis Calibration (245):	<no items>
	Evdev Axes Swap (246):	0
	Axis Labels (247):	"Abs X" (257), "Abs Y" (258), "Abs Pressure" (259)
	Button Labels (248):	"Button 0" (239), "Button Unknown" (238), "Button Unknown" (238), "Button Wheel Up" (126), "Button Wheel Down" (127)
	Evdev Middle Button Emulation (249):	0
	Evdev Middle Button Timeout (250):	50
	Evdev Wheel Emulation (251):	0
	Evdev Wheel Emulation Axes (252):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (253):	10
	Evdev Wheel Emulation Timeout (254):	200
	Evdev Wheel Emulation Button (255):	4
	Evdev Drag Lock Buttons (256):	0

```

```

:~$ xinput list-props 11
Device 'N-Trig MultiTouch':
	Device Enabled (120):	1
	Coordinate Transformation Matrix (122):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (240):	0
	Device Accel Constant Deceleration (241):	1.000000
	Device Accel Adaptive Deceleration (242):	1.000000
	Device Accel Velocity Scaling (243):	10.000000
	Evdev Axis Inversion (244):	0, 0
	Evdev Axis Calibration (245):	<no items>
	Evdev Axes Swap (246):	0
	Axis Labels (247):	"Abs X" (257), "Abs Y" (258), "Abs MT Touch Major" (260), "Abs MT Touch Minor" (261), "Abs MT Orientation" (262), "Abs MT Position X" (263), "Abs MT Position Y" (264)
	Button Labels (248):	"Button Unknown" (238), "Button Unknown" (238), "Button Unknown" (238), "Button Wheel Up" (126), "Button Wheel Down" (127)
	Evdev Middle Button Emulation (249):	0
	Evdev Middle Button Timeout (250):	50
	Evdev Wheel Emulation (251):	0
	Evdev Wheel Emulation Axes (252):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (253):	10
	Evdev Wheel Emulation Timeout (254):	200
	Evdev Wheel Emulation Button (255):	4
	Evdev Drag Lock Buttons (256):	0

```

```

:~$ xinput list-props 12
Device 'N-Trig Touchscreen':
	Device Enabled (120):	1
	Coordinate Transformation Matrix (122):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (240):	0
	Device Accel Constant Deceleration (241):	1.000000
	Device Accel Adaptive Deceleration (242):	1.000000
	Device Accel Velocity Scaling (243):	10.000000
	Evdev Axis Inversion (244):	0, 0
	Evdev Axis Calibration (245):	<no items>
	Evdev Axes Swap (246):	0
	Axis Labels (247):	"Abs X" (257), "Abs Y" (258), "Abs Misc" (265), "Abs Misc" (265)
	Button Labels (248):	"Button 0" (239), "Button Unknown" (238), "Button Unknown" (238), "Button Wheel Up" (126), "Button Wheel Down" (127)
	Evdev Middle Button Emulation (249):	0
	Evdev Middle Button Timeout (250):	50
	Evdev Wheel Emulation (251):	0
	Evdev Wheel Emulation Axes (252):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (253):	10
	Evdev Wheel Emulation Timeout (254):	200
	Evdev Wheel Emulation Button (255):	4
	Evdev Drag Lock Buttons (256):	0

```

```

dmesg | grep N-trig
[    5.462131] ntrig 0003:1B96:0001.0001: hidraw2: USB HID v1.10 Device [N-trig DuoSense] on usb-0000:00:1d.1-2/input0
[    5.841057] input: N-trig DuoSense as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input7
[    5.852111] input: N-trig DuoSense as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input8
[    5.867466] input: N-trig DuoSense as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input9
[    5.871346] ntrig 0003:1B96:0001.0002: input,hidraw3: USB HID v1.10 Device [N-trig DuoSense] on usb-0000:00:1d.1-2/input1

```

```

:~$ lsusb
Bus 004 Device 002: ID 0a5c:21b4 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 10f1:1a26  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by cheshirekow on 2011-05-18
Ok, I'm trying to install the xf86 input driver. I'll post this just for reference since I'm on a new install so it'll be useful to know what's required.

```

sudo apt-get install git-core build-essential autoconf xutils-dev libtool
git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
cd xf86-input-wacom
./autogen

```

Unfortunately it doesn't make it past the configure script. I get the following errors:

```

configure: error: Package requirements (xorg-server >= 1.7.0 xproto xext kbproto inputproto randrproto) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'xext' found
No package 'kbproto' found
No package 'inputproto' found
No package 'randrproto' found

```

It really is looking like the EMGD driver is preventing the wacom driver.


Edit:
Ok, weird. I added this guys PPA: [https://launchpad.net/~thopiekar/+archive/emgd?field.series_filter=natty](https://launchpad.net/~thopiekar/+archive/emgd?field.series_filter=natty) and then tried to install xorg-input-wacom with apt-get and it didn't work. Then I tried with Synaptic (wouldn't have figured it would work... but whatever) and it worked. Maybe I forgot to apt-get update? Anyway... that seemed to work. 

After rebooting the N-Trig pen is now on the wacom driver.

```

:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 1267:0103                           	id=9	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                       	id=10	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen pad                          	id=11	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                       	id=12	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig MultiTouch                       	id=13	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; HID 1267:0103                           	id=8	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=15	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=16	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=17	[slave  keyboard (3)]
:~$ xinput list-props 10
Device 'N-Trig Pen eraser':
	Device Enabled (120):	1
	Coordinate Transformation Matrix (122):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (240):	0
	Device Accel Constant Deceleration (241):	1.000000
	Device Accel Adaptive Deceleration (242):	1.000000
	Device Accel Velocity Scaling (243):	10.000000
	Wacom Tablet Area (263):	0, 0, 9600, 7200
	Wacom Rotation (264):	0
	Wacom Pressurecurve (265):	0, 0, 100, 100
	Wacom Serial IDs (266):	1, 0, 10, 0
	Wacom Capacity (267):	-1
	Wacom Pressure Threshold (268):	27
	Wacom Sample and Suppress (269):	2, 4
	Wacom Enable Touch (270):	0
	Wacom Enable Touch Gesture (271):	0
	Wacom Touch Gesture Parameters (272):	50, 20, 250
	Wacom Tool Type (273):	"ERASER" (257)
	Wacom Button Actions (274):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (275):	0, 0

```

Thanks thopiekar, whoever you are.

Ok, now on to multitouch.

---

### Post by Favux on 2011-05-18
Try the build dependencies on Part II. of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by Favux on 2011-05-18
You've confirmed the important thing.  We were right in thinking you have the same digitizer as the HP TX2z, Dell XT, and Dell XT2.
Vendor ID = 1b96
Product ID = 0001

So barring some sort of firmware problem you should be able to get the 'N-Trig Pen' on the Wacom X driver rather than evdev and you already have 'N-Trig MultiTouch' on the evdev driver.  Since ginn is installed by default on Natty, you should have multi-touch gestures unless you need to do some tinkering with the wishes.xml file.

Starting with Karmic they did introduce a new dependency for xserver-xorg-input-wacom and that was xserver-xorg-input-all.  Can't have one without the other.  I think that's still true with Natty.

---

### Post by cheshirekow on 2011-05-18
> **Favux said:**
> You've confirmed the important thing.  We were right in thinking you have the same digitizer as the HP TX2z, Dell XT, and Dell XT2.
Vendor ID = 1b96
Product ID = 0001

So barring some sort of firmware problem you should be able to get the 'N-Trig Pen' on the Wacom X driver rather than evdev and you already have 'N-Trig MultiTouch' on the evdev driver.  

You're right, and I did manage to get it. You're probably right about the build dependencies in your last post, but I guess someone else has built it successfully so I'll just use his for now. I will probably try to build it later just to make sure I can (because it improves frequently).

As far as using ginn, I'm still not 100% sure how it's supposed to work. Does it run in the background? 'ps -A | grep ginn' shows nothing. I figured I'm supposed to start it manually (from reading online), so I try that by opening a terminal and typing 'ginn'.

I checked /etc/ginn/wishes.xml and the first gesture is "Drag" with 2 fingers maps to the key "down", so I try that, but it just drags the mouse pointer under one of the fingers.

Edit:
Does utouch need to be installed? It seems I don't have it, though I thought it came with Natty.

Edit: 
I installed it from the repository and it doesn't seem to have helped... unless I need to start it up manually. `ps -A | grep utouch` shows nothing (I'm not sure if it's supposed to or what).

---

### Post by cheshirekow on 2011-05-18
I found the firmware version: 4.7.27.24.7 whcich his higher than the 4.6.5.8.5 quoted on the N-trig how to as the recommended (right)?

```

:~$ dmesg | grep ntrig
[    5.815656] ntrig 0003:1B96:0001.0001: hidraw2: USB HID v1.10 Device [N-trig DuoSense] on usb-0000:00:1d.1-2/input0
[    5.816204] ntrig 0003:1B96:0001.0001: Firmware version: 4.7.27.24.7 (1f08 0f63)
[    6.105637] ntrig 0003:1B96:0001.0002: input,hidraw3: USB HID v1.10 Device [N-trig DuoSense] on usb-0000:00:1d.1-2/input1
[    6.113199] ntrig 0003:1B96:0001.0002: Firmware version: 4.7.27.24.7 (1f08 0f63)


```

---

### Post by Ayuthia on 2011-05-18
I am still catching up on this thread, but from what I have read, it looks like you are trying to get multitouch gestures to work.  One way to test things out is to install utouch-gesturetest.  From there, you can run in a Terminal:
```

gesturetest 0 0 0xffffffff

```
Once you press enter, the prompt should just sit there.  Once you touch a finger on the screen, it should report something back.  I know that it should be able to see up to four fingers.  It will list one finger, two fingers, environment drag (three fingers), and meta drag (four fingers)

I have not heard too much about the Slate so I am not for sure about how many fingers it can report.  However, I don't think that it should be causing problems.

Let us know if it reports anything.  

By the way, do you which /dev/input/event number the N-Trig MultiTouch is reporting on?  If not, can you post the results of:
```

ls -l /dev/input/by-path

```

Thanks!

---

### Post by Ayuthia on 2011-05-18
> **cheshirekow said:**
> You're right, and I did manage to get it. You're probably right about the build dependencies in your last post, but I guess someone else has built it successfully so I'll just use his for now. I will probably try to build it later just to make sure I can (because it improves frequently).

As far as using ginn, I'm still not 100% sure how it's supposed to work. Does it run in the background? 'ps -A | grep ginn' shows nothing. I figured I'm supposed to start it manually (from reading online), so I try that by opening a terminal and typing 'ginn'.


I have not run ginn in Natty as of yet, but in the past you ran ginn from the Terminal and then it should be active.  You should be able to use it in Firefox and the Terminal should be able to report things back.

If you are using Unity, if you tap four fingers on the screen, it should bring up the shortcuts screen.  This is without using ginn.

---

### Post by cheshirekow on 2011-05-18
> **Ayuthia said:**
> I am still catching up on this thread, but from what I have read, it looks like you are trying to get multitouch gestures to work.  


That's correct!

> 
One way to test things out is to install utouch-gesturetest.


Fantastic, now I feel like I'm making progress. I *think* the slate reports four fingers (if I remember correctly). I run gesture test with the command you gave and when I touch the screen I get no output. The mouse moves to where I touched but the output of the terminal is unchanged.


> 
By the way, do you which /dev/input/event number the N-Trig MultiTouch is reporting on? 


I don't but here's the output of the command:

```

:~$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.0-usb-0:1:1.0-event-kbd -> ../event3
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.0-usb-0:1:1.1-event -> ../event4
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.1-usb-0:2:1.1-event -> ../event7
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.1-usb-0:2:1.1-event-mouse -> ../event8
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.1-usb-0:2:1.1-mouse -> ../mouse2
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.7-usb-0:8:1.0-event -> ../event5
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 platform-i8042-serio-0-event-kbd -> ../event1

```

Edit:
I also want to point out one thing: There are two devices listed from `xinput list`. One is called "N-Trig Touchscreen" and the other is called "N-Trig MultiTouch". Perhaps one of those devices is working (so I'm getting single finger mouse input), but the other is not.

---

### Post by cheshirekow on 2011-05-18
> **Ayuthia said:**
> I have not run ginn in Natty as of yet, but in the past you ran ginn from the Terminal and then it should be active.  You should be able to use it in Firefox and the Terminal should be able to report things back.


That's what I thought. I don't think it's working at all, also considering the result of gesture-test.

> 
If you are using Unity, if you tap four fingers on the screen, it should bring up the shortcuts screen.  This is without using ginn.

I'm using the classic interface. For some reason unity looks all fuzzy (like it's low res and scaled up). I'm not worrying about that yet because I prefer the classic interface anyway.

---

### Post by Ayuthia on 2011-05-18
> **cheshirekow said:**
> That's correct!



Fantastic, now I feel like I'm making progress. I *think* the slate reports four fingers (if I remember correctly). I run gesture test with the command you gave and when I touch the screen I get no output. The mouse moves to where I touched but the output of the terminal is unchanged.




I don't but here's the output of the command:

```

:~$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.0-usb-0:1:1.0-event-kbd -> ../event3
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.0-usb-0:1:1.1-event -> ../event4
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.1-usb-0:2:1.1-event -> ../event7
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.1-usb-0:2:1.1-event-mouse -> ../event8
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.1-usb-0:2:1.1-mouse -> ../mouse2
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 pci-0000:00:1d.7-usb-0:8:1.0-event -> ../event5
lrwxrwxrwx 1 root root 9 2011-05-18 18:48 platform-i8042-serio-0-event-kbd -> ../event1

```

I am thinking that it is /dev/input/event7.  You can try and install evtest and then run:
```

sudo evtest /dev/input/event7

```
It should show that it is using 'N-Trig MultiTouch' and when you touch the screen, it should report things back.  Please post a portion of it where you touch the screen with four fingers.  We should be able to see what is being reported.

---

### Post by Ayuthia on 2011-05-18
> **cheshirekow said:**
> 
I also want to point out one thing: There are two devices listed from `xinput list`. One is called "N-Trig Touchscreen" and the other is called "N-Trig MultiTouch". Perhaps one of those devices is working (so I'm getting single finger mouse input), but the other is not.

Usually when you see both, it is the MultiTouch that is working.  When the system can only report single touch, it defaults to N-Trig Touchscreen.

---

### Post by cheshirekow on 2011-05-18
Ok, here are the results of evtest. I touched four fingers to the pad and immediately pulled them away, and evtest output 400 lines! I'll just post the first bit unless we need more (it's saved to a file).

Also, just to confirm... it was advertised as having four-finger touch before it was released. The specs page on the website just says "multi-touch"... and I didn't play around with windows for more than 10 minutes before installing Ubuntu. I should have thought to try it at least (though honestly I was mostly concerned with the performance of the pen input).

```

Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x1b96 product 0x1 version 0x110
Input device name: "N-Trig MultiTouch"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value   4656
      Min        0
      Max     9600
      Fuzz      75
    Event code 1 (Y)
      Value   2407
      Min        0
      Max     7200
      Fuzz      78
    Event code 48 (?)
      Value      0
      Min        0
      Max     9600
      Fuzz     200
    Event code 49 (?)
      Value      0
      Min        0
      Max     7200
      Fuzz     150
    Event code 52 (?)
      Value      0
      Min        0
      Max        1
    Event code 53 (?)
      Value      0
      Min        0
      Max     9600
      Fuzz      75
    Event code 54 (?)
      Value      0
      Min        0
      Max     7200
      Fuzz      78
Testing ... (interrupt to exit)

```

And then after a touch
```

Event: time 1305760755.417062, type 3 (Absolute), code 53 (?), value 6286
Event: time 1305760755.417085, type 3 (Absolute), code 54 (?), value 1900
Event: time 1305760755.417089, type 3 (Absolute), code 52 (?), value 0
Event: time 1305760755.417092, type 3 (Absolute), code 48 (?), value 771
Event: time 1305760755.417096, type 3 (Absolute), code 49 (?), value 417
Event: time 1305760755.417100, -------------- Config Sync ------------
Event: time 1305760755.417122, type 3 (Absolute), code 53 (?), value 4129
Event: time 1305760755.417126, type 3 (Absolute), code 54 (?), value 1761
Event: time 1305760755.417129, type 3 (Absolute), code 52 (?), value 1
Event: time 1305760755.417133, type 3 (Absolute), code 48 (?), value 626
Event: time 1305760755.417136, type 3 (Absolute), code 49 (?), value 514
Event: time 1305760755.417140, -------------- Config Sync ------------
Event: time 1305760755.417145, type 3 (Absolute), code 53 (?), value 3602
Event: time 1305760755.417149, type 3 (Absolute), code 54 (?), value 3815
Event: time 1305760755.417153, type 3 (Absolute), code 52 (?), value 1
Event: time 1305760755.417156, type 3 (Absolute), code 48 (?), value 626
Event: time 1305760755.417160, type 3 (Absolute), code 49 (?), value 514
Event: time 1305760755.417163, -------------- Config Sync ------------
Event: time 1305760755.417168, type 1 (Key), code 330 (Touch), value 1
Event: time 1305760755.417173, type 3 (Absolute), code 0 (X), value 6286
Event: time 1305760755.417176, type 3 (Absolute), code 1 (Y), value 1900
Event: time 1305760755.417182, -------------- Report Sync ------------
Event: time 1305760755.436598, type 3 (Absolute), code 53 (?), value 6287
Event: time 1305760755.436612, type 3 (Absolute), code 54 (?), value 1890
Event: time 1305760755.436614, type 3 (Absolute), code 52 (?), value 0
Event: time 1305760755.436617, type 3 (Absolute), code 48 (?), value 771
Event: time 1305760755.436619, type 3 (Absolute), code 49 (?), value 417
Event: time 1305760755.436621, -------------- Config Sync ------------
Event: time 1305760755.436634, type 3 (Absolute), code 53 (?), value 4113
Event: time 1305760755.436637, type 3 (Absolute), code 54 (?), value 1769
Event: time 1305760755.436639, type 3 (Absolute), code 52 (?), value 1
Event: time 1305760755.436641, type 3 (Absolute), code 48 (?), value 626
Event: time 1305760755.436643, type 3 (Absolute), code 49 (?), value 514
Event: time 1305760755.436645, -------------- Config Sync ------------
Event: time 1305760755.436648, type 3 (Absolute), code 53 (?), value 3590
Event: time 1305760755.436651, type 3 (Absolute), code 54 (?), value 3800
Event: time 1305760755.436653, type 3 (Absolute), code 52 (?), value 0
Event: time 1305760755.436655, type 3 (Absolute), code 48 (?), value 771
Event: time 1305760755.436657, type 3 (Absolute), code 49 (?), value 626
Event: time 1305760755.436660, -------------- Config Sync ------------
Event: time 1305760755.436669, -------------- Report Sync ------------
Event: time 1305760755.454843, type 3 (Absolute), code 53 (?), value 6293
Event: time 1305760755.454857, type 3 (Absolute), code 54 (?), value 1889
Event: time 1305760755.454859, type 3 (Absolute), code 52 (?), value 0
Event: time 1305760755.454861, type 3 (Absolute), code 48 (?), value 771
Event: time 1305760755.454863, type 3 (Absolute), code 49 (?), value 417
Event: time 1305760755.454865, -------------- Config Sync ------------
Event: time 1305760755.454878, type 3 (Absolute), code 53 (?), value 4071
Event: time 1305760755.454880, type 3 (Absolute), code 54 (?), value 1788
Event: time 1305760755.454881, type 3 (Absolute), code 52 (?), value 1
Event: time 1305760755.454883, type 3 (Absolute), code 48 (?), value 626
Event: time 1305760755.454885, type 3 (Absolute), code 49 (?), value 514
Event: time 1305760755.454887, -------------- Config Sync ------------
Event: time 1305760755.454890, type 3 (Absolute), code 53 (?), value 3596
Event: time 1305760755.454892, type 3 (Absolute), code 54 (?), value 3805
Event: time 1305760755.454894, type 3 (Absolute), code 52 (?), value 0
Event: time 1305760755.454896, type 3 (Absolute), code 48 (?), value 771
Event: time 1305760755.454898, type 3 (Absolute), code 49 (?), value 626
Event: time 1305760755.454899, -------------- Config Sync ------------
---snip---

```

---

### Post by cheshirekow on 2011-05-18
On more tidbit, to confirm your comment before, if I disable "N-Trig Touchscreen" I can still move the mouse pointer with my finger. If I disable "N-Trig MultiTouch" then the mouse pointer does not move when I touch the screen. If I re-enable "TouchScreen" still no mouse movement. If I re-enable "MultiTouch" then the mouse moves when I touch the screen.

---

### Post by Ayuthia on 2011-05-18
> **cheshirekow said:**
> Ok, here are the results of evtest. I touched four fingers to the pad and immediately pulled them away, and evtest output 400 lines! I'll just post the first bit unless we need more (it's saved to a file).

Also, just to confirm... it was advertised as having four-finger touch before it was released. The specs page on the website just says "multi-touch"... and I didn't play around with windows for more than 10 minutes before installing Ubuntu. I should have thought to try it at least (though honestly I was mostly concerned with the performance of the pen input).

Boy, that sounds like me.

```

Event: time 1305760755.417062, type 3 (Absolute), code 53 (?), value 6286
Event: time 1305760755.417085, type 3 (Absolute), code 54 (?), value 1900
Event: time 1305760755.417089, type 3 (Absolute), code 52 (?), value 0
Event: time 1305760755.417092, type 3 (Absolute), code 48 (?), value 771
Event: time 1305760755.417096, type 3 (Absolute), code 49 (?), value 417
Event: time 1305760755.417100, -------------- Config Sync ------------
Event: time 1305760755.417122, type 3 (Absolute), code 53 (?), value 4129
Event: time 1305760755.417126, type 3 (Absolute), code 54 (?), value 1761
Event: time 1305760755.417129, type 3 (Absolute), code 52 (?), value 1
Event: time 1305760755.417133, type 3 (Absolute), code 48 (?), value 626
Event: time 1305760755.417136, type 3 (Absolute), code 49 (?), value 514
Event: time 1305760755.417140, -------------- Config Sync ------------
Event: time 1305760755.417145, type 3 (Absolute), code 53 (?), value 3602
Event: time 1305760755.417149, type 3 (Absolute), code 54 (?), value 3815
Event: time 1305760755.417153, type 3 (Absolute), code 52 (?), value 1
Event: time 1305760755.417156, type 3 (Absolute), code 48 (?), value 626
Event: time 1305760755.417160, type 3 (Absolute), code 49 (?), value 514
Event: time 1305760755.417163, -------------- Config Sync ------------
Event: time 1305760755.417168, type 1 (Key), code 330 (Touch), value 1
Event: time 1305760755.417173, type 3 (Absolute), code 0 (X), value 6286
Event: time 1305760755.417176, type 3 (Absolute), code 1 (Y), value 1900
Event: time 1305760755.417182, -------------- Report Sync ------------

```

From this code portion, it does look like it can see and report multiple fingers.  You can tell this because it reported the Config Sync more than once between the Report Sync.  It is also showing more than just the X/Y reports so it is reporting the MT events which is what we need for ginn.

So now we need to figure out why it cannot be seen in gesturetest.  Just to be sure, the N-Trig MultiTouch is still using the evdev driver, right (you can tell through xinput list-props 'N-Trig MultiTouch')?  If that is the case, can you make sure that gesturetest is not responding with gesturetest 0 0 0xffffffff -- that is two zeroes and a zero followed by a lowercase x and then 8 lowercase f's.

---

### Post by cheshirekow on 2011-05-18
> **Ayuthia said:**
> 
From this code portion, it does look like it can see and report multiple fingers.  You can tell this because it reported the Config Sync more than once between the Report Sync.  It is also showing more than just the X/Y reports so it is reporting the MT events which is what we need for ginn.


That is encouraging

> 
So now we need to figure out why it cannot be seen in gesturetest.  Just to be sure, the N-Trig MultiTouch is still using the evdev driver, right (you can tell through xinput list-props 'N-Trig MultiTouch')?

Yes xinput list-props for the 'MultiTouch' device still lists several evdev properties.

> 
If that is the case, can you make sure that gesturetest is not responding with gesturetest 0 0 0xffffffff -- that is two zeroes and a zero followed by a lowercase x and then 8 lowercase f's.


Yup, still nothing showing up in gesture test.

Here's an idea: perhaps there's something wrong with the xorg config files. Since I installed the EMGD driver, it may have generated a set of xorg configs that do something funny with the N-Trig. I'll see if I can find something a long those lines.

Here's /usr/share/X11/xorg.conf.d/10-evdev.conf

```

#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

```

Here's yet another possibility. The EMGD x server has broken randr extention. Is it possible this isn't working because the EMGD driver, or is that unrelated?

Ok well, it looks like I'm about out of battery on the slate. I will have to postpone further investigation until later this evening. I will appreciate any suggestions in the meantime.

---

### Post by Ayuthia on 2011-05-18
The EMGD driver should not be causing any problems with the N-Trig portion.  My guess is that we are missing a package.  Can you post the results of the utouch packages that have been installed?
```

dpkg -l *utouch*

```

---

### Post by cheshirekow on 2011-05-18
Ok, sure, here goes:

```

:~$ dpkg -l *utouch*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  libutouch-evemu1          1.0.5-0ubuntu1            Kernel Device Emulation Library
ii  libutouch-frame1          1.1.1-0ubuntu1            Touch Frame Library
ii  libutouch-geis-dev        2.0.10-0ubuntu1           Gesture engine interface support - dev files
ii  libutouch-geis-doc        2.0.10-0ubuntu1           Gesture engine interface support - documentation
ii  libutouch-geis1           2.0.10-0ubuntu1           Gesture engine interface support
ii  libutouch-grail-dev       1.0.20-0ubuntu4           Gesture Recognition And Instantiation Library - dev files
ii  libutouch-grail1          1.0.20-0ubuntu4           Gesture Recognition And Instantiation Library
ii  utouch                    1.1                       A meta-package to install gesture libraries and tools
ii  utouch-geis-tools         2.0.10-0ubuntu1           Gesture engine interface support - test tools
ii  utouch-gesturetest        1.0.4-0ubuntu1            Test tool for the X Gesture extension
ii  utouch-grail-tools        1.0.20-0ubuntu4           Gesture Recognition And Instantiation Library - test tools


```

---

### Post by cheshirekow on 2011-05-19
Ok, well, I just did a fresh install of Natty. I figured that it was time to start over and that I should investigate the multi-touch *before* doing anything else this time. Naturally, it's working now (also, the pen is back on the wacom driver. 

I'm going to start by installing the EMGD driver and seeing if that is what broke broke the wacom and the touch. I'll pay closer attention to which packages get removed when I try to install the EMGD driver, and report back.

Edit:
I just noticed that both xserver-xorg-input-wacom and xserver-xorg-input-all are removed when installing the emgd packages. However, only xserver-xorg-input-evdev, -mouse, -synaptics, and -vmouse are added back. I guess this is the problem. I noticed in the list of xserver-xorg-input-? packages there is one called xserver-xorg-input-mutouch. I bet that is what was missing. This time, after installing the EMGD driver, I'll try to get that one from the repository, and see if it fixes the problem. If not, I'll probably try to install Maverick and try out the PSB driver. It reports better 2D acceleration (which I hope makes ubuntu snappier, because Natty is looking a little clunky when dragging around windows, even with the EMGD driver).

Edit:
Hm... I can't find a good description of what mutouch is, but maybe it's not actually required. In any case, does anyone know if multi-touch requires an xf86 input driver other than evdev? Or maybe the version of the evdev driver that the EMGD driver installs is too old? It looks like when installing the EMGD driver, all the other x input drivers also get reinstalled, I guess from the EMGD PPA... which maybe has older versions? In either case, I think I will reinstall (yet again) with Maverick, try the PSB driver, and see if that doesn't screw things up as bad as this EMGD driver. It looks like the "normal video playback" for that driver isn't so hot, but since the slate has the CrystalHD media accelerator, maybe video playback isn't a big deal.

In either case, It looks like for HP Slate 500 and Natty, hardware accelerated video and multitouch are mutually exclusive right now.

---

### Post by Ayuthia on 2011-05-19
> **cheshirekow said:**
> Ok, well, I just did a fresh install of Natty. I figured that it was time to start over and that I should investigate the multi-touch *before* doing anything else this time. Naturally, it's working now (also, the pen is back on the wacom driver. 

I'm going to start by installing the EMGD driver and seeing if that is what broke broke the wacom and the touch. I'll pay closer attention to which packages get removed when I try to install the EMGD driver, and report back.

Edit:
I just noticed that both xserver-xorg-input-wacom and xserver-xorg-input-all are removed when installing the emgd packages. However, only xserver-xorg-input-evdev, -mouse, -synaptics, and -vmouse are added back. I guess this is the problem. I noticed in the list of xserver-xorg-input-? packages there is one called xserver-xorg-input-mutouch. I bet that is what was missing. This time, after installing the EMGD driver, I'll try to get that one from the repository, and see if it fixes the problem. If not, I'll probably try to install Maverick and try out the PSB driver. It reports better 2D acceleration (which I hope makes ubuntu snappier, because Natty is looking a little clunky when dragging around windows, even with the EMGD driver).

Edit:
Hm... I can't find a good description of what mutouch is, but maybe it's not actually required. In any case, does anyone know if multi-touch requires an xf86 input driver other than evdev? Or maybe the version of the evdev driver that the EMGD driver installs is too old? It looks like when installing the EMGD driver, all the other x input drivers also get reinstalled, I guess from the EMGD PPA... which maybe has older versions? In either case, I think I will reinstall (yet again) with Maverick, try the PSB driver, and see if that doesn't screw things up as bad as this EMGD driver. It looks like the "normal video playback" for that driver isn't so hot, but since the slate has the CrystalHD media accelerator, maybe video playback isn't a big deal.

In either case, It looks like for HP Slate 500 and Natty, hardware accelerated video and multitouch are mutually exclusive right now.

That would explain it.  The evdev driver that Natty is using contains code to help make the multitouch work.  So it could be possible that the EMGD PPA does not have the patches for it.  From what I can see from the [PPA]("https://launchpad.net/~gma500/+archive/emgd"), they downgraded the xorg-server-core back down to 1.9 (it looks like it was down to 1.9.2).  So that most likely means that they had some problems with getting the EMGD to work with the 1.10.  Based on the current [evdev driver]("http://packages.ubuntu.com/source/natty/xserver-xorg-input-evdev"), it says that it requires at least 1.9.99 so it looks like that source might not compile or run well with the downgraded xserver-xorg-core (what was going to be my original suggestion to try).

As for the mutouch, that is another driver for another touch device.  As far as I know, it is not needed for N-trig devices.  The only drivers that are used are the Wacom and evdev drivers.  The Wacom is recommended for the stylus and evdev is recommended for the touch.

If you have some compiling experience (and no fear of messing up your install), an option to try would be to see if you can compile Maverick's [evdev driver]("http://packages.ubuntu.com/source/maverick/xserver-xorg-input-evdev").  It should be compatible with ginn as far as I can tell.  Of course, I am not for sure about how well the Slate can handle compiling source code.  It is not too hard compile and install this, but you have to make sure all the dependencies are there (sudo apt-get build-dep xserver-xorg-input-evdev).

Sorry for the long winded reply.  It does look like the two drivers are mutually exclusive right now like you said.  Hopefully they can get the xserver-xorg-core updated soon along with its input packages.

---

### Post by cheshirekow on 2011-05-19
> **Ayuthia said:**
> That would explain it.  The evdev driver that Natty is using contains code to help make the multitouch work.  So it could be possible that the EMGD PPA does not have the patches for it.  From what I can see from the [PPA]("https://launchpad.net/~gma500/+archive/emgd"), they downgraded the xorg-server-core back down to 1.9 (it looks like it was down to 1.9.2).  So that most likely means that they had some problems with getting the EMGD to work with the 1.10.  Based on the current [evdev driver]("http://packages.ubuntu.com/source/natty/xserver-xorg-input-evdev"), it says that it requires at least 1.9.99 so it looks like that source might not compile or run well with the downgraded xserver-xorg-core (what was going to be my original suggestion to try).


Yeah, it says on the [Poulsbo Wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") page that it only works with a downgraded xserver.

> 
As for the mutouch, that is another driver for another touch device.  As far as I know, it is not needed for N-trig devices.  The only drivers that are used are the Wacom and evdev drivers.  The Wacom is recommended for the stylus and evdev is recommended for the touch.


Ok, thanks for the explanation.

> 
If you have some compiling experience (and no fear of messing up your install), an option to try would be to see if you can compile Maverick's [evdev driver]("http://packages.ubuntu.com/source/maverick/xserver-xorg-input-evdev").  It should be compatible with ginn as far as I can tell.  Of course, I am not for sure about how well the Slate can handle compiling source code.  It is not too hard compile and install this, but you have to make sure all the dependencies are there (sudo apt-get build-dep xserver-xorg-input-evdev).


I do have some experience compiling things so I might give this a try. Though, since I'm not so impressed with the EMGD driver anyway, I think I'd like to get Maverick + PSB driver a try first. If that one doesn't have significantly better compiz performance, I'll come back to Natty and the EMGD driver and see if I can't compile the updated evdev driver. I compiled the CrystalHD driver and XBMC on my first attempts with the slate. It was slow, but not impractical.

> 
Sorry for the long winded reply.  It does look like the two drivers are mutually exclusive right now like you said.  Hopefully they can get the xserver-xorg-core updated soon along with its input packages.

Not at all, I greatly appreciate all the help you've given me. I do hope I can get this working and set-up to my liking. I think the slate has some great hardware in it... but it's not powerful enough for a decent inking experience in windows (and I prefer Ubuntu anyway).

---

### Post by cheshirekow on 2011-05-19
New question: when installing Ubuntu 10.10 from a USB stick I get the error the guys in the first page were getting:

```

(initramfs) Unable to find a medium containing a live file system

```

I tried typing "exit" as suggested [URL="http://ubuntuforums.org/showthread.php?t=1332782&page=1"]in this thread[URL], but all I got was a bunch of errors about can't open files, no such file or directory, and

```

Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg

```

Try again and I get what looks like kernel log

[code]
/init: line 326: can't open /root/dev/console: no such file
[  242.543574] Kernel panic - not syncing: Attempted to kill init!
[  242.543658] Pid: 1, comm: init Not tainted 2.6.35-22-generic #33-Ubuntu
...
[code]

Unfortunately I do not have the option of putting together a custom install CD since my other computer is a 64bit machine (so I can't take the xhci.ko from this machine). It looks like the issue has to due with the USB port being USB 3.0. Unfortunately the slate only has 1 port.

Does anyone know how I can fix this without having another 32bit 10.10 machine around? I'll see if I can find a USB cd drive to use and maybe the cd drive will work better (though I suspect, since it's through the same USB, it will be the same).

I suppose if I have no other options, I can install a 32bit virtual machine on my other computer, and use that to make the custom CD... but that sounds like quite a hassle.

---

### Post by Ayuthia on 2011-05-19
> **cheshirekow said:**
> New question: when installing Ubuntu 10.10 from a USB stick I get the error the guys in the first page were getting:

```

(initramfs) Unable to find a medium containing a live file system

```

I tried typing "exit" as suggested [URL="http://ubuntuforums.org/showthread.php?t=1332782&page=1"]in this thread[URL], but all I got was a bunch of errors about can't open files, no such file or directory, and

```

Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg

```

Try again and I get what looks like kernel log

[code]
/init: line 326: can't open /root/dev/console: no such file
[  242.543574] Kernel panic - not syncing: Attempted to kill init!
[  242.543658] Pid: 1, comm: init Not tainted 2.6.35-22-generic #33-Ubuntu
...
[code]

Unfortunately I do not have the option of putting together a custom install CD since my other computer is a 64bit machine (so I can't take the xhci.ko from this machine). It looks like the issue has to due with the USB port being USB 3.0. Unfortunately the slate only has 1 port.

Does anyone know how I can fix this without having another 32bit 10.10 machine around? I'll see if I can find a USB cd drive to use and maybe the cd drive will work better (though I suspect, since it's through the same USB, it will be the same).

I suppose if I have no other options, I can install a 32bit virtual machine on my other computer, and use that to make the custom CD... but that sounds like quite a hassle.

You should be able to get the linux-image from packages.ubuntu.com.  Based on the information from this [site]("http://www.g-loaded.eu/2008/01/28/how-to-extract-rpm-or-deb-packages/"), you can then unpack the .deb file and grab the xhci.ko module from there.  You just need to know the kernel version you are using and download that package.

If I am understanding correctly from this [post]("http://ubuntuforums.org/showpost.php?p=10487073&postcount=24"), you just need to unpack casper/initrd.lz and add the kernel module to /lib/modules and then repackage the initrd.lz file.

---

### Post by cheshirekow on 2011-05-19
Ok, Great-idea. I actually went the virtual-machine-route... but you're right I could have saved time by getting the image package. I followed the path of [gonehiking's post]("http://ubuntuforums.org/showpost.php?p=10487073&postcount=24") but it took me a long time to figure out the relevent parts and it still didn't work. This is the exact process I did, can you spot any errors:

The [Live CD Customization]("https://help.ubuntu.com/community/LiveCDCustomization") community page has comprehensive instructions, but according to gonehiking we only need to add one file to initrd.lz... we don't actually need to change the filesystem or anything. So here's how we do that.

I copied /lib/modules/2.6.35-22-generic/kernel/drivers/usb/host/xhci-hcd.ko from the virtual machine guest (i386) to the host (amd64) (there was no xhci.ko).

On the host, I did the following.

I created a 'working' directory, and put the ubuntu-10.10 image in there. I also put a copy of xhci-hcd.ko in there. Then I did the following, from [Obtain Base System]("https://help.ubuntu.com/community/LiveCDCustomization#Obtain%20the%20base%20system"):

Mount the Desktop .iso

```

cd working
mkdir mnt
sudo mount -o loop ubuntu-10.10-desktop-i386.iso mnt

```

Extract .iso contents into dir 'extract'

```

mkdir extract
rsync -a mnt/ extract

```

Probably we don't need rsync because we don't need to exclude the filesystem. I suppose *cp -a mnt/* extract/* would work just as well.

extract init.lz according to [Removing the Casper Autologin]("https://help.ubuntu.com/community/LiveCDCustomization#Removing%20the%20%28Casper%29%20Autologin")

```

mkdir lztempdir
cd lztempdir
lzma -dc -S .lz ../extract/casper/initrd.lz | cpio -imvd --no-absolute-filenames

```

Add the xhci driver to the archive (there is not "host" folder in drivers/usb)

```

mkdir lib/modules/2.6.35-22-generic/kernel/drivers/usb/host
cp ../xhci-hcd.ko lib/modules/2.6.35-22-generic/kernel/drivers/usb/host/

```

I had to make the old initrd.lz writable

```

cd ..
chmod +w extract
chmod +w extract/casper
chmod +w extract/casper/init.lz
rm extract/casper/init.lz

```

Now archive initrd again

```

cd lztempdir
find . | cpio --quiet --dereference -o -H newc | lzma -7 > ../extract/casper/initrd.lz

```

Create a new checksum (may not be necessary)

```

cd ../extract
chmod +w md5sum.txt
rm md5sum.txt
find -type f -print0 | xargs -0 md5sum | grep -v isolinux/boot.cat | tee md5sum.txt

```

create the image

```

mkisofs -D -r -V "Ubuntu 10.10 with xhci" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../ubuntu-10.10-desktop-i386-xhci.iso .

```

Then I put that image on a USB with the "Startup Disk Creator". When I try to install, I get the same error.

Edit: 
Hm... I wonder if I wrote the correct image to the USB. I'll try again.

---

### Post by Ayuthia on 2011-05-19
I was actually thinking that you can go directly to the usb drive itself, unpack and update the initrd.lz in the casper folder, and then compress it again.  I would think that it would work.

---

### Post by cheshirekow on 2011-05-19
It doesn't seem to help. The init.lz on the usb drive does contain the xhci driver. I noticed [This Post]("http://ubuntuforums.org/showpost.php?p=10472525&postcount=16") on [This Thread]("http://ubuntuforums.org/showthread.php?t=1628665&page=2") where they're talking about similar problems on booting from USB 3.0 device. It looks like he solved the problem by creating a small internal partition and loading from it, but this part looks relevent

> 
I added the following lines:
```

xhci_hcd
usbhid
hid
usb_storage

```
to
/etc/initramfs-tools/modules

/# nano /etc/initramfs-tools/modules

I generated initramfs.
/# mkinitramfs -o /tmp/initramfs-$(uname -r)
/# mv /boot/initrd.img-2.6.35-25-generic-pae /boot/initrd.img-2.6.35-25-generic-pae-backup
/# mv /tmp/initramfs-2.6.35-25-generic-pae /boot/initrd.img-2.6.35-25-generic-pae


I think I will next try this and make another custom install cd.

---

### Post by Ayuthia on 2011-05-19
> **cheshirekow said:**
> It doesn't seem to help. The init.lz on the usb drive does contain the xhci driver. I noticed [This Post]("http://ubuntuforums.org/showpost.php?p=10472525&postcount=16") on [This Thread]("http://ubuntuforums.org/showthread.php?t=1628665&page=2") where they're talking about similar problems on booting from USB 3.0 device. It looks like he solved the problem by creating a small internal partition and loading from it, but this part looks relevent



I think I will next try this and make another custom install cd.

That makes sense.  Since we added the kernel module, we did not tell initrd that we needed to load the module.  So adding it in /etc/initramfs-tools/modules should tell it to load it.

I do recall in the past where I was trying to boot from an SD card and I ended up having to move the initrd portion to the hard drive so that it will know to load the module and use the card reader.  It then loaded the rest from the SD card.  It has been a while since I tried it though.

---

### Post by cheshirekow on 2011-05-20
Man, I really thought that was going to work. But, alas, it did not. 

I did this on a different machine so this time I downloaded linux-image-2.6.35-22 from [packages.ubuntu.com]("http://packages.ubuntu.com/maverick-updates/i386/linux-image-2.6.35-22-generic/download") as suggested by Ayuthia. I opened the .deb package in archive manager, and then opened the data.tar.bz2 file in archive manager. Then I copied lib/modules/2.6.35-22-generic/kernels/drivers/usb/host/xhci-hcd.ko to the the 'working' directory.

This time after adding the xhci-hcd.ko driver file to lztempdir, I also edited lztempdir/conf/modules, adding "xhci-hcd" to the list.

Then I repackaged the iso the same way as before. Yet I still got the same error about not finding a filesystem.

So, here is my understanding of the boot process and why I thought this would work. Can anyone tell me what is wrong with this understanding:

[List="1"]
[*]BIOS loads the bootloader
[*]The boot loader loads the linux kernel from isolinux/ and some how passes it casper/initrd.lz
[*]Linux boots up using initrd.lz (which now contains xhci-hcd.ko) and, in the process, creates an initial RAM filesystem (initramfs)
[*]It presents the ubuntu 10.10 loading screen (the animated dots) while it's unpacking initrd.lz and setting up, and then the installer options screen (the blank screen with the accessability icon at the bottom where you can change language and things)
[*]It then attempts to mount the filesystem at <install media>/casper/filesystem.squashfs, but can't find it
[/List]

When I boot from the USB drive (note, also from an SD cars) it makes it through (4)... but does not make it through (5). This is where it drops to a busybox shell with the error about not finding a filesystem. 

It's my understanding that since bootloader initially loads the kernel and supplies it with initrd.lz, that the bootloader can read from the USB drive fine. Then, there is not "seeking of things on the install media" by linux until after the install (language) options screen. However, it can't do that because the kernel doesn't know how to communicate with USB 3.0 devices because it hasn't loaded the xhci driver. Since I edited initrd.lz/conf/modules and added the xhci driver, I thought the kernel *would* be able to read from the device.

Any ideas what is wrong with that?

---

### Post by cheshirekow on 2011-05-21
On more try, still didn't work. This time I tried generating init.lz using mkinitramfs from within a chroot of the installation filesystem, after adding the xchi driver to /etc/initramfs-tools/modules. 

One thing that was weird was that mkinitramfs used gzip to compress the init ram-disk image (i.e. it creates initrd.gz not initrd.lz). So... I extracted the contents and repacked them with lzma. Before repacking, I checked the contents of the conf/modules file and it *did* contain the xhci driver.

I tested the iso in a virtual machine to make sure it works, and it booted up to the installation screen just fine. However, on the slate, it still gets stuck, after the language screen, with the same error about not finding a live file system.

I'm pretty much out of ideas and would appreciate any further suggestions.

---

### Post by cheshirekow on 2011-05-21
Latest attempt. From the virtual machine I chrooted into the usquashed filesystem. Then I ran aptitude update, upgrade to upgrade all packages. Then I copied the kernel 2.6.35-28-generic to /casper/vmlinuz, along with the initrd.lz. 

The resulting ISO boots up fine in the virtual machine, but does not on the HP Slate.

Edit:
Also tried making the startup disk from within the virtual machine (maybe using lucid's startup disk creator isn't the best idea). Unfortunately, that did not work either.  My next idea is to try and use the Natty boot loader. I'm not sure exactly how to do that. I plan to extract the Natty install cd, then replace the filesystem.squashfs with the one from the maverick install cd. We'll see how that goes.

---

### Post by cheshirekow on 2011-05-21
Hey! That seems to have worked :). 
So basically this is what I did:
[list="1"]
[*]mount and extract Natty install cd
[*]unmount
[*]mount Maverick CD
[*]copied casper/filesystem.* to the directory of the extracted natty cd
[*]made an ISO from the extract directory
[*]made a USB stick from that iso
[/list]

(Actually not really, I was using the filesystem.* from what I was working on, which actually had updated packages and updated initramfs-tools/modules and things, as I mentioned in previous posts... I'll try again later with a fresh set of files and see if that actually works, or if you really need to extract the filesystem, update packages, and update initramfs).

When I booted everything said 11.04 (even the install icon) but when I clicked on it the windows were all saying 10.10. When I booted into the system after installing it says it's 10.10. The only weird thing is it appears like the 11.04 kernal and init ramdisk image are both in /boot. So I removed both of those and ran update-grub. Then I installed the network drivers following [gonehiking's post]("http://ubuntuforums.org/showpost.php?p=10487073&postcount=24"). 

I will update on the PSB driver and other things as I try them out. So far, the touch input (even single-touch) isn't working at all.

Edit:
Did it again and it looks like it's not quite that simple. Evidently /boot get's it's vmlinuz and initrd image from the install cd, so you'll have to copy the kernel and ramdisk image from the maverick install cd into the unsquashed filesystem at /boot, resquash, and then add the image to the natty cd.

Edit 2:
Since the install puts the 2.6.38-8 in the filesystem, you should also run 'sudo update-initramfs -d -k 2.6.38-8-generic' which will delete the init ramdisk for that kernel and will make update-initramfs forget about it so that the next time you install a package it wont try to create an initramfs for 2.6.38-8. Otherwise, any packages that require update-initramfs will fail to install correctly (actually you'll just have to run the command manually specifing -k `uname -r`... but still, it's better to be clean I think).

---

### Post by Ayuthia on 2011-05-21
Have you tried copying the intramfs over to /boot on the slate and point the vmlinuz on the USB/SD (in GRUB)?  I was going to try something like that over here with my tablet, but I have not had a chance.

EDIT: Nevermind.  It looks like you have it working!

---

### Post by cheshirekow on 2011-05-21
> **Ayuthia said:**
> Have you tried copying the intramfs over to /boot on the slate and point the vmlinuz on the USB/SD (in GRUB)?  I was going to try something like that over here with my tablet, but I have not had a chance.

EDIT: Nevermind.  It looks like you have it working!

Yup. I've got maverick up! It looks like touch isn't working (though pen seems to be working fine, and on the wacom driver). You mentioned that the latest evdev driver had new code for multi-touch, do you think I need to compile that from source to make it work?

---

### Post by Favux on 2011-05-21
From Ubuntu source?

---

### Post by cheshirekow on 2011-05-21
> **Favux said:**
> From Ubuntu source?

Actually, I'm not really sure where to get the source :/. I can't find anything like the wacom project's webpage for evdev. The most up-to-date evdev for Maverick appears to be 1:2.3.2, whereas the most up-to-date one for Natty appears to be 1:2.6.0. 

Maybe switching to Maverick and PSB driver wont change anything... since I can't get the evdev driver that I need :/.

Edit:
Ugh... Nevermind. The PSB driver doesn't work anyway. I get the same problem that aquarat was having in 10.04... the system freezes after the Ubuntu animated dots :(

---

### Post by Favux on 2011-05-21
Here's the evdev site:  [http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/](http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/)

I'm just thinking there's a chance Ubuntu has tweaks to their Natty version.  Ayuthia probably knows.

---

### Post by Ayuthia on 2011-05-21
You will need to get the source from Ubuntu (packages.ubuntu.com) because the evdev driver does contain some additional libraries that the evdev git does not have.  However I thought that utouch in Maverick worked.

Are you just using the original stuff from Ubuntu and have not installed any additional graphics drivers?

---

### Post by cheshirekow on 2011-05-21
> **Ayuthia said:**
> You will need to get the source from Ubuntu (packages.ubuntu.com) because the evdev driver does contain some additional libraries that the evdev git does not have.  However I thought that utouch in Maverick worked.

Are you just using the original stuff from Ubuntu and have not installed any additional graphics drivers?

I did install the PSB driver, but that did not require any package changes like the EMGD driver did. I removed that anyway because it didn't work. utouch may work, but whatever the difference is between evdev 2.3.0 and 2.6.0 is must be the difference between multitouch working and not-working on this particular hardware. I think the best bet is to stick with Natty, and try to either: 1) get EMGD to compile against xorg 1.9.99 so that I can use the default evdev package or 2) get evdev 1.2.6 to compile against xorg 1.9.0 so I can use the default xorg paired with EMGD.

Since the PSB driver didn't work, I have no reason to stick to Maverick. The whole point of that experiment was to use the PSB driver instead of the EMGD :/.

---

### Post by aquarat on 2011-05-22
> **cheshirekow said:**
> 
Ugh... Nevermind. The PSB driver doesn't work anyway. I get the same problem that aquarat was having in 10.04... the system freezes after the Ubuntu animated dots :(

Sorry I haven't been more responsive... from what I remember the machine didn't freeze, it was still accessible using ssh, not sure how what was possible.

---

### Post by cheshirekow on 2011-05-23
> **aquarat said:**
> Sorry I haven't been more responsive... from what I remember the machine didn't freeze, it was still accessible using ssh, not sure how what was possible.

No problem. Probably mine was the same, (could probably still SSH in)... but it doesn't matter. Maverick + PSB wouldn't have allowed multi-touch so even if the PSB driver DID work (which it didn't) it still wouldn't have given me what I want.

---

### Post by cheshirekow on 2011-05-23
Ok, I downloaded the source xf86-input-evdev-2.6.0 from [ packages.ubuntu.com]("http://packages.ubuntu.com/source/natty/xserver-xorg-input-evdev"). I applied the patches that were also part of that source package. I configured and compiled without errors. I installed and rebooted, but multi-touch still isn't working.

Some notes: I configured with
```

./configure --prefix=/usr

```

and before installing I backed up the current evdev driver. So the whole process (from a fresh install of Natty) went like this

```

sudo apt-add-repository ppa:gma500/emgd
sudo apt-add-repository ppa:thopiekar/emgd
sudp apt-get update
sudo apt-get install xorg-emgd emgd-dkms
sudo apt-get upgrade
sudo emgd-xorg-conf
sudo apt-get install xserver-xorg-input-wacom
sudo shutdown -r now

```

after reboot

```

cd Codes
tar xvzf xserver-xorg-input-evdev_2.6.0.orig.tar.gz
gunzip xserver-xorg-input-evdev_2.6.0-1ubuntu12.diff.gz
cd xf86-input-evdev-2.6.0
patch -p0 < ../xserver-xorg-input-evdev_2.6.0-1ubuntu12.diff
sudo cp /usr/lib/xorg/modules/input/evdev_drv.so /usr/lib/xorg/modules/input/evdev_drv.so.emgdppa
./configure --prefix=/usr
make
sudo make install
sudo shutdown -r now

```

So, perhaps it's not just the downgraded evdev driver, but the downgraded xserver itself?

---

### Post by cheshirekow on 2011-05-23
Ok, well, since it appears I absolutely need xserver 1.10 that means the only chance I have is with the PSB driver... so I'm back on maverick and I've installed the PSB driver and now I need to figure out what's wrong. So after installation the GRUB menu and the Ubuntu loading dots are both "prettier" (higher resolution, at least) so I'm guessing that means the kernel driver is working. All I get is a blank screen after the ubuntu dots though (so I guess this means X is crashing). Does anyone know how to start troubleshooting this?

---

### Post by Favux on 2011-05-23
Have you tried the kernel line option 'nomodeset'?

---

### Post by cheshirekow on 2011-05-23
> **Favux said:**
> Have you tried the kernel line option 'nomodeset'?

Great idea, I should have thought of that. Unfortunately, it appears to already be set (I went to edit it in grub and it was already in there). But since I just looked at it, I figured I would go ahead and write down what else was there in case it hints at any problems, since all the word I've done in grub before had much less:

```

recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set af393f32-41c2-4ccf-9bbf-b296d8a2ce5b
linux /boot/vmlinuz-2.6.35-28-generic root=UUID=af393f32-41c2-4ccf-9bbf-b296d8a2ce5b ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb quiet splash
initrd /boot/initrd.img-2.6.35-28-generic

```

Edit:
Is it supposed to say vesa? I thought vesa was a different video driver?

Edit 2:
Surprisingly, ctrl+alt+shift+f<x> does not drop me to a shell

---

### Post by Favux on 2011-05-23
You have me confused.  That is not a Grub2 /etc/default/grub start up file.  Isn't Maverick suppose to be using Grub2?

And I agree a generic VESA video driver is not the way to go if you have an option.  It tends to limit resolution and performance.  But if nothing else gets X to start...  Of course X isn't starting.

---

### Post by cheshirekow on 2011-05-24
> **Favux said:**
> You have me confused.  That is not a Grub2 /etc/default/grub start up file.  Isn't Maverick suppose to be using Grub2

This is the result of pressing 'e' at the grub boot prompt where it lists the installed kernels.

---

### Post by cheshirekow on 2011-05-24
Here's a little more info. 

With a normal boot, I get a blank screen after the ubuntu loading dots. If I press the power button during this blank screen, I get the ubuntu shutting-down-dots and the computer shuts down.

If I select "recovery mode" from the grub boot menu, and then choose the "failsafe x" option, I get a blank screen with a cursor in the top left. If I press the power button, nothing happens.

By selecting "recovery mode" and dropping to a root shell I was able to look at the following:

/etc/X11/xorg.conf
```

Section "DRI"
    Mode    0666
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "psb"
EndSection

```

/etc/X11/xorg.conf.failsafe
```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

And I copied the logs from /var/log to a USB stick

/var/log/Xorg.0.log
```

[    20.461] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    20.461] X Protocol Version 11, Revision 0
[    20.461] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    20.461] Current Operating System: Linux Clare 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686
[    20.461] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=af393f32-41c2-4ccf-9bbf-b296d8a2ce5b ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb quiet splash
[    20.461] Build Date: 09 January 2011  12:14:58PM
[    20.462] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    20.462] Current version of pixman: 0.18.4
[    20.462] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    20.462] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.462] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 24 10:23:39 2011
[    20.462] (==) Using config file: "/etc/X11/xorg.conf"
[    20.462] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.464] (==) No Layout section.  Using the first Screen section.
[    20.464] (==) No screen section available. Using defaults.
[    20.464] (**) |-->Screen "Default Screen Section" (0)
[    20.464] (**) |   |-->Monitor "<default monitor>"
[    20.464] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    20.465] (**) |   |-->Device "Configured Video Device"
[    20.465] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    20.465] (==) Automatically adding devices
[    20.465] (==) Automatically enabling devices
[    20.465] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.465] 	Entry deleted from font path.
[    20.465] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    20.465] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.465] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.465] (II) Loader magic: 0x81f9b00
[    20.466] (II) Module ABI versions:
[    20.466] 	X.Org ANSI C Emulation: 0.4
[    20.466] 	X.Org Video Driver: 8.0
[    20.466] 	X.Org XInput driver : 11.0
[    20.466] 	X.Org Server Extension : 4.0
[    20.467] (--) PCI:*(0:0:2:0) 8086:8108:103c:145a rev 7, Mem @ 0x94000000/524288, 0x80000000/268435456, 0x94080000/262144, I/O @ 0x00004070/8
[    20.467] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.467] (II) LoadModule: "extmod"
[    20.471] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.471] (II) Module extmod: vendor="X.Org Foundation"
[    20.471] 	compiled for 1.9.0, module version = 1.0.0
[    20.471] 	Module class: X.Org Server Extension
[    20.471] 	ABI class: X.Org Server Extension, version 4.0
[    20.471] (II) Loading extension MIT-SCREEN-SAVER
[    20.471] (II) Loading extension XFree86-VidModeExtension
[    20.471] (II) Loading extension XFree86-DGA
[    20.471] (II) Loading extension DPMS
[    20.471] (II) Loading extension XVideo
[    20.471] (II) Loading extension XVideo-MotionCompensation
[    20.471] (II) Loading extension X-Resource
[    20.471] (II) LoadModule: "dbe"
[    20.472] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.473] (II) Module dbe: vendor="X.Org Foundation"
[    20.473] 	compiled for 1.9.0, module version = 1.0.0
[    20.473] 	Module class: X.Org Server Extension
[    20.473] 	ABI class: X.Org Server Extension, version 4.0
[    20.473] (II) Loading extension DOUBLE-BUFFER
[    20.473] (II) LoadModule: "glx"
[    20.474] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.474] (II) Module glx: vendor="X.Org Foundation"
[    20.474] 	compiled for 1.9.0, module version = 1.0.0
[    20.474] 	ABI class: X.Org Server Extension, version 4.0
[    20.474] (==) AIGLX enabled
[    20.474] (II) Loading extension GLX
[    20.474] (II) LoadModule: "record"
[    20.475] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.475] (II) Module record: vendor="X.Org Foundation"
[    20.475] 	compiled for 1.9.0, module version = 1.13.0
[    20.475] 	Module class: X.Org Server Extension
[    20.475] 	ABI class: X.Org Server Extension, version 4.0
[    20.475] (II) Loading extension RECORD
[    20.476] (II) LoadModule: "dri"
[    20.476] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.479] (II) Module dri: vendor="X.Org Foundation"
[    20.479] 	compiled for 1.9.0, module version = 1.0.0
[    20.479] 	ABI class: X.Org Server Extension, version 4.0
[    20.479] (II) Loading extension XFree86-DRI
[    20.479] (II) LoadModule: "dri2"
[    20.480] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.481] (II) Module dri2: vendor="X.Org Foundation"
[    20.481] 	compiled for 1.9.0, module version = 1.2.0
[    20.481] 	ABI class: X.Org Server Extension, version 4.0
[    20.481] (II) Loading extension DRI2
[    20.481] (II) LoadModule: "psb"
[    20.481] (II) Loading /usr/lib/xorg/modules/drivers/psb_drv.so
[    20.486] (II) Module psb: vendor="X.Org Foundation"
[    20.486] 	compiled for 1.9.0, module version = 0.32.0
[    20.486] 	Module class: X.Org Video Driver
[    20.486] 	ABI class: X.Org Video Driver, version 8.0
[    20.486] (II) PSB: driver for Intel GMA500 chipsets: Intel GMA500
[    20.487] (++) using VT number 7

[    20.511] (WW) Falling back to old probe method for psb
[    20.511] (--) Assigning device section with no busID to primary device
[    20.513] (--) Chipset Intel GMA500 found
[    20.513] (II) PSB(0): psb_drv - 2.2.0.32L.0027
[    20.513] (II) Loading sub module "vbe"
[    20.513] (II) LoadModule: "vbe"
[    20.514] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    20.515] (II) Module vbe: vendor="X.Org Foundation"
[    20.515] 	compiled for 1.9.0, module version = 1.1.0
[    20.515] 	ABI class: X.Org Video Driver, version 8.0
[    20.515] (II) PSB(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    20.515] (==) PSB(0): Depth 24, (--) framebuffer bpp 32
[    20.515] (II) Loading sub module "fb"
[    20.515] (II) LoadModule: "fb"
[    20.517] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.517] (II) Module fb: vendor="X.Org Foundation"
[    20.517] 	compiled for 1.9.0, module version = 1.0.0
[    20.517] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    20.518] (--) PSB(0): Linear framebuffer at 0x0
[    20.518] (==) PSB(0): RGB weight 888
[    20.518] (==) PSB(0): Default visual is TrueColor
[    20.518] (==) PSB(0): Use hardware cursor.
[    20.518] (==) PSB(0): Not using ACPI for LVDS detection.
[    20.518] (II) Loading sub module "dri"
[    20.518] (II) LoadModule: "dri"
[    20.519] (II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
[    20.519] (II) Loading sub module "Xpsb"
[    20.519] (II) LoadModule: "Xpsb"
[    20.520] (II) Loading /usr/lib/xorg/modules/drivers/Xpsb.so
[    20.522] (II) Module Xpsb: vendor="Tungsten Graphics Inc."
[    20.522] 	compiled for 1.6.0, module version = 0.1.0
[    20.523] (II) Loading sub module "vgahw"
[    20.523] (II) LoadModule: "vgahw"
[    20.524] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    20.526] (II) Module vgahw: vendor="X.Org Foundation"
[    20.526] 	compiled for 1.9.0, module version = 0.1.0
[    20.526] 	ABI class: X.Org Video Driver, version 8.0
[    20.526] (--) PSB(0): Mapped PCI MMIO at physical address 0x94000000
	with size 512 kiB
[    20.527] (EE) PSB(0): the stolenBase is:0x7f800000
[    20.527] (--) PSB(0): Detected 7932 kiB of "stolen" memory set aside as video RAM.
[    20.527] (EE) PSB(0): screnIndex is:0;fbPhys is:0x7f800000; fbsize is:0x007bf000
[    20.532] (--) PSB(0): Mapped graphics aperture at physical address 0x7f800000
	with size 7 MiB
[    20.532] (II) PSB(0): Poulsbo MemClock 533, CoreClock 200
[    20.532] (II) PSB(0): Poulsbo Latencies 324 744 210 450
[    20.533] (II) PSB(0): sku_value is 0x00800000, sku_bSDVOEnable is 1, sku_bMaxResEnableInt is 0
[    20.533] (II) PSB(0): Output LVDS0 has no monitor section
[    20.533] (II) PSB(0): I2C bus "LVDSBLC_B" initialized.
[    20.533] (II) PSB(0): I2C bus "LVDSDDC_C" initialized.
[    20.533] (II) PSB(0): I2C device "LVDSBLC_B:BLC Control" registered at address 0x58.
[    20.533] (II) PSB(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
[    20.589] (II) PSB(0): EDID for output LVDS0
[    20.589] (II) PSB(0): Manufacturer: CMO  Model: 903  Serial#: 0
[    20.589] (II) PSB(0): Year: 2008  Week: 45
[    20.589] (II) PSB(0): EDID Version: 1.3
[    20.589] (II) PSB(0): Digital Display Input
[    20.589] (II) PSB(0): Max Image Size [cm]: horiz.: 21  vert.: 12
[    20.589] (II) PSB(0): Gamma: 2.20
[    20.589] (II) PSB(0): No DPMS capabilities specified
[    20.589] (II) PSB(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.590] (II) PSB(0): First detailed timing is preferred mode
[    20.590] (II) PSB(0): redX: 0.571 redY: 0.360   greenX: 0.351 greenY: 0.573
[    20.590] (II) PSB(0): blueX: 0.156 blueY: 0.118   whiteX: 0.313 whiteY: 0.329
[    20.590] (II) PSB(0): Manufacturer's mask: 0
[    20.590] (II) PSB(0): Supported detailed timing:
[    20.590] (II) PSB(0): clock: 54.2 MHz   Image Size:  195 x 113 mm
[    20.590] (II) PSB(0): h_active: 1024  h_sync: 1077  h_sync_end 1112 h_blank_end 1200 h_border: 0
[    20.590] (II) PSB(0): v_active: 600  v_sync: 607  v_sync_end 620 v_blanking: 753 v_border: 0
[    20.590] (II) PSB(0):  N089L6-L03
[    20.590] (II) PSB(0):  CMO
[    20.590] (II) PSB(0):  N089L6-L03
[    20.590] (II) PSB(0): EDID (in hex):
[    20.590] (II) PSB(0): 	00ffffffffffff000daf030900000000
[    20.590] (II) PSB(0): 	2d12010380150c780a5f15925c599228
[    20.590] (II) PSB(0): 	1e505400000001010101010101010101
[    20.590] (II) PSB(0): 	0101010101012c1500b0405899203523
[    20.590] (II) PSB(0): 	7d00c37100000018000000fe004e3038
[    20.590] (II) PSB(0): 	394c362d4c30330a2020000000fe0043
[    20.590] (II) PSB(0): 	4d4f0a202020202020202020000000fe
[    20.590] (II) PSB(0): 	004e3038394c362d4c30330a202000fd
[    20.590] (II) PSB(0): EDID vendor "CMO", prod id 2307
[    20.590] (II) PSB(0): Printing DDC gathered Modelines:
[    20.591] (II) PSB(0): Modeline "1024x600"x0.0   54.20  1024 1077 1112 1200  600 607 620 753 -hsync -vsync (45.2 kHz)
[    20.591] (II) PSB(0): EDID vendor "CMO", prod id 2307
[    20.591] (II) Loading sub module "int10"
[    20.591] (II) LoadModule: "int10"
[    20.591] (II) Loading /usr/lib/xorg/modules/libint10.so
[    20.592] (II) Module int10: vendor="X.Org Foundation"
[    20.592] 	compiled for 1.9.0, module version = 1.0.0
[    20.592] 	ABI class: X.Org Video Driver, version 8.0
[    20.592] (II) PSB(0): initializing int10
[    20.599] (II) PSB(0): Bad V_BIOS checksum
[    20.600] (II) PSB(0): Primary V_BIOS segment is: 0xc000
[    20.600] (II) PSB(0): VESA BIOS detected
[    20.600] (II) PSB(0): VESA VBE Version 3.0
[    20.600] (II) PSB(0): VESA VBE Total Mem: 7872 kB
[    20.601] (II) PSB(0): VESA VBE OEM: Intel(r)SCH Chipset Family Graphics Chip Accelerated VGA BIOS
[    20.601] (II) PSB(0): VESA VBE OEM Software Rev: 1.0
[    20.601] (II) PSB(0): VESA VBE OEM Vendor: Intel Corporation
[    20.601] (II) PSB(0): VESA VBE OEM Product: Intel(r)SCH Chipset Family Graphics Controller
[    20.601] (II) PSB(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    20.602] (II) PSB(0): Found panel mode in BIOS VBT tables:
[    20.602] (II) PSB(0): Modeline "1024x600"x0.0   54.20  1024 1077 1112 1200  600 607 620 753 (45.2 kHz)
[    20.602] (II) PSB(0): BLC Data in BIOS VBT tables: datasize=0 paneltype=6                      type=0x02 pol=0x00 freq=0x00c8 minlevel=0x14                         i2caddr=0x58 cmd=0xaa 
[    20.602] (WW) PSB(0): BIOS panel mode data doesn't match probed data, continuing with probed.
[    20.602] (II) PSB(0): BIOS mode:
[    20.602] (II) PSB(0): Modeline "1024x600"x0.0   54.20  1024 1077 1112 1200  600 607 620 753 (45.2 kHz)
[    20.602] (II) PSB(0): probed mode:
[    20.602] (II) PSB(0): Modeline "1024x600"x0.0   54.20  1024 1077 1112 1200  600 607 620 753 -hsync -vsync (45.2 kHz)
[    20.602] xf86TokenToOptinfo: table is NULL
[    20.602] (II) PSB(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
[    20.602] (II) PSB(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
[    20.666] (II) PSB(0): I2C bus "SDVOB DDC Bus" initialized.
[    20.688] (II) PSB(0): Output SDVO-1 has no monitor section
[    20.700] (II) PSB(0): SDVO device VID/DID: 04:AE.00, clock range 25.0MHz - 165.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
[    20.700] (++) PSB(0): i830_psbSaveHWState
[    20.703] (II) PSB(0): Current clock rate multiplier: 1
[    20.862] (==) PSB(0): Shadow framebuffer disabled
[    20.862] (II) Loading sub module "exa"
[    20.862] (II) LoadModule: "exa"
[    20.863] (II) Loading /usr/lib/xorg/modules/libexa.so
[    20.865] (II) Module exa: vendor="X.Org Foundation"
[    20.866] 	compiled for 1.9.0, module version = 2.5.0
[    20.866] 	ABI class: X.Org Video Driver, version 8.0
[    20.866] (==) PSB(0): Acceleration enabled
[    20.866] (==) PSB(0): [EXA] Allocate 32768 kiB for EXA pixmap cache.
[    20.866] (==) PSB(0): [EXA] Allocate 4 kiB for scratch memory.
[    20.866] (II) PSB(0): Output "SDVO-1" is assigned to this screen.
[    20.866] (II) PSB(0): Output "LVDS0" is assigned to this screen.
[    20.866] (II) PSB(0): Searching for matching Poulsbo mode(s):
[    20.923] (II) PSB(0): EDID for output LVDS0
[    20.923] (II) PSB(0): Manufacturer: CMO  Model: 903  Serial#: 0
[    20.923] (II) PSB(0): Year: 2008  Week: 45
[    20.923] (II) PSB(0): EDID Version: 1.3
[    20.923] (II) PSB(0): Digital Display Input
[    20.923] (II) PSB(0): Max Image Size [cm]: horiz.: 21  vert.: 12
[    20.923] (II) PSB(0): Gamma: 2.20
[    20.923] (II) PSB(0): No DPMS capabilities specified
[    20.923] (II) PSB(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.923] (II) PSB(0): First detailed timing is preferred mode
[    20.923] (II) PSB(0): redX: 0.571 redY: 0.360   greenX: 0.351 greenY: 0.573
[    20.923] (II) PSB(0): blueX: 0.156 blueY: 0.118   whiteX: 0.313 whiteY: 0.329
[    20.923] (II) PSB(0): Manufacturer's mask: 0
[    20.924] (II) PSB(0): Supported detailed timing:
[    20.924] (II) PSB(0): clock: 54.2 MHz   Image Size:  195 x 113 mm
[    20.924] (II) PSB(0): h_active: 1024  h_sync: 1077  h_sync_end 1112 h_blank_end 1200 h_border: 0
[    20.924] (II) PSB(0): v_active: 600  v_sync: 607  v_sync_end 620 v_blanking: 753 v_border: 0
[    20.924] (II) PSB(0):  N089L6-L03
[    20.924] (II) PSB(0):  CMO
[    20.924] (II) PSB(0):  N089L6-L03
[    20.924] (II) PSB(0): EDID (in hex):
[    20.924] (II) PSB(0): 	00ffffffffffff000daf030900000000
[    20.924] (II) PSB(0): 	2d12010380150c780a5f15925c599228
[    20.924] (II) PSB(0): 	1e505400000001010101010101010101
[    20.924] (II) PSB(0): 	0101010101012c1500b0405899203523
[    20.924] (II) PSB(0): 	7d00c37100000018000000fe004e3038
[    20.924] (II) PSB(0): 	394c362d4c30330a2020000000fe0043
[    20.925] (II) PSB(0): 	4d4f0a202020202020202020000000fe
[    20.925] (II) PSB(0): 	004e3038394c362d4c30330a202000fd
[    20.925] (II) PSB(0): EDID vendor "CMO", prod id 2307
[    20.925] (II) PSB(0): Printing DDC gathered Modelines:
[    20.925] (II) PSB(0): Modeline "1024x600"x0.0   54.20  1024 1077 1112 1200  600 607 620 753 -hsync -vsync (45.2 kHz)
[    20.925] (II) PSB(0): EDID vendor "CMO", prod id 2307
[    20.925] (II) PSB(0): Printing probed modes for output LVDS0
[    20.925] (II) PSB(0): Modeline "1024x600"x60.0   54.20  1024 1077 1112 1200  600 607 620 753 -hsync -vsync (45.2 kHz)
[    20.976] (EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
[    21.015] (II) PSB(0): EDID for output SDVO-1
[    21.015] (II) PSB(0): Output LVDS0 connected
[    21.015] (II) PSB(0): Output SDVO-1 disconnected
[    21.015] (II) PSB(0): Using exact sizes for initial modes
[    21.015] (II) PSB(0): Output LVDS0 using initial mode 1024x600
[    21.015] (II) PSB(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.015] (**) PSB(0): Display dimensions: (210, 120) mm
[    21.015] (**) PSB(0): DPI set to (123, 216)
[    21.015] (--) Depth 24 pixmap format is 32 bpp
[    21.015] drmOpenDevice: node name is /dev/dri/card0
[    21.022] drmOpenDevice: open result is -1, (No such device or address)
[    21.028] drmOpenDevice: open result is -1, (No such device or address)
[    21.028] drmOpenDevice: Open failed
[    21.028] drmOpenDevice: node name is /dev/dri/card0
[    21.034] drmOpenDevice: open result is -1, (No such device or address)
[    21.039] drmOpenDevice: open result is -1, (No such device or address)
[    21.039] drmOpenDevice: Open failed
[    21.236] [drm] failed to load kernel module "psb"
[    21.236] (EE) [drm] drmOpen failed.
[    21.236] (EE) PSB(0): [dri] DRIScreenInit failed. Disabling DRI.
[    21.236] (EE) [drm] Could not uninstall irq handler.
[    21.236] (EE) PSB(0): This driver currently needs DRM to operate.
[    21.236] 
Fatal server error:
[    21.236] AddScreen/ScreenInit failed for driver 0
[    21.236] 
[    21.236] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    21.236] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    21.236] 
[    21.634]  ddxSigGiveUp: Closing log

```

/var/log/Xorg.1.log
```

[    21.689] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    21.689] X Protocol Version 11, Revision 0
[    21.689] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    21.689] Current Operating System: Linux Clare 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686
[    21.689] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=af393f32-41c2-4ccf-9bbf-b296d8a2ce5b ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb quiet splash
[    21.690] Build Date: 09 January 2011  12:14:58PM
[    21.690] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    21.690] Current version of pixman: 0.18.4
[    21.690] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.690] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.690] (==) Log file: "/var/log/Xorg.1.log", Time: Tue May 24 10:23:40 2011
[    21.690] (==) Using config file: "/etc/X11/xorg.conf"
[    21.690] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.691] (==) No Layout section.  Using the first Screen section.
[    21.691] (==) No screen section available. Using defaults.
[    21.691] (**) |-->Screen "Default Screen Section" (0)
[    21.691] (**) |   |-->Monitor "<default monitor>"
[    21.692] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    21.692] (**) |   |-->Device "Configured Video Device"
[    21.692] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    21.692] (==) Automatically adding devices
[    21.692] (==) Automatically enabling devices
[    21.692] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.692] 	Entry deleted from font path.
[    21.692] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.692] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.692] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.692] (II) Loader magic: 0x81f9b00
[    21.692] (II) Module ABI versions:
[    21.692] 	X.Org ANSI C Emulation: 0.4
[    21.692] 	X.Org Video Driver: 8.0
[    21.692] 	X.Org XInput driver : 11.0
[    21.692] 	X.Org Server Extension : 4.0
[    21.694] (--) PCI:*(0:0:2:0) 8086:8108:103c:145a rev 7, Mem @ 0x94000000/524288, 0x80000000/268435456, 0x94080000/262144, I/O @ 0x00004070/8
[    21.694] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.694] (II) LoadModule: "extmod"
[    21.695] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.696] (II) Module extmod: vendor="X.Org Foundation"
[    21.696] 	compiled for 1.9.0, module version = 1.0.0
[    21.696] 	Module class: X.Org Server Extension
[    21.696] 	ABI class: X.Org Server Extension, version 4.0
[    21.696] (II) Loading extension MIT-SCREEN-SAVER
[    21.696] (II) Loading extension XFree86-VidModeExtension
[    21.696] (II) Loading extension XFree86-DGA
[    21.696] (II) Loading extension DPMS
[    21.696] (II) Loading extension XVideo
[    21.696] (II) Loading extension XVideo-MotionCompensation
[    21.696] (II) Loading extension X-Resource
[    21.696] (II) LoadModule: "dbe"
[    21.697] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.697] (II) Module dbe: vendor="X.Org Foundation"
[    21.697] 	compiled for 1.9.0, module version = 1.0.0
[    21.697] 	Module class: X.Org Server Extension
[    21.697] 	ABI class: X.Org Server Extension, version 4.0
[    21.698] (II) Loading extension DOUBLE-BUFFER
[    21.698] (II) LoadModule: "glx"
[    21.698] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.699] (II) Module glx: vendor="X.Org Foundation"
[    21.699] 	compiled for 1.9.0, module version = 1.0.0
[    21.699] 	ABI class: X.Org Server Extension, version 4.0
[    21.699] (==) AIGLX enabled
[    21.699] (II) Loading extension GLX
[    21.699] (II) LoadModule: "record"
[    21.700] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.700] (II) Module record: vendor="X.Org Foundation"
[    21.700] 	compiled for 1.9.0, module version = 1.13.0
[    21.700] 	Module class: X.Org Server Extension
[    21.700] 	ABI class: X.Org Server Extension, version 4.0
[    21.700] (II) Loading extension RECORD
[    21.700] (II) LoadModule: "dri"
[    21.701] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.702] (II) Module dri: vendor="X.Org Foundation"
[    21.702] 	compiled for 1.9.0, module version = 1.0.0
[    21.702] 	ABI class: X.Org Server Extension, version 4.0
[    21.702] (II) Loading extension XFree86-DRI
[    21.702] (II) LoadModule: "dri2"
[    21.703] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.703] (II) Module dri2: vendor="X.Org Foundation"
[    21.703] 	compiled for 1.9.0, module version = 1.2.0
[    21.703] 	ABI class: X.Org Server Extension, version 4.0
[    21.703] (II) Loading extension DRI2
[    21.703] (II) LoadModule: "psb"
[    21.703] (II) Loading /usr/lib/xorg/modules/drivers/psb_drv.so
[    21.704] (II) Module psb: vendor="X.Org Foundation"
[    21.704] 	compiled for 1.9.0, module version = 0.32.0
[    21.704] 	Module class: X.Org Video Driver
[    21.704] 	ABI class: X.Org Video Driver, version 8.0
[    21.704] (II) PSB: driver for Intel GMA500 chipsets: Intel GMA500
[    21.704] (--) using VT number 7

[    21.730] (WW) Falling back to old probe method for psb
[    21.730] (--) Assigning device section with no busID to primary device
[    21.730] (--) Chipset Intel GMA500 found
[    21.730] (II) PSB(0): psb_drv - 2.2.0.32L.0027
[    21.730] (II) Loading sub module "vbe"
[    21.730] (II) LoadModule: "vbe"
[    21.731] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    21.732] (II) Module vbe: vendor="X.Org Foundation"
[    21.732] 	compiled for 1.9.0, module version = 1.1.0
[    21.732] 	ABI class: X.Org Video Driver, version 8.0
[    21.732] (II) PSB(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    21.732] (==) PSB(0): Depth 24, (--) framebuffer bpp 32
[    21.732] (II) Loading sub module "fb"
[    21.732] (II) LoadModule: "fb"
[    21.734] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.734] (II) Module fb: vendor="X.Org Foundation"
[    21.734] 	compiled for 1.9.0, module version = 1.0.0
[    21.734] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.734] (--) PSB(0): Linear framebuffer at 0x0
[    21.734] (==) PSB(0): RGB weight 888
[    21.735] (==) PSB(0): Default visual is TrueColor
[    21.735] (==) PSB(0): Use hardware cursor.
[    21.735] (==) PSB(0): Not using ACPI for LVDS detection.
[    21.735] (II) Loading sub module "dri"
[    21.735] (II) LoadModule: "dri"
[    21.736] (II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
[    21.736] (II) Loading sub module "Xpsb"
[    21.736] (II) LoadModule: "Xpsb"
[    21.737] (II) Loading /usr/lib/xorg/modules/drivers/Xpsb.so
[    21.737] (II) Module Xpsb: vendor="Tungsten Graphics Inc."
[    21.737] 	compiled for 1.6.0, module version = 0.1.0
[    21.737] (II) Loading sub module "vgahw"
[    21.737] (II) LoadModule: "vgahw"
[    21.739] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    21.739] (II) Module vgahw: vendor="X.Org Foundation"
[    21.739] 	compiled for 1.9.0, module version = 0.1.0
[    21.739] 	ABI class: X.Org Video Driver, version 8.0
[    21.740] (--) PSB(0): Mapped PCI MMIO at physical address 0x94000000
	with size 512 kiB
[    21.740] (EE) PSB(0): the stolenBase is:0x7f800000
[    21.740] (--) PSB(0): Detected 7932 kiB of "stolen" memory set aside as video RAM.
[    21.740] (EE) PSB(0): screnIndex is:0;fbPhys is:0x7f800000; fbsize is:0x007bf000
[    21.746] (--) PSB(0): Mapped graphics aperture at physical address 0x7f800000
	with size 7 MiB
[    21.746] (II) PSB(0): Poulsbo MemClock 533, CoreClock 200
[    21.746] (II) PSB(0): Poulsbo Latencies 324 744 210 450
[    21.746] (II) PSB(0): sku_value is 0x00800000, sku_bSDVOEnable is 1, sku_bMaxResEnableInt is 0
[    21.746] (II) PSB(0): Output LVDS0 has no monitor section
[    21.746] (II) PSB(0): I2C bus "LVDSBLC_B" initialized.
[    21.746] (II) PSB(0): I2C bus "LVDSDDC_C" initialized.
[    21.747] (II) PSB(0): I2C device "LVDSBLC_B:BLC Control" registered at address 0x58.
[    21.747] (II) PSB(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
[    21.803] (II) PSB(0): EDID for output LVDS0
[    21.803] (II) PSB(0): Manufacturer: CMO  Model: 903  Serial#: 0
[    21.803] (II) PSB(0): Year: 2008  Week: 45
[    21.803] (II) PSB(0): EDID Version: 1.3
[    21.803] (II) PSB(0): Digital Display Input
[    21.803] (II) PSB(0): Max Image Size [cm]: horiz.: 21  vert.: 12
[    21.803] (II) PSB(0): Gamma: 2.20
[    21.803] (II) PSB(0): No DPMS capabilities specified
[    21.803] (II) PSB(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    21.803] (II) PSB(0): First detailed timing is preferred mode
[    21.803] (II) PSB(0): redX: 0.571 redY: 0.360   greenX: 0.351 greenY: 0.573
[    21.803] (II) PSB(0): blueX: 0.156 blueY: 0.118   whiteX: 0.313 whiteY: 0.329
[    21.803] (II) PSB(0): Manufacturer's mask: 0
[    21.803] (II) PSB(0): Supported detailed timing:
[    21.804] (II) PSB(0): clock: 54.2 MHz   Image Size:  195 x 113 mm
[    21.804] (II) PSB(0): h_active: 1024  h_sync: 1077  h_sync_end 1112 h_blank_end 1200 h_border: 0
[    21.804] (II) PSB(0): v_active: 600  v_sync: 607  v_sync_end 620 v_blanking: 753 v_border: 0
[    21.804] (II) PSB(0):  N089L6-L03
[    21.804] (II) PSB(0):  CMO
[    21.804] (II) PSB(0):  N089L6-L03
[    21.804] (II) PSB(0): EDID (in hex):
[    21.804] (II) PSB(0): 	00ffffffffffff000daf030900000000
[    21.804] (II) PSB(0): 	2d12010380150c780a5f15925c599228
[    21.804] (II) PSB(0): 	1e505400000001010101010101010101
[    21.804] (II) PSB(0): 	0101010101012c1500b0405899203523
[    21.804] (II) PSB(0): 	7d00c37100000018000000fe004e3038
[    21.804] (II) PSB(0): 	394c362d4c30330a2020000000fe0043
[    21.804] (II) PSB(0): 	4d4f0a202020202020202020000000fe
[    21.804] (II) PSB(0): 	004e3038394c362d4c30330a202000fd
[    21.804] (II) PSB(0): EDID vendor "CMO", prod id 2307
[    21.804] (II) PSB(0): Printing DDC gathered Modelines:
[    21.804] (II) PSB(0): Modeline "1024x600"x0.0   54.20  1024 1077 1112 1200  600 607 620 753 -hsync -vsync (45.2 kHz)
[    21.804] (II) PSB(0): EDID vendor "CMO", prod id 2307
[    21.804] (II) Loading sub module "int10"
[    21.805] (II) LoadModule: "int10"
[    21.805] (II) Loading /usr/lib/xorg/modules/libint10.so
[    21.806] (II) Module int10: vendor="X.Org Foundation"
[    21.806] 	compiled for 1.9.0, module version = 1.0.0
[    21.806] 	ABI class: X.Org Video Driver, version 8.0
[    21.806] (II) PSB(0): initializing int10
[    21.813] (II) PSB(0): Bad V_BIOS checksum
[    21.813] (II) PSB(0): Primary V_BIOS segment is: 0xc000
[    21.814] (II) PSB(0): VESA BIOS detected
[    21.814] (II) PSB(0): VESA VBE Version 3.0
[    21.814] (II) PSB(0): VESA VBE Total Mem: 7872 kB
[    21.814] (II) PSB(0): VESA VBE OEM: Intel(r)SCH Chipset Family Graphics Chip Accelerated VGA BIOS
[    21.814] (II) PSB(0): VESA VBE OEM Software Rev: 1.0
[    21.814] (II) PSB(0): VESA VBE OEM Vendor: Intel Corporation
[    21.814] (II) PSB(0): VESA VBE OEM Product: Intel(r)SCH Chipset Family Graphics Controller
[    21.814] (II) PSB(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    21.815] (II) PSB(0): Found panel mode in BIOS VBT tables:
[    21.815] (II) PSB(0): Modeline "1024x600"x0.0   54.20  1024 1077 1112 1200  600 607 620 753 (45.2 kHz)
[    21.816] (II) PSB(0): BLC Data in BIOS VBT tables: datasize=0 paneltype=6                      type=0x02 pol=0x00 freq=0x00c8 minlevel=0x14                         i2caddr=0x58 cmd=0xaa 
[    21.816] (WW) PSB(0): BIOS panel mode data doesn't match probed data, continuing with probed.
[    21.816] (II) PSB(0): BIOS mode:
[    21.816] (II) PSB(0): Modeline "1024x600"x0.0   54.20  1024 1077 1112 1200  600 607 620 753 (45.2 kHz)
[    21.816] (II) PSB(0): probed mode:
[    21.816] (II) PSB(0): Modeline "1024x600"x0.0   54.20  1024 1077 1112 1200  600 607 620 753 -hsync -vsync (45.2 kHz)
[    21.816] xf86TokenToOptinfo: table is NULL
[    21.816] (II) PSB(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
[    21.816] (II) PSB(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
[    21.880] (II) PSB(0): I2C bus "SDVOB DDC Bus" initialized.
[    21.901] (II) PSB(0): Output SDVO-1 has no monitor section
[    21.913] (II) PSB(0): SDVO device VID/DID: 04:AE.00, clock range 25.0MHz - 165.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
[    21.913] (++) PSB(0): i830_psbSaveHWState
[    21.916] (II) PSB(0): Current clock rate multiplier: 1
[    22.075] (==) PSB(0): Shadow framebuffer disabled
[    22.075] (II) Loading sub module "exa"
[    22.076] (II) LoadModule: "exa"
[    22.076] (II) Loading /usr/lib/xorg/modules/libexa.so
[    22.076] (II) Module exa: vendor="X.Org Foundation"
[    22.076] 	compiled for 1.9.0, module version = 2.5.0
[    22.076] 	ABI class: X.Org Video Driver, version 8.0
[    22.076] (==) PSB(0): Acceleration enabled
[    22.076] (==) PSB(0): [EXA] Allocate 32768 kiB for EXA pixmap cache.
[    22.076] (==) PSB(0): [EXA] Allocate 4 kiB for scratch memory.
[    22.076] (II) PSB(0): Output "SDVO-1" is assigned to this screen.
[    22.076] (II) PSB(0): Output "LVDS0" is assigned to this screen.
[    22.077] (II) PSB(0): Searching for matching Poulsbo mode(s):
[    22.133] (II) PSB(0): EDID for output LVDS0
[    22.133] (II) PSB(0): Manufacturer: CMO  Model: 903  Serial#: 0
[    22.133] (II) PSB(0): Year: 2008  Week: 45
[    22.133] (II) PSB(0): EDID Version: 1.3
[    22.133] (II) PSB(0): Digital Display Input
[    22.133] (II) PSB(0): Max Image Size [cm]: horiz.: 21  vert.: 12
[    22.133] (II) PSB(0): Gamma: 2.20
[    22.133] (II) PSB(0): No DPMS capabilities specified
[    22.133] (II) PSB(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    22.133] (II) PSB(0): First detailed timing is preferred mode
[    22.133] (II) PSB(0): redX: 0.571 redY: 0.360   greenX: 0.351 greenY: 0.573
[    22.133] (II) PSB(0): blueX: 0.156 blueY: 0.118   whiteX: 0.313 whiteY: 0.329
[    22.133] (II) PSB(0): Manufacturer's mask: 0
[    22.134] (II) PSB(0): Supported detailed timing:
[    22.134] (II) PSB(0): clock: 54.2 MHz   Image Size:  195 x 113 mm
[    22.134] (II) PSB(0): h_active: 1024  h_sync: 1077  h_sync_end 1112 h_blank_end 1200 h_border: 0
[    22.134] (II) PSB(0): v_active: 600  v_sync: 607  v_sync_end 620 v_blanking: 753 v_border: 0
[    22.134] (II) PSB(0):  N089L6-L03
[    22.134] (II) PSB(0):  CMO
[    22.134] (II) PSB(0):  N089L6-L03
[    22.134] (II) PSB(0): EDID (in hex):
[    22.134] (II) PSB(0): 	00ffffffffffff000daf030900000000
[    22.134] (II) PSB(0): 	2d12010380150c780a5f15925c599228
[    22.134] (II) PSB(0): 	1e505400000001010101010101010101
[    22.134] (II) PSB(0): 	0101010101012c1500b0405899203523
[    22.134] (II) PSB(0): 	7d00c37100000018000000fe004e3038
[    22.134] (II) PSB(0): 	394c362d4c30330a2020000000fe0043
[    22.134] (II) PSB(0): 	4d4f0a202020202020202020000000fe
[    22.134] (II) PSB(0): 	004e3038394c362d4c30330a202000fd
[    22.134] (II) PSB(0): EDID vendor "CMO", prod id 2307
[    22.134] (II) PSB(0): Printing DDC gathered Modelines:
[    22.134] (II) PSB(0): Modeline "1024x600"x0.0   54.20  1024 1077 1112 1200  600 607 620 753 -hsync -vsync (45.2 kHz)
[    22.134] (II) PSB(0): EDID vendor "CMO", prod id 2307
[    22.134] (II) PSB(0): Printing probed modes for output LVDS0
[    22.134] (II) PSB(0): Modeline "1024x600"x60.0   54.20  1024 1077 1112 1200  600 607 620 753 -hsync -vsync (45.2 kHz)
[    22.185] (EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
[    22.223] (II) PSB(0): EDID for output SDVO-1
[    22.223] (II) PSB(0): Output LVDS0 connected
[    22.223] (II) PSB(0): Output SDVO-1 disconnected
[    22.224] (II) PSB(0): Using exact sizes for initial modes
[    22.224] (II) PSB(0): Output LVDS0 using initial mode 1024x600
[    22.224] (II) PSB(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    22.224] (**) PSB(0): Display dimensions: (210, 120) mm
[    22.224] (**) PSB(0): DPI set to (123, 216)
[    22.224] (--) Depth 24 pixmap format is 32 bpp
[    22.224] drmOpenDevice: node name is /dev/dri/card0
[    22.224] drmOpenDevice: open result is -1, (No such device)
[    22.224] drmOpenDevice: open result is -1, (No such device)
[    22.224] drmOpenDevice: Open failed
[    22.224] drmOpenDevice: node name is /dev/dri/card0
[    22.224] drmOpenDevice: open result is -1, (No such device)
[    22.225] drmOpenDevice: open result is -1, (No such device)
[    22.225] drmOpenDevice: Open failed
[    33.670] [drm] failed to load kernel module "psb"
[    33.671] (EE) [drm] drmOpen failed.
[    33.671] (EE) PSB(0): [dri] DRIScreenInit failed. Disabling DRI.
[    33.671] (EE) [drm] Could not uninstall irq handler.
[    33.671] (EE) PSB(0): This driver currently needs DRM to operate.
[    33.671] 
Fatal server error:
[    33.671] AddScreen/ScreenInit failed for driver 0
[    33.671] 
[    33.671] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    33.671] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    33.671] 
[    34.087] (WW) xf86CloseConsole: VT_WAITACTIVE failed: Interrupted system call
[    34.087]  ddxSigGiveUp: Closing log

```

/ver/log/Xorg.failsafe.log
```

[    19.268] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    19.288] X Protocol Version 11, Revision 0
[    19.295] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    19.302] Current Operating System: Linux Clare 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686
[    19.311] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=af393f32-41c2-4ccf-9bbf-b296d8a2ce5b ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb
[    19.338] Build Date: 09 January 2011  12:14:58PM
[    19.347] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    19.357] Current version of pixman: 0.18.4
[    19.367] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.387] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.416] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Tue May 24 10:26:04 2011
[    19.426] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[    19.436] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.446] (==) No Layout section.  Using the first Screen section.
[    19.446] (**) |-->Screen "Default Screen" (0)
[    19.446] (**) |   |-->Monitor "Configured Monitor"
[    19.447] (**) |   |-->Device "Configured Video Device"
[    19.447] (==) Automatically adding devices
[    19.447] (==) Automatically enabling devices
[    19.447] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.447] 	Entry deleted from font path.
[    19.447] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    19.447] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.448] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.448] (II) Loader magic: 0x81f9b00
[    19.448] (II) Module ABI versions:
[    19.448] 	X.Org ANSI C Emulation: 0.4
[    19.448] 	X.Org Video Driver: 8.0
[    19.448] 	X.Org XInput driver : 11.0
[    19.448] 	X.Org Server Extension : 4.0
[    19.449] (--) PCI:*(0:0:2:0) 8086:8108:103c:145a rev 7, Mem @ 0x94000000/524288, 0x80000000/268435456, 0x94080000/262144, I/O @ 0x00004070/8
[    19.449] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    19.449] (II) LoadModule: "extmod"
[    19.453] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.453] (II) Module extmod: vendor="X.Org Foundation"
[    19.453] 	compiled for 1.9.0, module version = 1.0.0
[    19.453] 	Module class: X.Org Server Extension
[    19.453] 	ABI class: X.Org Server Extension, version 4.0
[    19.453] (II) Loading extension MIT-SCREEN-SAVER
[    19.453] (II) Loading extension XFree86-VidModeExtension
[    19.453] (II) Loading extension XFree86-DGA
[    19.453] (II) Loading extension DPMS
[    19.453] (II) Loading extension XVideo
[    19.453] (II) Loading extension XVideo-MotionCompensation
[    19.453] (II) Loading extension X-Resource
[    19.453] (II) LoadModule: "dbe"
[    19.454] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.454] (II) Module dbe: vendor="X.Org Foundation"
[    19.454] 	compiled for 1.9.0, module version = 1.0.0
[    19.454] 	Module class: X.Org Server Extension
[    19.454] 	ABI class: X.Org Server Extension, version 4.0
[    19.454] (II) Loading extension DOUBLE-BUFFER
[    19.455] (II) LoadModule: "glx"
[    19.455] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.456] (II) Module glx: vendor="X.Org Foundation"
[    19.456] 	compiled for 1.9.0, module version = 1.0.0
[    19.456] 	ABI class: X.Org Server Extension, version 4.0
[    19.456] (==) AIGLX enabled
[    19.456] (II) Loading extension GLX
[    19.456] (II) LoadModule: "record"
[    19.457] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.457] (II) Module record: vendor="X.Org Foundation"
[    19.457] 	compiled for 1.9.0, module version = 1.13.0
[    19.457] 	Module class: X.Org Server Extension
[    19.457] 	ABI class: X.Org Server Extension, version 4.0
[    19.457] (II) Loading extension RECORD
[    19.457] (II) LoadModule: "dri"
[    19.458] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.461] (II) Module dri: vendor="X.Org Foundation"
[    19.461] 	compiled for 1.9.0, module version = 1.0.0
[    19.461] 	ABI class: X.Org Server Extension, version 4.0
[    19.461] (II) Loading extension XFree86-DRI
[    19.461] (II) LoadModule: "dri2"
[    19.462] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.462] (II) Module dri2: vendor="X.Org Foundation"
[    19.462] 	compiled for 1.9.0, module version = 1.2.0
[    19.462] 	ABI class: X.Org Server Extension, version 4.0
[    19.462] (II) Loading extension DRI2
[    19.462] (II) LoadModule: "vesa"
[    19.463] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.463] (II) Module vesa: vendor="X.Org Foundation"
[    19.463] 	compiled for 1.8.99.905, module version = 2.3.0
[    19.463] 	Module class: X.Org Video Driver
[    19.463] 	ABI class: X.Org Video Driver, version 8.0
[    19.463] (II) VESA: driver for VESA chipsets: vesa
[    19.463] (--) using VT number 2

```

The problem seems to be here
```

[    21.236] [drm] failed to load kernel module "psb"
[    21.236] (EE) [drm] drmOpen failed.
[    21.236] (EE) PSB(0): [dri] DRIScreenInit failed. Disabling DRI.
[    21.236] (EE) [drm] Could not uninstall irq handler.
[    21.236] (EE) PSB(0): This driver currently needs DRM to operate.
[    21.236] 
Fatal server error:
[    21.236] AddScreen/ScreenInit failed for driver 0

```

with the kernel module not loading. So in the root shell I tried
```

modprobe psb
lsmod | grep psb

```

and it appears to have loaded. After calling modprobe there is a message in the terminal "detear is disabled". The result of lsmod is
```

psb              147676  0 
drm_psb          178811  1 psb
agpgart           32011  1 drm_psb
i2c_algo_bit       5168  1 psb
video             18712  1 psb

```

---

### Post by Ayuthia on 2011-05-24
This one is an old [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/406651") so it might not be valid anymore, but it looks like psb-kernel-source was not installed.

---

### Post by cheshirekow on 2011-05-24
> **Ayuthia said:**
> This one is an old [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/406651") so it might not be valid anymore, but it looks like psb-kernel-source was not installed.

Good find, but... I recall the psb-kernel-source being installed when I first installed PSB, but I went ahead and reinstalled it anyway. It appears that it didn't help though. Since I first installed PSB after updating everything anyway, I don't think this could have been the issue.

Also, I am unable to boot into low graphics mode.

Edit:
Ugh, I seem to have lost the ability to get the grub boot menu for some reason :(.
ermm... nevermind, it's back

---

### Post by cheshirekow on 2011-05-24
Woah!!! 

Ok, this is weird. So you know how before gdm starts you usually get a couple of seconds at one of the tty login prompts? Well, I tried doing this *really* quickly:

[list=1]
[*]enter login name 
[*]enter password
[*]sudo modprobe psb
[*]enter password
[/list]

I guess I managed to beat the startup time of X because it worked! On the next reboot, blank screen. On the next reboot, I tried doing the above again, and it worked again. So I guess, for some reason, I have to manually load the psb kernel module. Is there anyway to put that in a configure script somewhere so that the psb module is automatically loaded before gdm starts?

Edit:
This seems to be the responsibility of /etc/modprobe.d which contains poulsbo.conf, which contains the line to load the psb module... so I'm not sure why it isn't loading automatically. pouslbo.conf contains two options disable_vsync=1 and no_fb=1. I'm wondering if I should change one of those? Are the contents of /etc/modprobe.d/ automatically parsed during boot? Or are they joined into some boot configuration file by something like update-initramfs?

Edit 2:
Nope, Favux is right. /etc/modprobe.d just defines options for *when* that module is loaded.

---

### Post by Favux on 2011-05-24
Yes, add it to the /etc/modules file's list so it auto-loads.

---

### Post by cheshirekow on 2011-05-24
> **Favux said:**
> Yes, add it to the /etc/modules file's list so it auto-loads.

It's AALLIIIIIIVEEE. 

Great, that worked. Thanks a ton! 

Now, I need to figure out how to upgrade the xorg server. Supposedly the PSB driver is compatible with 1.10.

Edit: I tried to install xorg-server from the natty repositories but dpkg says it will break xserver-xorg-video-8.

---

### Post by Favux on 2011-05-24
Good!

With *sudo depmod -a* all module dependencies should be rebuilt and the module should auto-load.  But with some modules on some systems, for whatever reason, it doesn't work.  Adding it to /etc/modules "forces" the auto-load.

Boy that stupid video doesn't want to cooperate does it?

---

### Post by cheshirekow on 2011-05-24
> **Favux said:**
> Boy that stupid video doesn't want to cooperate does it?

No, it doesn't. This has turned into quite a project... which is unfortunate, because now it's that much harder to quit ;).

---

### Post by cheshirekow on 2011-05-24
Hm... Maybe instead of trying to get xorg server 1.10 into maverick, maybe I should try to get the maverick kernel into Natty. I guess I could just dist-upgrade from what I've got. I'll give that a try next.

Edit:
Note, I had to comment out "#GRUB_HIDDEN_TIMEOUT=0" in /etc/default/grub in order to get the grub menu to show

Edit:
OMFG are you kidding me? I managed to get the maverick kernel installed and running in Natty... but even before I installed the PSB driver, multitouch only works with the Natty kernel.
And the wireless driver isn't working either.

---

### Post by cheshirekow on 2011-05-24
Ok, I think I'm giving up on this. In case anyone else has the bright idea of trying to install ubuntu on an HP slate, there are other issues that I haven't brought up yet.

sound doesn't work in Natty (looping), but does in lucid and maverick.

only the outword facing webcam works (inward one does not)

Edit:
Anyone interested in buying a barely used HP Slate 500?

---

### Post by Ayuthia on 2011-05-24
> **cheshirekow said:**
> Hm... Maybe instead of trying to get xorg server 1.10 into maverick, maybe I should try to get the maverick kernel into Natty. I guess I could just dist-upgrade from what I've got. I'll give that a try next.

Edit:
Note, I had to comment out "#GRUB_HIDDEN_TIMEOUT=0" in /etc/default/grub in order to get the grub menu to show

Edit:
OMFG are you kidding me? I managed to get the maverick kernel installed and running in Natty... but even before I installed the PSB driver, multitouch only works with the Natty kernel.
And the wireless driver isn't working either.

Have you tried grabbing the PSB driver source and building it?  I would think that the PSB driver and the wireless driver will have to be recompiled because they are kernel modules.  As for the multitouch, is that the one that comes with Natty or is it downgraded?

I have not had a chance to build the multitouch on the older xorg-server as of yet.  I was going to give it a shot to see if I can get the multitouch to respond on mine.

---

### Post by cheshirekow on 2011-05-24
> **Ayuthia said:**
> Have you tried grabbing the PSB driver source and building it?  I would think that the PSB driver and the wireless driver will have to be recompiled because they are kernel modules.  


I didn't install the PSB driver yet because the wireless wasn't working (so couldn't get the packages). The wireless module comes as a source package which is built when you install it. It built the module for both kernels (the natty one and the maverick one). Wireless networks are visible, but disconnect as soon as I connect to one. Note that this is only when running the maverick kernel. With the natty kernel, the wireless was working fine.

> 
As for the multitouch, is that the one that comes with Natty or is it downgraded?

I have not had a chance to build the multitouch on the older xorg-server as of yet.  I was going to give it a shot to see if I can get the multitouch to respond on mine.

Everything was from Natty except I was using the maverick kernel. It may be possible to rebuild things and make it work, but having spent literally all my free time (and too much of my work-time, shhhh... don't tell) for the past week and half, I'm pretty much burned out on trying to make it work. I'll wait for a device which doesn't require so many hoops. Honestly, I don't really care that much about the multi-touch cool factor... its the fact that, lacking external buttons, the multitouch is necessary IMHO to have a decent experience.

Edit: what device do you have?

---

### Post by aquarat on 2011-05-24
wow, this is great progress! I'm going to go venture out into the rain and retrieve my slate from the car to try this :D .

---

### Post by cheshirekow on 2011-05-24
> **aquarat said:**
> wow, this is great progress! I'm going to go venture out into the rain and retrieve my slate from the car to try this :D .

Good luck. If you want multitouch to work the important thing to figure out is what exactly is required. I've only gotten it to work with kernel 2.6.38, xorg-server 1.10, xserver-xorg-input-evdev 2.6.0 (i.e. default Natty install). Changing any of those three seems to break multitouch. Hardware accelerated graphics + multitouch will only be possible if

1) multitouch works with kernel 2.6.35, xorg-server 1.10, evdev ?? (in which case you should either try to get the maverick kernel to work in a natty install, and use the PSB driver, or try to get xorg-server 1.10 to install in maverick, and use the psb driver )

2) multitouch works with kernel 2.6.38, xorg-server 1.9, evdev 2.3 (in which case you should install the emgd driver in natty)

---

### Post by aquarat on 2011-05-24
IT WORKS :D I'm so happy :) Thanks Cheshirekow!

I'm not that phased by multi-touch not working or the cameras not working... the next thing for me is VAAPI/CrystalHD. and YAY! the brightness applet works now! *tear*

---

### Post by Ayuthia on 2011-05-24
> **cheshirekow said:**
> I didn't install the PSB driver yet because the wireless wasn't working (so couldn't get the packages). The wireless module comes as a source package which is built when you install it. It built the module for both kernels (the natty one and the maverick one). Wireless networks are visible, but disconnect as soon as I connect to one. Note that this is only when running the maverick kernel. With the natty kernel, the wireless was working fine.



Everything was from Natty except I was using the maverick kernel. It may be possible to rebuild things and make it work, but having spent literally all my free time (and too much of my work-time, shhhh... don't tell) for the past week and half, I'm pretty much burned out on trying to make it work. I'll wait for a device which doesn't require so many hoops. Honestly, I don't really care that much about the multi-touch cool factor... its the fact that, lacking external buttons, the multitouch is necessary IMHO to have a decent experience.

Edit: what device do you have?

I actually have the HP tx2 tablet.  It has the N-trig touchscreen and has the Broadcom wireless card, but it runs with and ATI graphics card.  Unfortunately, the graphics card is not a heavy-duty one so the tablet runs pretty hot when you try to view a video or play a game.

I will not be able to test out the graphics portion, but I would be able to test out the downgraded xorg-server by using the EMGD method to see if I can get it to run.  As far as I know, multitouch has worked with the N-trig drivers in 1.9.

As for the multitouch, I agree about the cool factor.  It is nice to be able to use multitouch gestures to get things to run when you lack buttons.

Can one of you post your hardware info (lspci/lsusb or any other relevant option)?  I have been curious about what is in there.

---

### Post by lnxlvr on 2011-05-24
I have a HP slate 500 and yesterday I installed Natty using Wubi installer. And it booted up just fine. Single touch works (No multi touch) and no on-screen keyboard.

I can connect usb keyboard/mouse and it works perfectly fine.

---

### Post by aquarat on 2011-05-24
Just say if this is too verbose.

lspci :
```

00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
01:00.0 Multimedia controller: Broadcom Corporation Device 1615
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

```

lspci -vvv :

```


00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
	Subsystem: Hewlett-Packard Company Device 145a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 145a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 94000000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at 4070 [size=8]
	Region 2: Memory at 80000000 (32-bit, non-prefetchable) [size=256M]
	Region 3: Memory at 94080000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [b0] Vendor Specific Information: Len=07 <?>
	Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Kernel driver in use: psb

00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 145a
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 940c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s Enabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4161
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=1 ArbSelect=Fixed TC/VC=00
			Status:	NegoPending- InProgress-
	Capabilities: [130 v1] Root Complex Link
		Desc:	PortNumber=0f ComponentID=00 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=00 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed10000
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 90000000-90ffffff
	Prefetchable memory behind bridge: 91000000-91ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM+ Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #1, PowerLimit 10.000W; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn+ PwrFlt- MRL- PresDet+ CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 145a
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 93000000-93ffffff
	Prefetchable memory behind bridge: 92000000-92ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #2, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM+ Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #2, PowerLimit 10.000W; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn+ PwrFlt- MRL- PresDet+ CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 145a
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 145a
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at 4040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 145a
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 4: I/O ports at 4020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 145a
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 4000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 145a
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 19
	Region 0: Memory at 940c4000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
	Subsystem: Hewlett-Packard Company Device 145a
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel modules: lpc_sch

00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07) (prog-if 80 [Master])
	Subsystem: Hewlett-Packard Company Device 145a
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	Region 4: I/O ports at 4060 [size=16]
	Kernel driver in use: pata_sch
	Kernel modules: pata_sch

01:00.0 Multimedia controller: Broadcom Corporation Device 1615
	Subsystem: Broadcom Corporation Device 1615
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 40
	Region 0: Memory at 90800000 (64-bit, non-prefetchable) [size=64K]
	Region 2: Memory at 90000000 (64-bit, non-prefetchable) [size=8M]
	Capabilities: [48] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [60] Vendor Specific Information: Len=6c <?>
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0300c  Data: 4159
	Capabilities: [cc] Express (v2) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <64us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout+ NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [13c v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Kernel driver in use: crystalhd
	Kernel modules: crystalhd

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
	Subsystem: Hewlett-Packard Company Device 1483
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at 93000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=2 PME-
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [d0] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
			ClockPM+ Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [13c v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 00-00-af-ff-ff-10-cc-52
	Capabilities: [16c v1] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl

```

lsusb :
```

Bus 004 Device 002: ID 0a5c:21b4 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 10f1:1a26  
Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and lsusb -vvv
```


Bus 004 Device 002: ID 0a5c:21b4 Broadcom Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x21b4 
  bcdDevice            4.81
  iManufacturer           1 Broadcom Corp
  iProduct                2 Broadcom 2070 Bluetooth
  iSerial                 3 CC52AF1A4A99
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          216
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      1 
      iInterface              0 
      Device Firmware Upgrade Interface Descriptor:
        bLength                             7
        bDescriptorType                    33
        bmAttributes                        7
          Will Not Detach
          Manifestation Tolerant
          Upload Supported
          Download Supported
        wDetachTimeout                   5000 milliseconds
        wTransferSize                      64 bytes
Device Status:     0x0001
  Self Powered

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 002: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1b96 N-Trig
  idProduct          0x0001 Duosense Transparent Electromagnetic Digitizer
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           75
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength       8
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               2
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     962
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               2
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Connection timed out (110)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc312 DeLuxe 250 Keyboard
  bcdDevice            1.01
  iManufacturer           1 LITEON Technology
  iProduct                2 USB Multimedia Keyboard
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               70mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      65
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              24
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 006: ID 10f1:1a26  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x10f1 
  idProduct          0x1a26 
  bcdDevice            2.37
  iManufacturer           1 Importek
  iProduct                2 HP Webcam
  iSerial                 3 Dual Sensor
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength         1001
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              0 
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           77
        dwClockFrequency       30.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x0000000e
          Auto-Exposure Mode
          Auto-Exposure Priority
          Exposure Time (Absolute)
      VideoControl Interface Descriptor:
        bLength                26
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 2
        guidExtensionCode         {92423946-d10c-e34a-8783-3133f9eaaa3b}
        bNumControl             3
        bNrPins                 1
        baSourceID( 0)          1
        bControlSize            1
        bmControls( 0)       0xff
        iExtension              0 
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 3
        bSourceID               2
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000177f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          White Balance Temperature
          Backlight Compensation
          Gain
          Power Line Frequency
          White Balance Temperature, Auto
        iProcessing             0 
        bmVideoStandards     0x 9
          None
          SECAM - 625/50
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             4
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               3
        iTerminal               0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      VideoStreaming Interface Descriptor:
        bLength                            15
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                         2
        wTotalLength                      813
        bEndPointAddress                  129
        bmInfo                              0
        bTerminalLink                       4
        bStillCaptureMethod                 2
        bTriggerSupport                     1
        bTriggerUsage                       1
        bControlSize                        1
        bmaControls( 0)                    27
        bmaControls( 1)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                8
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         400000
        bFrameIntervalType                  4
        dwFrameInterval( 0)            400000
        dwFrameInterval( 1)            400001
        dwFrameInterval( 2)            400002
        dwFrameInterval( 3)            400003
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1024
        wHeight                           768
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     1572864
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  4
        dwFrameInterval( 0)            666666
        dwFrameInterval( 1)            666667
        dwFrameInterval( 2)            666668
        dwFrameInterval( 3)            666669
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     2621440
        dwDefaultFrameInterval        4000000
        bFrameIntervalType                  4
        dwFrameInterval( 0)           4000000
        dwFrameInterval( 1)           4000001
        dwFrameInterval( 2)           4000002
        dwFrameInterval( 3)           4000003
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         400000
        bFrameIntervalType                  4
        dwFrameInterval( 0)            400000
        dwFrameInterval( 1)            400001
        dwFrameInterval( 2)            400002
        dwFrameInterval( 3)            400003
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         400000
        bFrameIntervalType                  4
        dwFrameInterval( 0)            400000
        dwFrameInterval( 1)            400001
        dwFrameInterval( 2)            400002
        dwFrameInterval( 3)            400003
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval        4000000
        bFrameIntervalType                  4
        dwFrameInterval( 0)           4000000
        dwFrameInterval( 1)           4000001
        dwFrameInterval( 2)           4000002
        dwFrameInterval( 3)           4000003
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1600
        wHeight                          1200
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     3840000
        dwDefaultFrameInterval        4000000
        bFrameIntervalType                  4
        dwFrameInterval( 0)           4000000
        dwFrameInterval( 1)           4000001
        dwFrameInterval( 2)           4000002
        dwFrameInterval( 3)           4000003
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         8
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           2048
        wHeight                          1536
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     6291456
        dwDefaultFrameInterval        4000000
        bFrameIntervalType                  4
        dwFrameInterval( 0)           4000000
        dwFrameInterval( 1)           4000001
        dwFrameInterval( 2)           4000002
        dwFrameInterval( 3)           4000003
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               8
        wWidth( 0)                        640
        wHeight( 0)                       480
        wWidth( 1)                       1024
        wHeight( 1)                       768
        wWidth( 2)                       1280
        wHeight( 2)                      1024
        wWidth( 3)                        320
        wHeight( 3)                       240
        wWidth( 4)                        160
        wHeight( 4)                       120
        wWidth( 5)                       1280
        wHeight( 5)                       720
        wWidth( 6)                       1600
        wHeight( 6)                      1200
        wWidth( 7)                       2048
        wHeight( 7)                      1536
        bNumCompressionPatterns             8
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     0 (Unspecified)
        bTransferCharacteristics            0 (Unspecified)
        bMatrixCoefficients                 0 (Unspecified)
      VideoStreaming Interface Descriptor:
        bLength                            11
        bDescriptorType                    36
        bDescriptorSubtype                  6 (FORMAT_MJPEG)
        bFormatIndex                        2
        bNumFrameDescriptors                8
        bFlags                              1
          Fixed-size samples: Yes
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         400000
        bFrameIntervalType                  4
        dwFrameInterval( 0)            400000
        dwFrameInterval( 1)            400001
        dwFrameInterval( 2)            400002
        dwFrameInterval( 3)            400003
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1024
        wHeight                           768
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     1572864
        dwDefaultFrameInterval         400000
        bFrameIntervalType                  4
        dwFrameInterval( 0)            400000
        dwFrameInterval( 1)            400001
        dwFrameInterval( 2)            400002
        dwFrameInterval( 3)            400003
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     2621440
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  4
        dwFrameInterval( 0)            666666
        dwFrameInterval( 1)            666667
        dwFrameInterval( 2)            666668
        dwFrameInterval( 3)            666669
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         400000
        bFrameIntervalType                  4
        dwFrameInterval( 0)            400000
        dwFrameInterval( 1)            400001
        dwFrameInterval( 2)            400002
        dwFrameInterval( 3)            400003
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         400000
        bFrameIntervalType                  4
        dwFrameInterval( 0)            400000
        dwFrameInterval( 1)            400001
        dwFrameInterval( 2)            400002
        dwFrameInterval( 3)            400003
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  4
        dwFrameInterval( 0)            666666
        dwFrameInterval( 1)            666667
        dwFrameInterval( 2)            666668
        dwFrameInterval( 3)            666669
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1600
        wHeight                          1200
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     3840000
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  4
        dwFrameInterval( 0)            666666
        dwFrameInterval( 1)            666667
        dwFrameInterval( 2)            666668
        dwFrameInterval( 3)            666669
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  7 (FRAME_MJPEG)
        bFrameIndex                         8
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           2048
        wHeight                          1536
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     6291456
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  4
        dwFrameInterval( 0)            666666
        dwFrameInterval( 1)            666667
        dwFrameInterval( 2)            666668
        dwFrameInterval( 3)            666669
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               8
        wWidth( 0)                        640
        wHeight( 0)                       480
        wWidth( 1)                       1024
        wHeight( 1)                       768
        wWidth( 2)                       1280
        wHeight( 2)                      1024
        wWidth( 3)                        320
        wHeight( 3)                       240
        wWidth( 4)                        160
        wHeight( 4)                       120
        wWidth( 5)                       1280
        wHeight( 5)                       720
        wWidth( 6)                       1600
        wHeight( 6)                      1200
        wWidth( 7)                       2048
        wHeight( 7)                      1536
        bNumCompressionPatterns             8
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     0 (Unspecified)
        bTransferCharacteristics            0 (Unspecified)
        bMatrixCoefficients                 0 (Unspecified)
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1340  3x 832 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1300  3x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x12c0  3x 704 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x6366 Multi Flash Reader
  bcdDevice            1.00
  iManufacturer           1 Generic
  iProduct                2 Mass Storage Device
  iSerial                 3 058F63666433
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.7
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0503 highspeed power enable connect
   Port 8: 0000.0503 highspeed power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```

and also vainfo after "sudo ln -s /usr/lib/va/drivers/psb_drv_video.so /usr/local/lib/dri/" : 

```

libva: libva version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/local/lib/dri/psb_drv_video.so
libva error: /usr/local/lib/dri/psb_drv_video.so has no function __vaDriverInit_0_32
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

I'm now going to upgrade to Natty... see what happens.

---

### Post by cheshirekow on 2011-05-24
> **lnxlvr said:**
> I have a HP slate 500 and yesterday I installed Natty using Wubi installer. And it booted up just fine. Single touch works (No multi touch) and no on-screen keyboard.

I can connect usb keyboard/mouse and it works perfectly fine.

Hey lnxlvr. I'm assuming you're using the "Ubuntu Classic" interface. Open a terminal and run ginn. Then put three fingers on the screen and spread them out. You should see the terminal window maximize. The opposite gesture minimizes. You should also see the terminal printing a ton of text. Try a couple of times if nothing happens but you are seeing output to the terminal. The multi-touch is most-likely working, but there is no software using it. 

The unity interface has multi-touch recognition built-in... but it also requires 3d hardware to run compiz. The "classic" interface doesn't have multi-touch built-in, but ginn can do it for you.

As for the on-screen keyboard... the one I used was called "onboard". I think it comes installed, but if not it's in the repositories. Just run the command "onboard" and it will launch. I've added it to my settings in the "Startup Applications" tool. You can also get to it from the login screen by clicking on the accessibility icon (I believe in the bottom left).

Hope that helps.

---

### Post by cheshirekow on 2011-05-24
> **aquarat said:**
> IT WORKS :D I'm so happy :) Thanks Cheshirekow!

I'm not that phased by multi-touch not working or the cameras not working... the next thing for me is VAAPI/CrystalHD. and YAY! the brightness applet works now! *tear*

Glad to have helped :). You can also rotate with the PSB driver. Run 'xrandr -o left' to rotate the screen 90deg ccw, and 'xrandr -o normal' to restore it. I believe the slate has an accelerometer in it. It might be worth looking into binding that to the xrandr command if it's usable in ubuntu.

---

### Post by cheshirekow on 2011-05-24
> **Ayuthia said:**
> I actually have the HP tx2 tablet.  It has the N-trig touchscreen and has the Broadcom wireless card, but it runs with and ATI graphics card.  Unfortunately, the graphics card is not a heavy-duty one so the tablet runs pretty hot when you try to view a video or play a game.

I will not be able to test out the graphics portion, but I would be able to test out the downgraded xorg-server by using the EMGD method to see if I can get it to run.  As far as I know, multitouch has worked with the N-trig drivers in 1.9.


Ok, please let me know if you figure anything out. If we can get the N-trig multitouch to work with 1.9 and it's not a Kernel issue, then sticking with ubuntu 10.10 and the PSB driver will pretty much provide me with everything I want from this device. If it is a kernel issue, well then at least the EMGD driver + multi-touch will make it worth keeping.

Edit:
Just found [this message]("https://lists.launchpad.net/multi-touch-dev/msg00218.html") on the mailing lists, which says that maverick *should* support ntrig multi-touch out of the box. Maybe I will keep trying after all :/.

---

### Post by aquarat on 2011-05-24
> 
Run 'xrandr -o left' to rotate the screen 90deg ccw, and 'xrandr -o normal' to restore it.

haha, I was just trying that as you made your post. Very useful for note-taking, thank you once again :) .

Other users had logged a bug on the [Google Code page](http://code.google.com/p/gma500/issues/detail?id=42) for PSB, so I added in your discovery, hopefully it will help them too.

CrystalHD is being loaded...
```

[    4.425696] Loading crystalhd 3.2.0
[    4.425781] crystalhd 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.506756] crystalhd 0000:01:00.0: irq 40 for MSI/MSI-X
[    4.506811] opening HW
[    4.506818] crystalhd_hw_open: setting up functions, device = Flea
[    4.597117] Closing HW
[    4.633196] crystalhd 0000:01:00.0: setting latency timer to 64

```

---

### Post by Ayuthia on 2011-05-24
> **cheshirekow said:**
> Ok, please let me know if you figure anything out. If we can get the N-trig multitouch to work with 1.9 and it's not a Kernel issue, then sticking with ubuntu 10.10 and the PSB driver will pretty much provide me with everything I want from this device. If it is a kernel issue, well then at least the EMGD driver + multi-touch will make it worth keeping.

Edit:
Just found [this message]("https://lists.launchpad.net/multi-touch-dev/msg00218.html") on the mailing lists, which says that maverick *should* support ntrig multi-touch out of the box. Maybe I will keep trying after all :/.

I was just trying to install the emgd ppa and just found xorg-emgd does not exist in 64-bit so I am going to install the 32-bit version and try again.

I thought that the multi-touch was supposed to work in Maverick and even possibly in Lucid (but not out of the box).  I have been using it for quite some time now and that is why I am surprised that it is not working for you.  The positive side is that we have confirmed that the Slate is able to report the multi-touch events over to evdev so we just need to figure out why it does not make it over to ginn/gesturtest.

---

### Post by cheshirekow on 2011-05-24
> **Ayuthia said:**
> I thought that the multi-touch was supposed to work in Maverick and even possibly in Lucid (but not out of the box).  I have been using it for quite some time now and that is why I am surprised that it is not working for you.  The positive side is that we have confirmed that the Slate is able to report the multi-touch events over to evdev so we just need to figure out why it does not make it over to ginn/gesturtest.

Yeah, I just found [this mailing list message]("https://lists.launchpad.net/multi-touch-dev/msg00218.html") saying exactly that (that it should work in maverick). I posted a bug on utouch [here]("https://bugs.launchpad.net/utouch/+bug/787854"). 

I'll reinstall maverick and rerun those tests because they were last run in Natty. I would assume the problem is the same and I expect the results to be the same, but never the less I should check.

P.S. I guess this means I'm un-giving-up.

---

### Post by cheshirekow on 2011-05-24
aquarat, out of curiosity, how did you get maverick to install. Did you follow my steps about building the custom image? Or did you manage to get it another way?

---

### Post by cheshirekow on 2011-05-24
Minor status report: I saw some stuff on the utouch mailing list about an xserver-xorg-input-evtouch driver. I figured I would give that a shot. I'm currently running maverick with the PSB driver. When I installed the evtouch driver the xserver crashes on load (segmentation fault is logged in the Xorg log file), so I removed that. I probably should have not installed the PSB driver until after I got multi-touch working...

Also, when I run evtest, the display freezes after I touch the screen. As far as I can tell, everything freezes (I can't drop to a shell).

Edit:
fresh install of maverick, no PSB driver, evtest still freezes the system

Edit 2: 
This is cute. It's not evtest, it's the multi-touch. Just touching the screen after logging in will freeze the system.

Edit 3:
I upgraded the kernel to 2.6.35-28, and same problem. Touching the screen freezes the system.

Does anyone know how the ordering of the Xorg logs are? Is Xorg.0.log for the current session, .1.log for the last session, .2.log for the one before that?
Nevermind, the xorg manual page says its the display number. Why do I have 5 displays? It probably doesn't matter...

---

### Post by Ayuthia on 2011-05-24
> **cheshirekow said:**
> Minor status report: I saw some stuff on the utouch mailing list about an xserver-xorg-input-evtouch driver. I figured I would give that a shot. I'm currently running maverick with the PSB driver. When I installed the evtouch driver the xserver crashes on load (segmentation fault is logged in the Xorg log file), so I removed that. I probably should have not installed the PSB driver until after I got multi-touch working...

Also, when I run evtest, the display freezes after I touch the screen. As far as I can tell, everything freezes (I can't drop to a shell).

Edit:
fresh install of maverick, no PSB driver, evtest still freezes the system

Edit 2: 
This is cute. It's not evtest, it's the multi-touch. Just touching the screen after logging in will freeze the system.

Edit 3:
I upgraded the kernel to 2.6.35-28, and same problem. Touching the screen freezes the system.

Does anyone know how the ordering of the Xorg logs are? Is Xorg.0.log for the current session, .1.log for the last session, .2.log for the one before that?
Nevermind, the xorg manual page says its the display number. Why do I have 5 displays? It probably doesn't matter...

The Xorg.0.log is the current, then the Xorg.0.log.old, then the Xorg.1.log, and so on.  

Are you sure that it is not the evtouch driver that is crashing?

---

### Post by cheshirekow on 2011-05-25
> **Ayuthia said:**
> The Xorg.0.log is the current, then the Xorg.0.log.old, then the Xorg.1.log, and so on.  

Are you sure that it is not the evtouch driver that is crashing?

I removed evtouch since it didn't do anything after installing it.

---

### Post by Ayuthia on 2011-05-25
Is there anything that is showing up in /var/log/messages?

Somewhat good news, I am able to duplicate your issue with the downgraded xorg-server.  I did find out that utouch was not installed so I installed it and gesturetest failed to work.  Right now I am going to build the utouch packages from the source to see if I can get them to work.  I have found out that the packages that are needed to build the utouch stuff is quite large as it is telling me that it is going to take over 40 minutes to download the dependent packages.

---

### Post by Ayuthia on 2011-05-25
I am still working on getting the gestures to work but I am running the tests for the multitouch.  Can you install mtview and see if it will work for you:
```

sudo mtview /dev/input/eventX

```
Replace eventX with the event that belongs to your touch input.  When you run the application, it should bring up a window.  Maximize the window and then press your fingers on the screen and see how many fingers appear.

---

### Post by cheshirekow on 2011-05-25
> **Ayuthia said:**
> I am still working on getting the gestures to work but I am running the tests for the multitouch.  Can you install mtview and see if it will work for you:
```

sudo mtview /dev/input/eventX

```
Replace eventX with the event that belongs to your touch input.  When you run the application, it should bring up a window.  Maximize the window and then press your fingers on the screen and see how many fingers appear.

I'll give this a try, but since touch is currently freezing the system I suspect it wont be much help. Tonight, I will compile a newer evdev from source and see if that helps with the freezing. Otherwise, I will remember to save this for a) when I get the touch to stop freezing in maverick, or b) the next time I give up on maverick and reinstall natty.

Edit:
I don't seem to have mtview in maverick.

---

### Post by cheshirekow on 2011-05-25
> **Ayuthia said:**
> Is there anything that is showing up in /var/log/messages?

I don't see anything in messages around the time of when I touch the screen and get a freeze. The last messages logged there are from about 2 minutes before that.

---

### Post by cheshirekow on 2011-05-26
Ok, I reinstalled natty. This time on it's own partition so I can try things in both maverick and natty. When I run mtview, it works perfectly. I can draw four different color blobs by putting four fingers on the screen and moving them around.

Still nothing from gesture test, or ginn... And gestures don't seem to be doing anything in unity either (though I don't really know how they're supposed to work).

I've linked a screenshot below (can't figure out how to do attachments on the forums). I can't guarantee this image will stay up forever.

[IMG]http://cheshirekow.com/ubuntu/mtview_screen.png[/IMG]

This was created by putting four fingers on the screen and dragging them all to the right, varying the spread between them.

Edit:
With all the work they put into utouch, I wish they'd given us some more documentation. I still don't have any idea what the utouch stack actually looks like. Though, maybe if I had a better understanding of X it would be obvious. Anyway, I don't know how to continue trouble shooting.

So here's what I've gathed so far:
[list=1]
[*]I touch the hardware
[*]the hardware sends some kind of signal
[*]some kernel module (driver) picks up that signal and generates an "event"
[*]the driver publishes that event to /dev/input/event<#>
[/list]

That's all I understand so far. I don't what comes next. Here's a random guess:

[list=5]
[*]xorg server reads the event from /dev/input/event<#> and generates an x event
[*]possibly this is done by notifying evdev which actually generates the x event
[*]utouch gesture recognition engine gets notification of the x event and interprets it into a "gesture event"
[*]ginn recieves the "gesture event"
[/list]

anyone know better?

Edit:
Just found [this architecture schematic]("https://wiki.ubuntu.com/Multitouch/uTouchArchitecture"). It's exactly what I was looking for, but I'm not sure it really tells me how to troubleshoot it :/. From this document, it appears that evdev actually is a kernel module, runs in kernel space, and generates events which are picked up by X. This document makes me wonder, is there some kind of ginn server component? Or does ginn implement the GEIS and Grail part in place of unity.

---

### Post by cheshirekow on 2011-05-26
FYI lucazade posted [here]("http://ubuntuforums.org/showpost.php?p=10579622&postcount=3502") on installing the PSB driver for Natty. This is what I was looking for before. It requres a downgraded kernel, but uses the newer xorg. I will give this a try at some point.

---

### Post by cheshirekow on 2011-05-26
I took a look at the evdev driver code that I was compiling. Turns out I'm not applying the patches correctly. Anyone know how this is supposed to work? The diff file I applied only appears to diff against the debian package. I.e. it drops three patch files in /debian/patches. I tried to apply those patches on the source but the result wont compile. Any ideas?

---

### Post by Ayuthia on 2011-05-26
> **cheshirekow said:**
> I took a look at the evdev driver code that I was compiling. Turns out I'm not applying the patches correctly. Anyone know how this is supposed to work? The diff file I applied only appears to diff against the debian package. I.e. it drops three patch files in /debian/patches. I tried to apply those patches on the source but the result wont compile. Any ideas?

Can you post the error messages?  I was building them earlier and found that some of the library paths (the .h files in /usr/include/xorg) were not correct in the code and in some of the .h libraries (pixman).

---

### Post by cheshirekow on 2011-05-26
> **Ayuthia said:**
> Can you post the error messages?  I was building them earlier and found that some of the library paths (the .h files in /usr/include/xorg) were not correct in the code and in some of the .h libraries (pixman).

Sure. Here goes (by the way, evidently the correct way to extract and patch a debian source packages is "dpkg-source -x <package>.dsc. Then run ./debian/rules patch). 

```

In file included from evdev.c:34:0:
evdev.h:43:2: error: #error "Need X server input ABI version 12.2 or greater"
In file included from evdev.c:34:0:
evdev.h:119:5: error: expected specifier-qualifier-list before 'ValuatorMask'
evdev.h:129:5: error: expected specifier-qualifier-list before 'ValuatorMask'
evdev.h:224:27: error: expected declaration specifiers or '...' before 'ValuatorMask'
evdev.c: In function 'EvdevSwitchMode':
evdev.c:145:15: error: 'struct <anonymous>' has no member named 'flags'
evdev.c:155:19: error: 'struct <anonymous>' has no member named 'flags'
evdev.c:159:19: error: 'struct <anonymous>' has no member named 'flags'
evdev.c: In function 'EvdevIsDuplicate':
evdev.c:211:15: error: 'struct <anonymous>' has no member named 'min_maj'
evdev.c:216:23: error: 'struct <anonymous>' has no member named 'min_maj'
evdev.c:217:23: error: 'struct <anonymous>' has no member named 'min_maj'
evdev.c:217:42: error: 'struct <anonymous>' has no member named 'min_maj'

```

The first line about the ABI I plan to just comment out. I'm building from source so the ABI shouldn't matter right? The rest looks like an undefined struct ValuatorMask. I'm trying to figure out where that is supposed to come from now.

---

### Post by Ayuthia on 2011-05-26
> **cheshirekow said:**
> Sure. Here goes (by the way, evidently the correct way to extract and patch a debian source packages is "dpkg-source -x <package>.dsc. Then run ./debian/rules patch). 

```

In file included from evdev.c:34:0:
evdev.h:43:2: error: #error "Need X server input ABI version 12.2 or greater"
In file included from evdev.c:34:0:
evdev.h:119:5: error: expected specifier-qualifier-list before 'ValuatorMask'
evdev.h:129:5: error: expected specifier-qualifier-list before 'ValuatorMask'
evdev.h:224:27: error: expected declaration specifiers or '...' before 'ValuatorMask'
evdev.c: In function 'EvdevSwitchMode':
evdev.c:145:15: error: 'struct <anonymous>' has no member named 'flags'
evdev.c:155:19: error: 'struct <anonymous>' has no member named 'flags'
evdev.c:159:19: error: 'struct <anonymous>' has no member named 'flags'
evdev.c: In function 'EvdevIsDuplicate':
evdev.c:211:15: error: 'struct <anonymous>' has no member named 'min_maj'
evdev.c:216:23: error: 'struct <anonymous>' has no member named 'min_maj'
evdev.c:217:23: error: 'struct <anonymous>' has no member named 'min_maj'
evdev.c:217:42: error: 'struct <anonymous>' has no member named 'min_maj'

```

The first line about the ABI I plan to just comment out. I'm building from source so the ABI shouldn't matter right? The rest looks like an undefined struct ValuatorMask. I'm trying to figure out where that is supposed to come from now.

That is where I am at right now too.  I am thinking that there is another dependent package/library that we have not patched and applied yet so it is not compiling.  I have not had a chance to verify it yet though.

---

### Post by cheshirekow on 2011-05-26
> **Ayuthia said:**
> That is where I am at right now too.  I am thinking that there is another dependent package/library that we have not patched and applied yet so it is not compiling.  I have not had a chance to verify it yet though.

I'm thinking the same thing. I figured libxi was probably the one, but I downloaded the source, patched, and compiled without errors and it did not seem to fix the problem. However, I asked a question on the utouch launchpad [here]("https://answers.launchpad.net/utouch/+question/159060") and according to the answerer, we should just need evdev. I don't think he looked at the packages in the EMGD ppa though so maybe he's assuming something is on the system that is not.

Edit:
I don't think evdev 2.6.0 can be compiled for xorg 1.9. By looking at the git changelogs (i.e. see [here]("http://permalink.gmane.org/gmane.comp.freedesktop.xorg.announce/1336")) it looks like this "Valuator Mask" concept wasn't even checked in until 1.9.99. I think 1.10 *is* required for this evdev driver. I'll try the maverick evdev.

Edit 2: 
2.3.2 compiled ok. I got a bunch of warnings about stuff being deprecated. After installation non of my input devices work (mouse, keyboard, touchscreen). The pen works fine though (as it should, since it's on the wacom driver).

Edit 3:
Got a response from Stephen Webb on the Canonical utouch team over at my [launchpad question]("https://answers.launchpad.net/utouch/+question/159060"). It looks like the natty evdev *DOES* requires xorg 1.10. Well, at least it requires the newer ABI, which I think means either xorg 1.9.99 or 1.10.x. He said it shouldn't take too much effort to backport, so I will add a bug to backport it to the older ABI... but first I'm going to look at installing the PSB driver in Natty with a downgraded kernel.

---

### Post by aquarat on 2011-05-30
Perhaps not the most important thing ever, but I re-installed Ubuntu 10.04, upgraded to 10.10, installed psb and a few other libraries and BAM! VAAPI works using mplayer-vaapi.

It seems to be using poulsbo as the decoder (as opposed to crystalhd) :

```

aquarat@slatrat:~$ vainfo
libva: libva version 0.31.1-sds1
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/psb_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Intel GMA500 - 5.0.1.0046
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointMoComp
      VAProfileMPEG4Simple            :	VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

I haven't checked cpu usage yet but it happily plays back 720p H264 MKV files using mplayer-vaapi while underclocked to 800MHz.

I'm now busy compiling VLC with VAAPI support (which is actually an FFMPEG option).

---

### Post by krustybaguette on 2011-07-19
> **rothgar said:**
> I'll get the output for you guys later this weekend. I will go back to 10.10 just so I can get something to load and then we will work our way to something more functional.

The USB does work (although there is only 1 port). What I have been doing is plugging in a Mac keyboard and using the 2 USB ports on the keyboard for the USB flash drive and mouse.

I have a Slate 500 and there is one USB on the tablet and another 2 USB ports on the docking station along with an HDMI connector. I just saw one on sale on craigslist because the owner says it won't run Linux. I'd be more interested in getting HP to release an installable version of webOS and run it as a Win7/WebOS dual boot. Haven't found anything indicating that HP has done so yet.

---

### Post by cheshirekow on 2011-07-19
> **krustybaguette said:**
> I just saw one on sale on craigslist because the owner says it won't run Linux. 

You must be in the boston area. That's my slate on craigslist :(.

---

### Post by aquarat on 2011-09-19
Did you sell your slate chesirekow ?

---

### Post by cheshirekow on 2011-09-22
Nope. No one wants it on craigslist or ebay. Not even at a $200 loss. I can't say I blame them.

I've been using the psb-gfx driver for a while. It's not too bad. The compiz effects emulation is really slow, and I wish they just didn't try to do that in unity, but whatever.

I've got a new question though. When I'm using the stylus, if I pick up the pen and move it to a new location, and then press back down, the button press event appears to be generated before the mouse move event. In xournal, this means I get random lines that jump all over the place. Any idea what the problem could be? I've built the latest xf86-input-wacom with no change.

---

### Post by lisati on 2012-04-27
Thread closed, may it rest in peace.

---

