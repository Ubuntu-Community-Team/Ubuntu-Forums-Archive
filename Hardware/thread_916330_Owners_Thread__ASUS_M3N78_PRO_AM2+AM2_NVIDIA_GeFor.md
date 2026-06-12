---
title: "Owners Thread:  ASUS M3N78 PRO AM2+/AM2 NVIDIA GeForce 8300 HDMI ATX AMD Motherboard"
date: 2008-09-10
forum: Hardware
---

### Post by ghat on 2008-09-10
hi guys, 

Got a new  [ASUS M3N78 PRO AM2+/AM2 NVIDIA GeForce 8300 HDMI ATX AMD Motherboard ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131320")

Installed Ubuntu LTS and seems to work fine. I have some problems with  the nvidia driver. 

Starting this thread for owners, to discuss problems and workarounds.

---

### Post by badmoon on 2008-09-18
I just configured mine today and am also having problems with the nvidia restricted drivers.  I tried both the -new and the original ones.  Both didn't work.  BTW I'm using the 16-pin VGA output (not the HDMI or DVI).

I get this error in the Xorg.0.log:
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

Any suggestions on what do due next would be much appreciated!

---

### Post by biro on 2008-09-18
Hello lads,

I had the same problems, but I solved removing the linux restricted drivers and following the instruction for manual installation from this post [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=880787]("http://ubuntuforums.org/showthread.php?t=880787")[/COLOR].

So download from [COLOR="#0000ff"][http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")[/COLOR] your drivers. I downloaded the Linux IA32 v173.14.12.

Make sure you removed the envy package

Then:
```

sudo apt-get install build-essential
sudo /etc/init.d/gdm stop

```

From the the directory in which you downladed the file run and follow the package instruction:
```

sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run

```

Restart the gdm:
```

sudo /etc/init.d/gdm start

```


Reboot the system (just to be in the safe side). 


Good luck...

Cheers,
Roberto

---

### Post by badmoon on 2008-09-18
Roberto,

I followed your directions and it worked perfectly.  You're the best!

Thanks!
Moon

---

### Post by Aff Controlz on 2008-09-26
I just bought an open box Asus M3N78 Pro.  Unlike other open box Items I have purchased before (a few things missing), this came as a bare board.  I am in need of the VGA cable/plug for the onboard video.  Anyone not using the VGA plug on their board willing to sell me it?  This wouldn't be a problem except the only rear plug on the board is an HDMI plug and I still have an analog monitor.  If I had a digital LCD I could just use a HDMI to DVI cable.

Please help my poor butt out,
Brent

---

### Post by Zaff on 2008-09-27
Has anyone else experienced sound problems ? This threads describes what I get : [http://ubuntuforums.org/showthread.php?t=881363](http://ubuntuforums.org/showthread.php?t=881363)
It doesn't look like there's going to be a fix for that crackling sound problem any time soon. I'm just wondering if it does this for everyone as well...

---

### Post by tuskentower on 2008-10-20
> **ghat said:**
> hi guys, 

Got a new  [ASUS M3N78 PRO AM2+/AM2 NVIDIA GeForce 8300 HDMI ATX AMD Motherboard ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131320")

Installed Ubuntu LTS and seems to work fine. I have some problems with  the nvidia driver. 

Starting this thread for owners, to discuss problems and workarounds.

Since you are not having problems I am going to throw this weird one in there.  I am being dropped to the initramfs with my old 8.04 installation disk.  From what I have been able to piece together it is a driver issue with the chipset on this mobo being to new (doh!).  I am going to download and install with a newer 8.10 install disk and post back.

---

### Post by tuskentower on 2008-10-20
> **tuskentower said:**
> Since you are not having problems I am going to throw this weird one in there.  I am being dropped to the initramfs with my old 8.04 installation disk.  From what I have been able to piece together it is a driver issue with the chipset on this mobo being to new (doh!).  I am going to download and install with a newer 8.10 install disk and post back.

The 8.10 install CD didn't work.  My new 8.04 CD does.  Go figure.

---

### Post by bswanboat on 2008-10-26
Installing Ubuntu 8.04 64 on this board has been the most discouraging install I have done. The screen just keeps going blank. I have been try to follow the steps in the post to update the Nvidia nForce driver for 8300 but so far no success. Has anyone else had this problem?

Suggestions would be more than appreciated.

---

### Post by neil291094 on 2008-10-27
hi, i just got the asus m2n78 pro and when i fitted the vga otput and connected up mymonitor it does not send any signal to the monitor. I have tried it on its own and with the graphics card. I am out of ideas can you help me?
Thanks

---

### Post by ghat on 2008-11-07
hi

upgraded to Intrepid 8.10 and installed nvidia prop driver from nvidia website and it works...

I still see the following messages in my /var/log/messages

Nov  5 09:08:27 desktop pulseaudio[8715]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  5 09:08:27 desktop pulseaudio[8717]: pid.c: Stale PID file, overwriting.
Nov  5 09:08:27 desktop pulseaudio[8717]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  5 09:08:27 desktop pulseaudio[8717]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted


also GLX performance is horrible, (with glxgears) I bet this is because of the default intrepid kernel.
I am expecting at least something like 

4515 frames in 5.0 seconds = 903.000 FPS
5176 frames in 5.0 seconds = 1035.200 FPS
5304 frames in 5.0 seconds = 1060.800 FPS
5287 frames in 5.0 seconds = 1057.400 FPS


g

---

### Post by bswanboat on 2008-11-16
Fianlly, I have Kubuntu 64 installed! I used the install disk since I could not get around the busy box issue when installing Ubuntu 8.10 on another machine. 

The Asus M3N78 Pro was either leaking juice to the case, the motherboard was defective (the eth0 stopped working as well ), or the Anatec 500D psu was defective. I did the RMA thing on the motherboard, put electical tape over the motherboard spacer, and went to a PC Power & Cooling 610 watt psu. 

The screen has not gone blank, not one time since I used the install disk. Now it is up and working! Whew!

---

### Post by jonahhorowitz on 2009-02-06
I have the M3N78 with a Phenom II 940.  I've been having the blank screen problem over and over, so I'm glad to see it's not just me.

I've only been using the HDMI port with the DVI adapter to plug into my LCD monitor.  It works for 10 minutes or so and then goes blank.  It does it during the install process or just using the live cd.

I'm about 83% done using the curses installer on the mini.iso.  You might try that if you're having problems.  I'll post an update once I get the installation finished.

---

### Post by ZarathustraDK on 2009-02-10
I just purchased a M3N78 PRO (geforce 3800 onboard) with an Athlon FX2 2.5GHz chip for a HTPC setup. It'll be interesting to see how it plays out.

As far as I understand getting the graphics to work is a matter of using the proprietary nvidia-drivers (normal or beta?) without having any other nvidia-related drivers/cruft installed from the get-go.

I'll let you know how it plays out.

3 Terabyte goodness, here I come :)

---

### Post by designed76 on 2009-02-15
I have the same motherboard. Will that work with my 64-bit xubuntu?

---

### Post by ZarathustraDK on 2009-02-15
I tried using Kubuntu 64bit with the m3n78 pro. I don't know if it's just me but I got a lot of repo-errors in adept, so I just stuck with regular Ubuntu. In relation to graphics: After a clean install I simply installed the nvidia 1.80 drivers through Synaptic (they're there, but they don't show up under the "restricted drivers"-dialog in intrepid), then ran nvidia-settings as root, configured it to my liking and chose "save x-configuration to file" (or something like that) before closing it. It all looks nice and tight, although I seem to get some graphics-corruption if run wobbly windows-plugin for too long.

Now, a question for you m3n78 pro-owners. How on earth do you set the HDMI-out as default primary video? I just get a no-signal screen when I plug it into my tv, so I'm forced to use the VGA-out instead. Very frustrating, as it is what keeps me from putting the pc into its place in the rack. Is it a jumper somewhere? In the BIOS? I'm tearing my hair out on this one.

A cookie for the person who can answer that one :popcorn:

Edit: I got a little further. Seems like HDMI is not capable of showing "standard" graphics like the commandline and basic gnome-desktop without the Nvidia-drivers installed (ver 180 here). Now my problem is that somehow the green channel does not go through, so everything is kinda pink here. Yes, I've checked the cable, yes, there's nothing wrong with the TV. Oh well, VGA is just as snazzy, don't need the audio part of HDMI anyway, got surround and SP/DIF for that if I need it...

UPDATE:
The graphics-part of this motherboard is major pain in Ubuntu. In regular Ubuntu it regularly crashes when using compiz-fusion (specifically when using wobbly windows, or trying to open an "open file"-dialog. In Kubuntu the screen freezes when doing certain things, leaving no other option than to press the reset button. These were with the nvidia-driver available in the repository (180.11 I think).
After that I installed Xubuntu with the latest drivers from Nvidia's site (180.77 I think, they're newer than the repo-ones), and everything is dandy. I'll still get graphics-corruption and crash if I use wobbly windows, but I can live without that plugin for now. The rest is good.

It could be that it's possible to run Ubuntu/Kubuntu with the latest Nvidia-drivers from Nvidias site, somebody else will have to try that, I'm tired of reinstalling :)

Now I just need to seduce my TV to run 60Hz instead of 58.80Hz, I'd give an arm and a leg and a kidney for the magic modeline that'd make that happen.

---

### Post by mulluysavage on 2009-02-23
I am trying Roberto's procedure for installing the Nvidia driver, but when I try to stop the gdm I get the "command not found" error. What to do?


> **biro said:**
> Hello lads,

I had the same problems, but I solved removing the linux restricted drivers and following the instruction for manual installation from this post [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=880787]("http://ubuntuforums.org/showthread.php?t=880787")[/COLOR].

So download from [COLOR="#0000ff"][http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")[/COLOR] your drivers. I downloaded the Linux IA32 v173.14.12.

Make sure you removed the envy package

Then:
```

sudo apt-get install build-essential
sudo /etc/init.d/gdm stop

```

From the the directory in which you downladed the file run and follow the package instruction:
```

sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run

```

Restart the gdm:
```

sudo /etc/init.d/gdm start

```


Reboot the system (just to be in the safe side). 


Good luck...

Cheers,
Roberto

---

### Post by mulluysavage on 2009-02-28
I have a problem where my motherboard splash screen hangs - if I disconnect my usb HD and restart then it proceeds past the splash screen. Sometimes this happens, sometimes not!

---

### Post by EXCiD3 on 2009-06-06
> **badmoon said:**
> I just configured mine today and am also having problems with the nvidia restricted drivers.  I tried both the -new and the original ones.  Both didn't work.  BTW I'm using the 16-pin VGA output (not the HDMI or DVI).

I get this error in the Xorg.0.log:
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```Any suggestions on what do due next would be much appreciated!


Anyone get the Nvidia card working on Ubuntu 8.04 LTS? I have the M4N78 with an 8300 and I have installed the 169 driver from the repo as well as the very latest 180.60 driver with no luck, getthing the same error as above, and saying the chipset cannot be found. :(

---

### Post by Splarz on 2009-06-22
hallo to everybody!
I found this topic searching google, the aim was finding some solutions about the bad experience with nvidia geforce 8300.
reading the topic i discover i'm luky: not so terrible troubles but a big difference in performance between windows xp (or windows 7) and xubuntu (8.10 and now 9.04). when i move or drop down windows linux is not fluid and menus are jerkily: the impression is that the whole system is very slow.
have you noticed the same behaviour?
thanks!

---

### Post by Chemical Imbalance on 2009-06-22
> **Splarz said:**
> hallo to everybody!
I found this topic searching google, the aim was finding some solutions about the bad experience with nvidia geforce 8300.
reading the topic i discover i'm luky: not so terrible troubles but a big difference in performance between windows xp (or windows 7) and xubuntu (8.10 and now 9.04). when i move or drop down windows linux is not fluid and menus are jerkily: the impression is that the whole system is very slow.
have you noticed the same behaviour?
thanks!

I have the motherboard discussed in this thread and have no problems with performance with the nvidia drivers installed (180.60).

---

### Post by Splarz on 2009-06-23
> I have the motherboard discussed in this thread and have no problems with performance with the nvidia drivers installed (180.60)
so, if you use windows too, can you confirm you do not notice any difference between the OS?

how can i discover if my driver is 180.60? in driver hardware they talk about 180, but it's not specified furthermore.

ps: thanks for the replay :)

---

### Post by Chemical Imbalance on 2009-06-23
> **Splarz said:**
> so, if you use windows too, can you confirm you do not notice any difference between the OS?

how can i discover if my driver is 180.60? in driver hardware they talk about 180, but it's not specified furthermore.

ps: thanks for the replay :)

I use Windows XP occasionally and I have not noticed any difference in performance.

To find what version of nvidia drivers you have in Linux:

```
 cat /proc/driver/nvidia/version
```

---

### Post by Splarz on 2009-06-23
uh, it's 180.**44**! so you installed the driver manually, i think!

---

### Post by Chemical Imbalance on 2009-06-23
Yes, I did.  I'm not sure what you are asking.

Here are the drivers: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by Splarz on 2009-06-23
my last question? i think it's my terrible english's fault :P ubuntu by default (i've just discovered) it's two driver versions late; i think that installing the last driver my performance problems will disappear.
thank to all!

ps: can i install v185.18.14?

---

### Post by Splarz on 2009-06-23
I added [these repos](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) and the situation has imporoved a lot!
Now my driver version is 185.18.14

Again: thanks (and sorry for my english)

---

### Post by Chemical Imbalance on 2009-06-23
> **Splarz said:**
> I added [these repos](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) and the situation has imporoved a lot!
Now my driver version is 185.18.14

Again: thanks (and sorry for my english)

Glad you found a solution!

Your english is great, by the way.  It's not like I can speak Italiano.  ;)

---

### Post by EXCiD3 on 2009-06-24
I'm going to contact Asus about the M4N78 usb issues I've been having. Also going to see what using the usb->ps/2 converter on my mouse does to help the situation. Keyboard loses power after unplugging it when the mouse goes out so maybe I won't notice any problems with mouse on ps/2.

---

### Post by Chemical Imbalance on 2009-06-24
> **EXCiD3 said:**
> I'm going to contact Asus about the M4N78 usb issues I've been having. Also going to see what using the usb->ps/2 converter on my mouse does to help the situation. Keyboard loses power after unplugging it when the mouse goes out so maybe I won't notice any problems with mouse on ps/2.

The weird thing is that it doesn't happen in XP or Intrepid for me.

Only Jaunty and Fedora 11 so far.

---

### Post by EXCiD3 on 2009-06-25
Yeah, It's happened in Debian for me now. I may try Intrepid and see if it happens or not. It's driving me nuts!

---

### Post by Chemical Imbalance on 2009-06-25
> **EXCiD3 said:**
> Yeah, It's happened in Debian for me now. I may try Intrepid and see if it happens or not. It's driving me nuts!

Intrepid doesn't agree with my onboard sound, so I'm just gonna dig in and wait until Karmic reaches a later alpha stage.

---

### Post by EXCiD3 on 2009-06-25
There's always something every release. :( I need to see if I can get my usb modem working at full speed in linux. I'm just going to settle down and use XP for a while on my desktop at least.

---

### Post by Chemical Imbalance on 2009-06-25
> **EXCiD3 said:**
> There's always something every release. :( 

Yeah, and this is the worst yet. ](*,)

---

### Post by tehfade on 2009-10-13
Bump for anyone who can tell me how to get video output on HDMI. I've installed and updated Xubuntu 9.04, and I can't get any video through HDMI! Haven't even looked at the sound issues yet, since that isn't working. I posted a thread about it [here]("http://ubuntuforums.org/showthread.php?t=1290196").

---

### Post by EXCiD3 on 2009-10-14
Do you have the nvidia driver installed? You should be able to configure it through the nvidia-settings tool.

---

### Post by tehfade on 2009-10-22
Yes, I have the 1.80 drivers installed. I've run nvidia-settings, and I'm only seeing one display, CRT-0. I don't see any settings to configure a different output in there. 

BTW, my mobo is actually an M3N78-EM, not the PRO, if that makes a difference. I looked at dmesg, and /var/log/messages, and can't find any sort of errors in there either. Any ideas?

---

### Post by ghat on 2009-10-28
hi
I have used the HDMI port with no problems, I however dont do the layman nvidia-settings..

I use dpkg-reconfigure xserver-xorg which gives a empty file... then hand edit the /etc/X11/xorg.conf file to make sure that the "nvidia" driver is used and then start the X server with the HDMI cable plugged into the monitor. Prior to that I make sure the monitor is set to the HDMI input.

The nvidia.. driver detects the monitor and self configures it... usually... 
It gives each of the panels it detects names like CRT-0 DFP-1 etc....all this information is logged in the /var/log/Xorg.0.log file.. I then use that file as reference and lalso use the UNIX read me on the nvidia driver page to build a detailed /etc/X11/xorg.conf with whatever config I want... 

Here is an example, (the example is not for this MOBO)
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0  100
    Screen      1  "Screen1" 1920 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    FontPath        "unix/:7100"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    # generated from data in "/etc/sysconfig/mouse"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "IMPS/2"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from data in "/etc/sysconfig/keyboard"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbLayout" "us"
    Option         "XkbModel" "pc105"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Dell Inc"
    ModelName      "DELL 2407WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Dell Inc"
    ModelName      "DELL 2001FP"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 285"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "MetaModes"   "DFP-0: 1920x1200, CRT-0: 1920x1200"
    Option         "ModeValidation" "DFP-0: NoMaxPClkCheck,NoEdidMaxPClkCheck"
    Option         "XvmcUsesTextures" "true"
EndSection
Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 285"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "MetaModes"   "DFP-1: 1600x1200, CRT-0: 1600x1200"
    Option         "ModeValidation" "DFP-0: NoMaxPClkCheck,NoEdidMaxPClkCheck"
    Option         "XvmcUsesTextures" "true"
    Option         "Rotate" "CCW"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1920x1200 +0+0"
    Option "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1600x1200 +0+0"
    Option "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by 16777216 on 2009-12-10
Has anyone found a solution to the USB problems?

My mouse, keyboard, and printer keep hanging up and I have to reset the computer.
If I could just reset the USB system via comandline or script as I now use the keyboard on the PS/2 port with an adapter.
Unfortunately, my motherboard only has one PS/2 port and it is keyboard only or I would have the mouse in it and use an on screen keyboard during lockups.

---

### Post by EXCiD3 on 2009-12-11
> **16777216 said:**
> Has anyone found a solution to the USB problems?

My mouse, keyboard, and printer keep hanging up and I have to reset the computer.
If I could just reset the USB system via comandline or script as I now use the keyboard on the PS/2 port with an adapter.
Unfortunately, my motherboard only has one PS/2 port and it is keyboard only or I would have the mouse in it and use an on screen keyboard during lockups.

If you have a USB hub, plug everything into that, and then plug the hub into your motherboard or a case USB plug. Move it around to whichever port(s) don't have issues and you should be alright. I know at least for me that the bottom 2 usb ports don't cause issue on my M4N78 PRO but the top two seem to be the ones causing the lockups.

---

### Post by 16777216 on 2009-12-11
Every USB port on it locks up simultaneously.

If I put a hub on it, that, and everything on it would lock up too.

The kernel module needs fixing for this mobo's crappy firmware.

---

### Post by colo on 2009-12-25
Is there anyone of you who succeeded in having the mainboard regulate fan-speeds via voltage regulation? If yes, how?

---

### Post by ghat on 2010-08-14
hi Guys, 

I forgot I started this thread when I bought the motherboard...

Can anyone of you comment on the following one

[http://ubuntuforums.org/showthread.php?t=1547552](http://ubuntuforums.org/showthread.php?t=1547552)

about the same MB 

G

---

### Post by ub-newbie on 2010-12-24
[SOLVED] but I'm leaving this here for others reference.. Turns out it was a TV problem...When I switched to cable there was no audio there either.. And I had "unchecked" a IEC958 in Gnome ALSA Mixer. 
----------------------------------------------------------------
OS - 10.04x64
HDMI sound was working, but I did some upgrades and it has went away (upgrades from XBMC and Ubuntu sources)

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

and 
```
$ aplay -D plughw:0,3 3.wav
Playing WAVE '3.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

```
does not give audio output (nor does Dev 1), but Dev 0 does give audio out via analog jack.

I had (a long time ago) added this to /etc/pulse/default.pa
```
load-module module-alsa-sink device=hw:0,3
```

I have checked every volume setting I can find, including ```
sudo alsamixer
```and everything is set to max.

When I open **Applications, Sound and Video, Pulse Audio Control** I can see the jumping audio bar (when RythmBox is playing).  In that program (PAC) my options are "Internal Audio, Internal Audio Analog, or Simultaneous" and I have Simultaneous selected.

ALSA is 1.0.21


Can anyone point me it the correct direction?

---

