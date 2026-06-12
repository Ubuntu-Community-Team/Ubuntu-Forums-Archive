---
title: "Webcam?"
date: 2004-10-16
forum: General Help
---

### Post by Termina on 2004-10-16
I'd like to use my webcam in Ubuntu, but in /dev there doesn't seem to be a '/dev/video' file, which is what I seem to need to test my webcam with xawtv (which I installed via synaptic).

Could anyone help me out with that? Thanks!


EDIT:

I tried to set up a /dev/video using the BTTV mini-howo ([http://www.faqs.org/docs/Linux-mini/BTTV.html](http://www.faqs.org/docs/Linux-mini/BTTV.html))

Trying to run it:

will@Hivemind:/dev $ xawtv -c /dev/video
This is xawtv-3.93, running on Linux/i686 (2.6.8.1-3-386)
Cannot open plugin directory ${exec_prefix}/lib/libquicktime
Did you forget "make install"? You need it because
libquicktime cannot load plugins out of the sourcetree
can't open /dev/video: No such device
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video: No such device
v4l2: open /dev/video: No such device
v4l: open /dev/video: No such device
no video grabber device available

Trying to run xawtv without arguments:

will@Hivemind:/dev $ xawtv
This is xawtv-3.93, running on Linux/i686 (2.6.8.1-3-386)
Cannot open plugin directory ${exec_prefix}/lib/libquicktime
Did you forget "make install"? You need it because
libquicktime cannot load plugins out of the sourcetree
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct

---

### Post by OldKraut on 2004-10-26
Finally, just before before getting completely crazy, I managed to make my Logitec Quickcam Express ( USB) work without being an expert.
- I found a page at sourceforge with the driver
- I loaded the driver and unpacked it
- I followed the instructions in the readme-file

The device manager supported the parameter-IDs of my cam (vendor etc.).
Synaptic was necessary to provide the basic ubuntu-system with kernel-headers and -source (linux-headers and linux-source for the recent system as this forum told me) and gcc.

A configuration tool for the cam was provided with the driver  - I needed it to find out the video channel I had to select in gnomeeting.

So, follow the (error) messages of the script and don't give up. After more or less try and error you will succeed. If not, don hesitate to ask me. Though I don't really know what I did, I'll try to help you.

---

### Post by uggeli on 2004-11-25
Hmm could you give a step by step guide how you managed to get things work? I hava Dexxa Webcam but in windows it uses Logitech Quickcam Express drivers so I should get it working the way you did.

What I hava done so far:

I follow [this](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Webcam-HOWTO.html#DEV-MANUAL) guide, first step 3.2 and then 3.3 where I go to step 4.5 and follow the link there. And then I found myself in [this](http://qce-ga.sourceforge.net/) page and downloaded driver "Logitech Quickcam VC (USB and Parallel)" which was mentioned there. Now I don't have a clue what to do (yes I have read the readmefile). It's just that I'm totally newbie with linux, so I need help for this even it probably is some basic things to you, but for me it isn't.

Feels like I have to switch back to windows cause I simply don't get things working in here with ubuntu. :( Or if I do it is painful, like configuring 3d to ati. Well I'm not giving up yet, cause otherways this is so great os after widows.. :)

---

### Post by uggeli on 2004-11-29
Just checked via device manager and my webcam seems to be there as QuickCam Express. Should it then work now or do it still needs some drivers? GnomeMeeting keeps saying it doesn't find device when trying to use V4L.

Edit: Just managed to install [this](http://sourceforge.net/project/showfiles.php?group_id=12924&package_id=86447&release_id=276924) driver and now GnomeMeeting finds the device, but the screen where picture should be is green.. :( Allso that when installing drivers there was mention that I should but 'modprobe quickcam' somewhere as root so it runs at startup but I don't know how to do that step. Well it wouldn't help much since picture doesn't show up, but would be nice to know for future..

---

### Post by uggeli on 2004-12-04
Well I put little more information here so maybe you guys can tell me what's wrong here.

1. when I check sudo lsmod there is webcam mentioned:

"quickcam 76132 0
videodev 9984 1 quickcam"

2. when I type 'xawtv - hwscan' in to terminal I got list:

This is xawtv-3.94, running on Linux/i686 (2.6.8.1-3-k7)
looking for available devices
port 61-61
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay

ioctl: VIDIOC_QUERYCAP(driver="";card="";bus_info="";version=0.0.0;capabilities=0x0 []): Unknown error 515
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l
    name : Logitech QuickCam USB
    flags:  capture


3. When I try to run xawtv I got errormessage to terminal (xawtv starts with black screen):

This is xawtv-3.94, running on Linux/i686 (2.6.8.1-3-k7)
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



So there is no picture via webcam in any situation (just green or black screen). If someone can help me with this, then please do I don't know what to do anymore.. :(

---

