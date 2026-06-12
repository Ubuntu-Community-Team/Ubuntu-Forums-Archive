---
title: "Dell XPS  M1730"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by tseval on 2007-09-29
Hey folks,

I'm about to place an order for one of these beasts:

[http://www1.euro.dell.com/content/products/productdetails.aspx/xpsnb_m1730?c=uk&cs=ukbsdt1&l=en&s=bsd](http://www1.euro.dell.com/content/products/productdetails.aspx/xpsnb_m1730?c=uk&cs=ukbsdt1&l=en&s=bsd)

However, I need to run linux on it. I know that the previous XPS laptops run very nicely on Ubuntu (I have one myself), but this beast is a bit different. For one thing it has Dual GeForce 8700 cards in SLI config. It also has a 400Gig Raid0. I work in 3D graphics development so the most important part is the graphics card, and I need to be able to develop OpenGL apps on it.

I will order it with the "Next Gen Intel wireless-N card". I'm not sure which one this is, but I guess it must be this one:

[http://www.intel.com/network/connectivity/products/wireless/wireless_n/overview.htm](http://www.intel.com/network/connectivity/products/wireless/wireless_n/overview.htm)

Anyone have any experience with this computer or similar hardware configs? Any known hardware in it that may not work? Will the Nvidia linux drivers support SLI? 

Also, should I install Feisty or Gutsy on it?

Cheers.

---

### Post by oc3an on 2007-10-22
I have one of those laptops and am running Gutsy on it.

SLI - not sure if it's working or not, but the nvidia drivers work fine.
Wireless - worked out of the box, no problem.

I can't get the G15(?) lcd working, but I haven't really tried yet, and I can't get the memory card reader working yet either, but I haven't had a good chance to play yet.

Anybody else got one of these?

-Patrick

---

### Post by bongey on 2007-10-26
I just got one  .  Did you do a x64 install or x86  ? I read on the nvidia forum that the driver doesn't work in sli yet.

---

### Post by bongey on 2007-10-27
Just install gusty x86 . Nvidia drivers give me a blank screen , nothing nada. Are you using the distro nvidia drivers or ones from nvidia? Maybe you could post your xorg for me .

---

### Post by SaguratuS on 2007-11-06
Some notes on what I've encountered so far with my M1730

1. If you're using more than one m-pcie slot, you must use a 64 bit distribution.  It appears that there are some unusual IRQ related issues otherwise

2. No SLI support, topic open on nvnews - [http://www.nvnews.net/vbulletin/showthread.php?t=100677](http://www.nvnews.net/vbulletin/showthread.php?t=100677)

3. As with most integrated audio, Built in audio on the M1730 is no different and without any postprocessing, it's a nightmare if you're a bit of an audiophile (On any os).  The only way to get audio up to a semi-decent level of quality is to use a heavy duty equalizer, such as a 20-40 band xmms eq plugin or a logarithmic eq for winamp in addition to the creative software audigy drivers.  Popping / crackling is still common and impossible to outright eliminate, however one benefit the M1730 seems to have is the lack of background noise from dirty power or other interference.

4. No LED control on linux, not that it really matters.  There are ways to get the XPS lcd working, as it's the same controller as what's on the G15 gaming keyboard.

5. Haven't trieid the integrated camera or mic yet, will update when I get some results.

Everything else appears to work fine, would like to swap out my 8700m cards with something from ATI, but I'm pretty sure all dell systems have proprietary interfaces for video, not MXM.

---

### Post by Amalsek on 2007-12-19
I currently own a M1730, and I will say only this : go for ubuntu 64bits. I've never managed to make work the nvidia driver in 32bits, but works just fine in 64. And don't forget to go for the envy driver !

On another note, I got a problem with HAL & dbus ( gnome mixer crashing at start, and themes not working), but managed to get rid of with the following:

```

>$ sudo rm /var/lib/dbus/machine-id
>$ sudo dbus-uuidgen --ensure
>$ sudo aptitude reinstall --purge hal

```

Then reboot.

---

### Post by wiresquire on 2007-12-20
Hey guys & gals

I just got an m1730 and will be looking to install Ubuntu 7.10 soon. I decided to try the Live CD (AMD64 of course!) and am having some problems.

It seems like it's video driver/display related, but I can't work it out.

[LIST]
[*]When I boot, I don't get the splash screen with the 'status bar'. The screen is completely off - not blank or dark, but off. 
[*]Then I will get an "X-ish" looking screen asking for my display settings. I think it says something like "Can't work out your display - using safe graphics" or the like. 
[*]I can set the vga resolution and it seems to look correct
[*] It then looks like X crashes. I get the blinking cursor on the X screen/console, and it dumps me back to the first screen/console.
[*]I can get to other consoles OK.
[/LIST]

xorg.conf says it's loaded the vesa driver. I tried a couple of times with selecting the nVidia driver (ie one on the cd, not the proprietery nvidia), but am getting lost :(

Can anyone help or give tips on if they have got the desktop live CD going, what they did or how they got Ubuntu installed ?

Thanks
ws

---

### Post by wiresquire on 2007-12-20
Well, I have 7.10 amd64 installed.

The screen/graphics problems are still the same as above. I will try the nvidia drivers tomorrow....:popcorn:

Any help still welcome !

ws

---

### Post by tdeboeser on 2007-12-20
Goto [Alberto']("http://albertomilone.com/nvidia_scripts1.html")s site and download "envy", it's a wonderful py script that'll install your driver without trouble.  

There is an "envy" in the repository, but it's older...

Tom de

---

### Post by wiresquire on 2007-12-21
Thank you, tdeboeser !!!

That was a bit scary, but things are looking a **lot** better now.

It installed the 100.x driver. I was interested in the 169 driver, which didn't seem to be available via Envy. I had seen that it had SLI support for the M1730, but it seems there are too many fans.
Bwahahahahahaa :lolflag:

ws

---

### Post by tdeboeser on 2007-12-21
Cool... good to hear

But the credit goes to Alberto.  He's been at the script for a while now, and he's responsive to questions.

Tom de

---

### Post by wiresquire on 2007-12-23
Things seem to be running OK. Still plenty I haven't played with properly. I have been distracted a bit with eye candy of Compiz.
The webcam seems to be working via Ekiga. Well, except there's an ugly guy there all the time.... :)

One problem is that I can't get the microphone(s) to work. Eg, using Sound Recorder.

I googled a lot and have found that we have the Intel 82801H (ICH8 Family). Codec: SigmaTel9228.

I had added 
options snd-hda-intel probe_mask=1 model=3stack
to /etc/modprobe.d/alsa-base
but still seem to be getting no microphone input?

Has anyone got tips on this?

---

### Post by tdeboeser on 2007-12-23
> **wiresquire said:**
> Things seem to be running OK. Still plenty I haven't played with properly. I have been distracted a bit with eye candy of Compiz.
The webcam seems to be working via Ekiga. Well, except there's an ugly guy there all the time.... :)

One problem is that I can't get the microphone(s) to work. Eg, using Sound Recorder.

I googled a lot and have found that we have the Intel 82801H (ICH8 Family). Codec: SigmaTel9228.

I had added 
options snd-hda-intel probe_mask=1 model=3stack
to /etc/modprobe.d/alsa-base
but still seem to be getting no microphone input?

Has anyone got tips on this?

I could use a tip or two hear too - I've got 2 laptops with SigmaTel 92xx's that don't have sound...


Tom de

---

### Post by wiresquire on 2007-12-24
There's a bazillion threads out there on these chips.

For general instructions, you might try [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

From what I have read (multiple bugs etc), it seems that the real bug for my m1730 is :
[https://bugs.launchpad.net/dell/+bug/153963](https://bugs.launchpad.net/dell/+bug/153963)

hth
ws

---

### Post by wiresquire on 2007-12-26
I still have the microphone problem.  

Anyways, I got around to fine-tuning a couple of things, and thought I would share:
1. Solving my black screen on boot and shutdown.
Good information [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930"). 
Basically, I set the usplash.conf to 1024x768, added vga=791 to the boot options, and then modified the modules/blacklist per orange2k's post. Voila!
2. The touchpad was driving me nuts as the area for vertical scrolling was too large. The post [here]("http://ubuntuforums.org/showthread.php?t=519712") gave me the clue. I needed to add 
Option          "SHMConfig"             "on" 
to the Synaptics mouse section in xorg.conf to enable me to see the output of synclient.
5700 seems about right for me. This lets me slide my finger along the right edge for the touchpad to scroll.

Now, if I can just get this internal microphone working, I'll almost be there!

hth
ws

---

### Post by davethelorax on 2008-01-03
I've gotten the video to work great with Ubuntu 7.10 64bit, the restricted nvidia drivers rock.  I have also installed Wine and Compiz and can spin a running Warcraft around on a projected cube of desktops (Try that with Vista), but I can't get the integrated camera to work.  I saw that one poster had gotten the integrated camera working but no details were given.  Has anyone gotten that camera working and can share the details.

Thus far, I've tried to get information on the camera using "caminfo" which says it finds the camera, then I use "camstream" to try to use the device but get an error -19, no such device.  I also tried Ekiga but it couldn't get a picture either.

Here's the output of a couple of these commands:

[INDENT]
**# caminfo**
CVideoDeviceInput: Warning: no channel info available.
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "Laptop Integrated Webcam"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 1600x1200
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

**# dov4l**

dov4l v0.9, (C) 2003-2006 by [email]folkert@vanheusden.com[/email]

Canonical name for this interface: Laptop Integrated Webcam
Type of interface:
 Can capture to memory

Number of radio/tv channels if appropriate: 1
Number of audio devices if appropriate: 0
Maximum capture width in pixels: 1600
Maximum capture height in pixels: 1200
Minimum capture width in pixels: 48
Minimum capture height in pixels: 32

Image size (x,y): 640, 480

VDIOCGCHAN: Invalid argument
[/INDENT]

I''d certainly appreciate any clues.

--- Thanks

---

### Post by wiresquire on 2008-01-04
I haven't really used the webcam itself, but it would show a live video of an ugly guy in Ekiga.
(Sorry, I am a newb with a webcam, so haven't got a clue about what I should be looking for. Both the commands you mentioned weren't even installed).

Ekiga detected the webcam automagically. The only thing I needed to change from the default was to tell it to use the V4L2 plugin, instead of V4L. 

I have the nvidia 100.14.23 x64 proprietary driver installed.

hth
ws

---

### Post by pt85 on 2008-01-09
Hi there.

Thought some might be interested in getting the Logitech GamePanel LCD and keys working.  I'm using Ubuntu Gutsy 32 bit (with Custom kernel - PAE).

I'm using g15tools ([http://www.g15tools.com](http://www.g15tools.com)) and in particular libg15 and g15daemon.  I'm also using lcdproc ([http://www.lcdproc.org/](http://www.lcdproc.org/)).  Only one patch is required in libg15 to recognise the device.  Patch is below.  For those interested, you also need to load the uinput kernel module (modprobe uinput or edit /etc/modules).

Once compiled and installed, run "g15dameon -s", LCDd and lcdproc.  See manual entries for more details.

Hope this helps.

pt85

*** libg15-1.2.4/libg15.c       2007-11-25 16:02:04.000000000 +1100
--- ../libg15-1.2.4/libg15.c    2008-01-09 16:46:57.000000000 +1100
***************
*** 46,51 ****
--- 46,52 ----
      DEVICE("Logitech G11",0x46d,0xc225,G15_KEYS),
      DEVICE("Logitech Z-10",0x46d,0x0a07,G15_LCD|G15_KEYS|G15_DEVICE_IS_SHARED),
      DEVICE("Logitech G15 v2",0x46d,0xc227,G15_LCD|G15_KEYS|G15_DEVICE_5BYTE_RETURN),
+     DEVICE("Logitech GamePanel LCD",0x46d,0xc251,G15_LCD|G15_KEYS),
      DEVICE(NULL,0,0,0)
  };

---

### Post by wiresquire on 2008-01-11
Hey, thanks pt85!!

I hadn't got around to that, and had no idea even where to start!
I'm looking forward to giving this a go once I get a bit of time.

Cheers
ws

---

### Post by lmacy1211 on 2008-01-24
Hi, I just got an m1730 and am trying to install the 64 bit version of 7.10. All seems to go along fine, except it wont recognize the video. But that is explained elsewhere. The I get to the line in the boot sequence "Running local boot scripts (/etc/rc.local)  [OK]" and the boot sequence just stops. Since the /etc/rc.local file is in the compressed files on the Live CD I can not tell what it is stopping on. 

Any suggestions on how to proceed?? 

I am not new to linux, but am new to Ubuntu and Live CD's. 

And I can get past this part with the i386 version, but I really need the 64 bit version to take advantage of the horse power this beast has.

Thanks

Larry

---

### Post by macabro22 on 2008-01-27
it hangs during boot for me as well! =[

---

### Post by macabro22 on 2008-01-27
Wiresquire,

How did you get past the blank screen issue??

Edit: AHA! I got past it by choosey a different tty: (ctrl + F3) and using the ENVY installer. Sweet!

---

### Post by macabro22 on 2008-01-28
> **davethelorax said:**
> I've gotten the video to work great with Ubuntu 7.10 64bit, the restricted nvidia drivers rock.  I have also installed Wine and Compiz and can spin a running Warcraft around on a projected cube of desktops (Try that with Vista), but I can't get the integrated camera to work.  I saw that one poster had gotten the integrated camera working but no details were given.  Has anyone gotten that camera working and can share the details.

Thus far, I've tried to get information on the camera using "caminfo" which says it finds the camera, then I use "camstream" to try to use the device but get an error -19, no such device.  I also tried Ekiga but it couldn't get a picture either.

Here's the output of a couple of these commands:

[INDENT]
**# caminfo**
CVideoDeviceInput: Warning: no channel info available.
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "Laptop Integrated Webcam"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 1600x1200
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

**# dov4l**

dov4l v0.9, (C) 2003-2006 by [email]folkert@vanheusden.com[/email]

Canonical name for this interface: Laptop Integrated Webcam
Type of interface:
 Can capture to memory

Number of radio/tv channels if appropriate: 1
Number of audio devices if appropriate: 0
Maximum capture width in pixels: 1600
Maximum capture height in pixels: 1200
Minimum capture width in pixels: 48
Minimum capture height in pixels: 32

Image size (x,y): 640, 480

VDIOCGCHAN: Invalid argument
[/INDENT]

I''d certainly appreciate any clues.

--- Thanks

Ekiga shows my video out of the box!

choose V4L2.

---

### Post by lmacy1211 on 2008-01-29
Macabro22,

And at what point in the boot cycle did you do that?? ctrl-f3 that is. I am not getting any further than the local.rc line in the boot cycle.

Larry

---

### Post by macabro22 on 2008-01-31
> **lmacy1211 said:**
> Macabro22,

And at what point in the boot cycle did you do that?? ctrl-f3 that is. I am not getting any further than the local.rc line in the boot cycle.

Larry

Sorry Larry, when the boot sequence locks up (I am not quite sure when that was) hit Control +alt + F3. 

This will take you to another terminal instance. Then, extract Alberto Milone's ENVY app. Install the nVIdia drivers.

Edit your /etc/X11/xorg.conf:

```
sudo gedit /etc/X11/xorg.conf
```

make it look like this:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg


#

Section "Device"
	Identifier	"nVidia0"
	Driver		"nvidia"
	Vendorname	"nVidia Corporation"
	Boardname	"GeForce 8700M GT"
	#    BusID	"PCI:3:0:0"
	Option		"NvAGP"	"0"
	Option		"SLI"	"SFR"
	Option		"UseCompositeWrapper"	"true"
	Option		"DamageEvents"	"false"
	Option		"AllowGLXWithComposite"	"true"
	Option		"NoFlip"	"True"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option "CursorShadow" "true"
	Option "CursorShadowAlpha" "64"
	#    Option	"BackingStore"	"true"
	#    Option "AddARGBGLXVisuals"	"true"
	#    Option 	"RenderAccel" 	"true"
	#    Option "XAANoOffscreenPixmaps" "true"
	#	Option "Triplebuffer" "true"
EndSection

Section "Device"
	Identifier	"nVidia1"
	Driver		"nvidia"
	Vendorname	"nVidia Corporation"
	Boardname	"GeForce 8700M GT"
	#    BusID	"PCI:4:0:0"
	#    Option	"NvAGP"		"0"file:///usr/share/ubuntu-artwork/home/index.html
	Option		"SLI"	"SFR"
	Option		"NoLogo"	"false"
	Option		"UseCompositeWrapper"	"true"
	Option		"DamageEvents"	"false"
	Option		"AllowGLXWithComposite"	"true"
	Option		"NoFlip"	"true"
	Option "CursorShadow" "true"
	Option "CursorShadowAlpha" "64"
	#    Option	"BackingStore"	"true"
	#    Option 	"RenderAccel" 	"true"
	#    Option "XAANoOffscreenPixmaps" "true"
	#	Option "Triplebuffer" "true"
	#	Option "AddARGBGLXVisuals"	"true"
EndSection

Section "Module"
	Load		"dbe"
	Load		"glx"
	Load		"extmod"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia0"
	Monitor		"LCD"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

Then you are good to go.

EDIT: I am sorry, this has nothing to do with the camera. This is how I got my video card to work.

---

### Post by macabro22 on 2008-01-31
> **wiresquire said:**
> Things seem to be running OK. Still plenty I haven't played with properly. I have been distracted a bit with eye candy of Compiz.
The webcam seems to be working via Ekiga. Well, except there's an ugly guy there all the time.... :)

One problem is that I can't get the microphone(s) to work. Eg, using Sound Recorder.

I googled a lot and have found that we have the Intel 82801H (ICH8 Family). Codec: SigmaTel9228.

I had added 
options snd-hda-intel probe_mask=1 model=3stack
to /etc/modprobe.d/alsa-base
but still seem to be getting no microphone input?

Has anyone got tips on this?

Mic is all that is left for me to fix!

I've searched the entire cyberspace for a solution for this and got nothing yet.

---

### Post by bongey on 2008-02-02
This is the how to for the XPS M1730 . I have this for x64 edition don't know about the i386 . But for those who are wondering how my set up runs, I play Wow in wine and get about 60-130 fps . 
This is a little incomplete more to come, but I did my install a while ago and don't remember all the steps, but I decided I wanted to have everything working the way it should , so I figured it out with various other guides on the web . 
1) For the initial install remove the following from the kernel boot parameters . (don't change your uuid, I just commented mine out) 
kernel          /vmlinuz-2.6.22-14-generic root=UUID=xxxxxxxxxxxxx ro  quiet splash
to 
kernel          /vmlinuz-2.6.22-14-generic root=UUIDxxxxxxxxxxxxx   ro  

Get rid of the splash in the kernel  boot parameters the default with mess it up .  The fix is a little later. 
2) Do not use the  proprietary  driver through synaptic use envy, it works much better , the latest drivers have sli enable. Notice SLI is not support with dual monitors , it isn't support in windows either. (I don't run in sli) . 
3) After you get it installed ,  I suggest using envy to install the NVIDIA driver from here. 

 [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Here is my xorg.conf (It is a dual monitor setup) 
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection



Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sharp"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Proview"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 76.0
EndSection



Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8700M GT"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8700M GT"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection


Section "Screen"

# Removed Option "TwinView" "1"
    Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    #Option         "SLI" "on"
    Option         "TwinView" "1"
    #Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

  


4) Get all the updates and the latest kernel , Make sure the nvidia driver is working correctly . ie 
     glx-info | grep rendering 
     direct rendering: Yes

5) Fix the splash screen .  
  a) Modify  sudo vim /etc/initramfs-tools/modules add the following 
     vga16b
     fbcon
     vesafb
   b) Modify sudo vim /etc/modprobe.d/blacklist-framebuffer 
       Comment out the following lines .
      #blacklist vesafb
      #blacklist vga16fb
    c) Run the following 
      sudo update-initramfs -u -k `uname -r`
    d) Add the following to the end of the kernel boot parameters . 
       kernel          /vmlinuz-2.6.22-14-generic root=UUID=xxxxxxxxxxxxxxxxxx ro  quiet splash **vga=791**
 
   e ) 

edit the /etc/usplash.conf
to
# Usplash configuration file
xres=1024
yres=768

The default is wrong and will give you the black/blank screen . 
6) Hibernate should work out of the box , but suspend fails . 
Change the following in /etc/default/acpi-support to the following 
 # Should we save and restore state using the VESA BIOS Extensions?
 SAVE_VBE_STATE=false
 
 # Should we attempt to warm-boot the video hardware on resume?
 POST_VIDEO=false
 
b) Restart acpi
sudo /etc/init.d/acpi-support restart
sudo /etc/init.d/acpid restart


7) Web cam 
sudo apt-get install  kopete 
Notice I had some issues with the color coming out black and white after a suspend  , also adjusting whiteness fails and causes kopete to crash.


8) TO COME HOW DID I FIX THE MIC , it was  a while ago . lol (have mic working in wow )
ah here it is 
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by bongey on 2008-02-02
Nothing to see here.

---

### Post by macabro22 on 2008-02-04
AHHH  the mic fix does not work for me. 

I tried to compile the latest alsa drivers 1.0.15 and Now I get no sound devices detected!

Flawed!

What do I do?

---

### Post by bongey on 2008-02-05
You shouldn't of compiled anything, the backport works, I tried compiling also and got nothing. That backport drivers is the same sound card in your xps 1730 . I will get more tonight after work. Try installing the backports from synaptic first , not compiling.

---

### Post by macabro22 on 2008-02-12
> **bongey said:**
> You shouldn't of compiled anything, the backport works, I tried compiling also and got nothing. That backport drivers is the same sound card in your xps 1730 . I will get more tonight after work. Try installing the backports from synaptic first , not compiling.

Not only that doesn't work for me, it kills all my audio.

The mixer menu icon on the gnome taskbar appears with a forbidden sign whiche gives me this message when double-clicked:

```
No volume control GStreamer plugins and/or devices found.
```

:(

EDIT: AHA! Audio playback now works after editing  sudo gedit /etc/modprobe.d/alsa-base 
and adding 
```
options snd-hda-intel probe_mask=1 model=3stack
```
unfortunately sound capture still fails:

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat

---

### Post by wiresquire on 2008-02-13
> **lmacy1211 said:**
> Hi, I just got an m1730 and am trying to install the 64 bit version of 7.10. All seems to go along fine, except it wont recognize the video. But that is explained elsewhere. The I get to the line in the boot sequence "Running local boot scripts (/etc/rc.local)  [OK]" and the boot sequence just stops. Since the /etc/rc.local file is in the compressed files on the Live CD I can not tell what it is stopping on. 

Any suggestions on how to proceed?? 

I am not new to linux, but am new to Ubuntu and Live CD's. 

And I can get past this part with the i386 version, but I really need the 64 bit version to take advantage of the horse power this beast has.

Thanks

Larry

Hey, sorry for delay in replying. I think the workarounds with updating video with a real install are well documented, but I found some quick notes I had about using the M1730 with the LiveCD.
The below relates to selecting the video card and screen resolution. Sorry it's not more detailed/step-by-step (newbies beware!), but I hope it might help in case anyone else is interested in using the AMD64 LiveCD. 

# When running LiveCD, there are problems with video resolution/drivers. The screen goes black. It will come back. Eventually. Not if you use minimal resolution, or if you adjust the
resolution.
#     Seems to work if I set to 1920 x 1200 and set both video cards to nv fbdev. Need to go to Console 1 (Ctrl-Alt-F1) and gdm restart. Then switch to Console 8 (Ctrl-Alt-F8 ). Don't get why it's not Console 7....

If only that MIC would work....  :cry:

Cheers
ws

---

### Post by bongey on 2008-02-15
Really don't use the gnome application mine gives the same error but guess what it works. Try this , go to audio properties (right click the speaker near the clock) . Make sure the sound is turned up on the Recording , go to the Options tab , there should be 3 input sources change them all to mic. Just to make sure we are on the same page, you should have four outputs for playback, one recording, two options for switches , 3 for options. Go to the Sound Preferences page and under sound capture make sure it is alsa,all the rest autodetect , and Default mixer tracks hda Intel(Alsa mixer) . 
Now turn up your volume , hit test with a mic plugged in .  Talk into the mic you should here yourself even though the dam gnome app said it failed. My mic works fine in wow and other applications , just some reason the gnome app flops, well it says failed but it works .

---

### Post by macabro22 on 2008-02-16
> **bongey said:**
> Really don't use the gnome application mine gives the same error but guess what it works. Try this , go to audio properties (right click the speaker near the clock) . Make sure the sound is turned up on the Recording , go to the Options tab , there should be 3 input sources change them all to mic. Just to make sure we are on the same page, you should have four outputs for playback, one recording, two options for switches , 3 for options. Go to the Sound Preferences page and under sound capture make sure it is alsa,all the rest autodetect , and Default mixer tracks hda Intel(Alsa mixer) . 
Now turn up your volume , hit test with a mic plugged in .  Talk into the mic you should here yourself even though the dam gnome app said it failed. My mic works fine in wow and other applications , just some reason the gnome app flops, well it says failed but it works .

Nope. Mine really doesn't work. 

Some doode in the #alsa channel at irc.freenode.net told me the mic will work if we install ALSA 1.0.16. 

I am afraid of compiling since last time I tried I lost even audio playback. I will wait till april and the release of Hardy Heron, pulseaudio and the newest ALSA drivers.

If someone has the balls, tell us the outcome.

Good Luck,

---

### Post by bongey on 2008-02-19
Are you running 7.10 or 7.04? x64 or i386? I am on x64 7.10  so that may be some of it. Just give me heads up. I am going to follow these instructions and see where it gets me [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) .  Edit I did compile and get the 1.0.16 drivers in , works fine. All I did was do the instructions on  link listed but I didn't add the --with--driver part left it out, (it compiles all the drivers that way didn't want to miss anything) .

---

### Post by cdukes on 2008-02-21
A bit off topic here but...
I'm looking at buying one of these juicy suckers and was wondering if any of you know where I can get the best deal?
Much appreciated!

---

### Post by macabro22 on 2008-02-26
> **bongey said:**
> Are you running 7.10 or 7.04? x64 or i386? I am on x64 7.10  so that may be some of it. Just give me heads up. I am going to follow these instructions and see where it gets me [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) .  Edit I did compile and get the 1.0.16 drivers in , works fine. All I did was do the instructions on  link listed but I didn't add the --with--driver part left it out, (it compiles all the drivers that way didn't want to miss anything) .

I am on x64 7.10 as well. Just for the record, whats the output of
```
lspci grep | Audio
```
?

---

### Post by macabro22 on 2008-02-26
> **cdukes said:**
> A bit off topic here but...
I'm looking at buying one of these juicy suckers and was wondering if any of you know where I can get the best deal?
Much appreciated!

[www.dell.com](www.dell.com)

---

### Post by cdukes on 2008-02-26
> **macabro22 said:**
> [www.dell.com](www.dell.com)

Thank you captain obvious...I said a "good deal" not the standard deal.
I'm pretty sure I know how to stfw.

---

### Post by VinylPusher on 2008-02-28
I have been struggling for a few hours now to get Kubuntu 7.10 installed and working on my M1730.

I have just done a clean reinstall from the Kubuntu 7.10 alternate CD (i386) followed immediately by running the Envy script.

This resulted in blank screen. LCD backlight off, unable to get to another virtual console. System still running but no display (can shutdown by hitting the power button).

I booted into a recovery console and tried 'startx'.

I got something like:
  Cannot find matching [something] at BusId 4:0:0
  Display section found but no displays have a workable config

I then opened xorg.conf in vim and noticed "DefaultDepth 16". Changed it to 32 and tried 'startx' again. No joy. This time I got the same errors with an additional "depth of 32 is not supported" which is, of course, laughable.

I restored my xorg.conf from the backup generated by the Envy script and rebooted, which is why Im now back here typing this post! :)

Before this last clean install, I did try amending my xorg.conf as advised by some previous posts in this thred, all with the same result (blank screen, LCD backlight off).

This is extremely frustrating, I have to say. I've had Kubuntu installed on this laptop for a while but I'm now trying to migrate away from Windows completely. I don't *need* eye-candy, but I *do* need the odd 15 minutes of Half Life 2.

Any suggestions that don't invlove installing the amd64 variant of Ubuntu?

**EDIT**

I have admitted defeat and installed Ubuntu 7.10 amd64. I would much rather be using KDE than Gnome but I guess I'll have to stick with it :(

---

### Post by Shootfast on 2008-03-02
Hey guys, Just thought I'd chime in on my experience with ubuntu 32bit on the XPS m1730.

I used the alternate CD and installed on the second hard drive. Once you get it installed, the graphics will run in safe mode. DON'T INSTALL THE NVIDIA DRIVERS FROM THE REPOSITORY!!!

They always seem to leave some small files behind that makes it a bitch to install the driver from the nvidia website. Don't use Envy guys, it only breaks systems. Its drop dead easy to install the nvidia driver from the website anyway.

Just download the driver, ctrl alt f2 to get to a virtual terminal, login, and type 
```
sudo /etc/init.d/gdm stop
```

Then type ```
sh NVIDIA-Linux-x86-192.xx-pkg1.run
```

And bam, all done.

If you did try the driver from the repo, you've no doubt found out that by now, no matter how many times you install the new driver, it still boots in safe mode. To fix this, just navigate to /lib/linux-restricted-modules/*2.6.xx-xx-generic*/ and remove the folders nvidia-glx-new and nvidia-legacy. You can leave the "nvidia" folder as thats the driver your trying to manually install.

Good luck guys, just remember that if you install the driver this way, you have to reinstall it each time you change kernels.

---

### Post by wiresquire on 2008-03-10
Not sure if anyone has played with SLI. I had a look at it a while ago, and wasn't too sure about whether it really did anything for me.
[LIST]
[*]glxgears reported horrible figures, which [another thread]("http://ubuntuforums.org/showthread.php?t=627804") mentioned was probably to be expected.
[*]Powermizer reported both gpus running at Max performance
[*]There seems to be some 'delay' when using Compiz, eg switching workspace etc.
[/LIST]

Anyways, I noticed a [thread over at nvnews]("http://www.nvnews.net/vbulletin/showthread.php?t=109514") and there's a guy over there that seems pretty happy with his settings. I haven't tried them yet, but thought someone here might be interested...

Cheers
ws

---

### Post by macabro22 on 2008-03-31
htorres@GLaDOS:/etc/tor$ glxgears
2238 frames in 5.0 seconds = 447.597 FPS
2225 frames in 5.0 seconds = 444.823 FPS
2218 frames in 5.0 seconds = 443.511 FPS
2252 frames in 5.0 seconds = 450.138 FPS
2181 frames in 5.0 seconds = 436.094 FPS
2203 frames in 5.0 seconds = 440.521 FPS
2257 frames in 5.0 seconds = 451.200 FPS

---

### Post by macabro22 on 2008-03-31
htorres@GLaDOS:~$ glxgears
12776 frames in 5.0 seconds = 2555.193 FPS
12551 frames in 5.0 seconds = 2503.322 FPS
12275 frames in 5.0 seconds = 2454.012 FPS
10392 frames in 5.1 seconds = 2047.711 FPS
12831 frames in 5.0 seconds = 2566.192 FPS
13381 frames in 5.0 seconds = 2675.955 FPS

---

### Post by cdukes on 2008-04-14
So it seems I'm real close.
Compiled everything and it works fine.
G15 drivers are loading properly and a clock is now displaying on the LCD panel.
However, nothing seems to happen when I load up lcdproc.
when I tail syslog, I see the following message:
```

Apr 14 20:51:08 cdukes-lnx g15daemon[6224]: Booting plugin "LCDServer"
Apr 14 20:51:08 cdukes-lnx g15daemon[6224]: Plugin "LCDServer" boot successful.
Apr 14 20:59:26 cdukes-lnx LCDd: sock_send: socket write error

```

Any idea how to fix this?


> **pt85 said:**
> Hi there.

Thought some might be interested in getting the Logitech GamePanel LCD and keys working.  I'm using Ubuntu Gutsy 32 bit (with Custom kernel - PAE).

I'm using g15tools ([http://www.g15tools.com](http://www.g15tools.com)) and in particular libg15 and g15daemon.  I'm also using lcdproc ([http://www.lcdproc.org/](http://www.lcdproc.org/)).  Only one patch is required in libg15 to recognise the device.  Patch is below.  For those interested, you also need to load the uinput kernel module (modprobe uinput or edit /etc/modules).

Once compiled and installed, run "g15dameon -s", LCDd and lcdproc.  See manual entries for more details.

Hope this helps.

pt85

*** libg15-1.2.4/libg15.c       2007-11-25 16:02:04.000000000 +1100
--- ../libg15-1.2.4/libg15.c    2008-01-09 16:46:57.000000000 +1100
***************
*** 46,51 ****
--- 46,52 ----
      DEVICE("Logitech G11",0x46d,0xc225,G15_KEYS),
      DEVICE("Logitech Z-10",0x46d,0x0a07,G15_LCD|G15_KEYS|G15_DEVICE_IS_SHARED),
      DEVICE("Logitech G15 v2",0x46d,0xc227,G15_LCD|G15_KEYS|G15_DEVICE_5BYTE_RETURN),
+     DEVICE("Logitech GamePanel LCD",0x46d,0xc251,G15_LCD|G15_KEYS),
      DEVICE(NULL,0,0,0)
  };

---

### Post by wiresquire on 2008-04-18
Maybe it's permissions ?

I still haven't played with this yet, so I haven't a clue where to start....

---

### Post by dront78 on 2008-04-29
**Dell M1730** 

internal microphone works great for me with alsa-driver-hg20080426 daily snapshot. just configured

./configure --with-cards=hda-intel
CC=gcc-4.1 make
sudo make install

remove any options snd-hda-intel from /etc/modprobe.d/alsa-base
reboot
select **Digital Input Source [Digital Mic 1]**
in Playback->Digital
also i've Input Source [Mic] in Capture

do not forget to install linux headers and other stuff
hope this will work for you too )))

---

### Post by macabro22 on 2008-05-04
Yeah, the mic now works in Hardy. =]

---

### Post by macabro22 on 2008-05-08
Good News.

I've found out that enabling SLI in AFR mode improves frame rates a lot.

I am attaching /etc/X11/xorg.conf as an example: 

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"nVidia0"
	Driver		"nvidia"
	Vendorname	"nVidia Corporation"
	Boardname	"GeForce 8700M GT"
	Option		"NvAGP"	"0"
	Option		"SLI"	"AFR"
	Option		"UseCompositeWrapper"	"true"
	Option		"DamageEvents"	"false"
	Option		"AllowGLXWithComposite"	"true"
	Option		"NoFlip"	"True"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"False"
	Option "UseEvents" "false"
	Option "RenderAccel" "true"
	Option "XAANoOffscreenPixmaps" "true"
	Option "backingstore" "true"
	Option "Triplebuffer" "true"
EndSection

Section "Device"
	Identifier	"nVidia1"
	Driver		"nvidia"
	Vendorname	"nVidia Corporation"
	Boardname	"GeForce 8700M GT"
	Option		"SLI"	"AFR"
	Option		"NoLogo"	"false"
	Option		"UseCompositeWrapper"	"true"
	Option		"DamageEvents"	"false"
	Option		"AllowGLXWithComposite"	"true"
	Option		"NoFlip"	"true"
 	Option "UseEvents" "false"
	Option "RenderAccel" "true"
	Option "XAANoOffscreenPixmaps" "true"
	Option "backingstore" "true"
	Option "Triplebuffer" "true"
EndSection

Section "Module"
	Load		"dbe"
	Load		"glx"
	Load		"extmod"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia0"
	Monitor		"LCD"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
``` 

Here's the updated output to glxgears:

```
htorres@GLaDOS:~$ glxgears
13705 frames in 5.0 seconds = 2740.877 FPS
15482 frames in 5.0 seconds = 3096.049 FPS
15527 frames in 5.0 seconds = 3105.273 FPS
14119 frames in 5.0 seconds = 2823.753 FPS
14065 frames in 5.0 seconds = 2812.468 FPS
15230 frames in 5.0 seconds = 3045.897 FPS


```

---

### Post by nossifer on 2008-05-15
works out of box with Hardy.  only slight trick is to select Digital Mic in the sound settings.  (for noobs:  go into preferences and enable stuff in the checkboxes)

mic quality was very, very good for just the built in mic.  cant wait to use an external one.

tuning my guitar will finally be easy!

---

### Post by bongey on 2008-05-24
I am running hardy x64 with the nvidia beta 173 drivers(sorry envy broke me this time). I don't know what everyone is doing to there machine but here is my frame rates for glxgears. These rates are actually disappointing I used to get around 120000 with ubuntu 7.04.  no sli, enabled. I just did a reinstall to enable full disk encryption. 
42827 frames in 5.0 seconds = 8565.261 FPS
44810 frames in 5.0 seconds = 8957.638 FPS
38369 frames in 5.0 seconds = 7673.800 FPS
44707 frames in 5.0 seconds = 8938.868 FPS
44363 frames in 5.0 seconds = 8872.584 FPS

---

### Post by macabro22 on 2008-06-20
Impressive. I am getting only ~1200 fps now

---

### Post by soulsedition on 2008-06-24
Hello everyone! This is my first time posting and i didn't see an introductions thread anywhere. I'm new to Linux and Ubuntu, currently in iraq with some spare time on my hands so i thought i would install it. It installed rather well on my dell xps 1730, however when i try to use compiz it slows down quite a bit. I got the nvidia drivers from the repository, i believe 169. Anyways, does anyone with this computer have some input for me? i've got the t7700 processor with dual 8700m SLI and am running hardy in dual boot with xp. Please try to break it down for me, as i'm rather new to linux. I appreciate any responses!

SGT Skaggs

---

### Post by soulsedition on 2008-06-25
Bump

---

### Post by wiresquire on 2008-07-08
Sgt Skaggs

What exactly is slow? The graphics performance? A particular game? Moving a window? etc.
The reason I ask is that is because there are a number of posts at the nvidia forums about specific situations that cause bad performance, eg websites with background images have atrocious performance in firefox 3.

Also, what version of ubuntu are you using (eg 8.04?)? Which architecture? AMD64 or 32 bit?

The performance I get off my machine is quite OK for what I use it for :-D

a) Check you really have the nvidia driver installed properly:
in a terminal, after you have logged in 
 > glxinfo
Up the top, you should see
Direct rendering: Yes
server glx vendor string: NVIDIA Corporation

b)  What is the fps you get when you run glxgears in a terminal window?
(glxgears is not a benchmark, but can highlight when things aren't what they should be...

c) Compiz settings: Based on my tests, make sure that you DO NOT have the sync to vblank enabled in the Advanced Desktop Settings Effect. It's OK to do it in the nvidia driver settings, but I went from glxgears 6500fps to 5500fps when I enabled it in Compiz. (Yes, I know it's not a benchmark!)

d) Do not enable SLI unless you're interested in seeing if it helps for games. For normal desktop use, it appears to create an initial 'pause', and (more importantly to me) does not allow Powermizer, so you would probably lose battery life. If you haven't enabled SLI manually, don't worry about this, by default, only 1 gpu will be used.

hth
ws

PS: I have recently done a fresh install to 8.04 AMD64 on my machine. Biggest win was the Mic now works! I used Envy to install 173.14.05, and noticed a decrease in glxgears the same as bongey (though I guess he has the 8800!). glxgears now reports ~ 6500 fps vs the 7500 fps I used to get using 169.x on 7.10. Single 8700, no SLI. Yes, I know that it's not a benchmark...

---

### Post by soulsedition on 2008-07-08
Hey Wiresquire, thanks for the reply. The good news is that i've got ubuntu up and running on the laptop. (BTW it's 8.04 AMD64) I was having a problem with that initial pause that everyone has been talking about. Got it fixed, though. However, performance still doesn't seem to be up to par, i'm getting ~2600 FPS in GLXGEARS and my mic still isn't working..

---

### Post by wiresquire on 2008-07-10
I think I can help with the mic. 
- Open the Volume Control. On the top right 'applet' panel, right click the Speaker and select Open Volume Control.
- Once opened, from the menu select Edit/Preferences
- Starting about half way down, make sure that Capture, Capture 1, Capture 2, Digital, Digital Input Source, Digital, Digital, Digital are checked. Hit Close.
- This will add some new options to the tabs. Select the Options tab. Make sure that Digital Input Source is set to Digital Mic 1.
- On the recording tab, make sure that the the volume levels are enabled and are maximum for Capture and Digital. You can leave Capture 1 and Capture 2 disabled.

Close the volume control, and do a test using the Sound Recorder (under the main Ubuntu Applications/Sound & Video menu). Leave the settings as Record from input: Master. Record something, and then play it back. The quality is quite good.

Re the low fps on your graphics card, that has me beat. Maybe posting a request for help at the [nvidia linux forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14) would be your best bet.

hth
ws

---

### Post by macabro22 on 2008-07-17
You think yours is bad?

```
 glxgears
5512 frames in 5.1 seconds = 1079.092 FPS
4481 frames in 5.0 seconds = 894.231 FP
```S

---

### Post by soulsedition on 2008-07-18
That sucks, Mac.

Wiresquire- I tried the mic fix and i ended up borking my audio settings, losing us of the front buttons to control sound, much to my room-mates dismay. It magically fixed itself, somehow.

---

