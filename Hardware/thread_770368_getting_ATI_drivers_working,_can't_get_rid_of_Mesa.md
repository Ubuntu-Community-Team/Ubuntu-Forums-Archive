---
title: "getting ATI drivers working, can't get rid of Mesa"
date: 2008-04-27
forum: Hardware
---

### Post by gerben1 on 2008-04-27
I just don't seem able to get the ATI proprietary drivers installed. I have tried this tutorial: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

and I followed it closely, and have tried multiple times, but it just won't work I keep getting this:

gerben@CC1184274-A:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

I also tried using envyNG but it gave me exactly the same result.
(even though it did recognize my card, and said it was supported by the driver)

I had to fix a libGL error as explained in:
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)
but all I had to do for that was make a link like this:
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

That is all fine, but having to correct links like that makes me feel a bit nervous about the intergity of my system, especially if things can go wrong such important(i assume) video drivers/libraries (thoughts like, "there probably all kind of link pointing to wrong files" etc.).


Anyways I had this working perfectly fine in Gutsy, so it must be possible to get it working again. Does anybody have some suggestions for things to check?

---

### Post by chek2fire on 2008-04-27
what card you have?

---

### Post by gerben1 on 2008-04-27
ATI Mobility Radeon X700

---

### Post by gerben1 on 2008-04-27
Oh common, does nobody know anything about this?

This looks like a very basic issue to me, somebody must be able to point me in the right direction?? I can go on googling for more different howto's/tutorials, but they all do bassically the same thing, sometimes the order is a bit different or they use a different text editor to edit xorg.conf but that can't make much of a difference I assume.

There is no way I can solve this myself, as the normal way of doing this does not work in my case. I really need someone with knowledge of the operating system to help me a bit in order get any further.

---

### Post by again617 on 2008-04-27
It sounds like I'm having the same problem that you're having.  I've followed so many tutorials and made so many changes to config files that I have nearly gone crazy.  I have also gotten quite proficient at using Linux in the process.

No matter what I do, I can't seem to get the proprietary driver to show up in the restricted drivers list.  So right now I'm thinking that the problem might be that I can't enable it, but I'm not convinced that this is the problem.  It could also be the segmentation faults I get when running fglrxinfo.  But that could be just me.

If anyone has some ideas as to what the problem is then I would love to hear them.

My computer:
IBM Thnkpad T41
ATI Radeon 7500

---

### Post by hoobadoo on 2008-04-27
I'm also having the same problem, and whenever I boot it just goes to a white screen. I'm using a Radeon 9800 pro

---

### Post by ratazana80 on 2008-04-27
Same problem here!

I have an Asus A6VA (A6Q00VA), with an ATI Mobility Radeon X700.

display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

---

### Post by darkelvenangel on 2008-04-28
I'm also having the very same problem and had no such problem before my update to 8.04.  It would seem like it should be a simple fix but I'm not familiar enough with Ubuntu's configuration files to sort out where the problem is.

I'm using an ATI X1900 AIW.

---

### Post by pinkelmer on 2008-04-28
Same issue here with an ATI Mobility Radeon 9600 using fglrx :

display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

---

### Post by again617 on 2008-04-28
If I have the Driver labeled as fglrx in my xorg.conf file than Ubuntu creates and uses an xorg.conf.failsafe file.  Perhaps that is a clue?

---

### Post by darkelvenangel on 2008-04-28
> **again617 said:**
> If I have the Driver labeled as fglrx in my xorg.conf file than Ubuntu creates and uses an xorg.conf.failsafe file.  Perhaps that is a clue?

I don't think the problem is in the xorg.conf my time with GENTOO leads me to think the problem is else where.  I just don't know if Ubuntu has a command similar to the eselect opengl that you use in gentoo to setup the what renderer to use.

---

### Post by mesilikas on 2008-04-28
> **again617 said:**
> It sounds like I'm having the same problem that you're having.  I've followed so many tutorials and made so many changes to config files that I have nearly gone crazy.  I have also gotten quite proficient at using Linux in the process.

No matter what I do, I can't seem to get the proprietary driver to show up in the restricted drivers list.  So right now I'm thinking that the problem might be that I can't enable it, but I'm not convinced that this is the problem.  It could also be the segmentation faults I get when running fglrxinfo.  But that could be just me.

If anyone has some ideas as to what the problem is then I would love to hear them.

My computer:
IBM Thnkpad T41
ATI Radeon 7500

Have also I the same problem with you in Laptop IBM T42 with card ATI Radeon 7500 and I have tryed many drivers without result with the previous publication Ubuntu (7.10) I did not have such problems I hope in certain radical update our solution this problems!

---

### Post by ratazana80 on 2008-04-28
Well, I've found a way to make it work.

Were's how I've done it:

I did a Ubuntu 8.04 fresh install, and then used the "Add and Remove" under "Applications" and selected a package named: "ATI binary X.Org driver" and installed it. After doing so, I've selected "System / Administration / Hardware Drivers" and enabled the "Ati accelerated graphics driver" and rebooted the machine. And this was the output of # fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.1.7412 Release

---

### Post by darkelvenangel on 2008-04-28
Is there no way to fix this with out reinstalling?  I don't really want to download and burn a new disk if I don't have to.

Glad to see that it is possible to have it work though, BTW does you compiz work properly now?

---

### Post by ratazana80 on 2008-04-29
> **darkelvenangel said:**
> Is there no way to fix this with out reinstalling?  I don't really want to download and burn a new disk if I don't have to.

Glad to see that it is possible to have it work though, BTW does you compiz work properly now?
Hi, yes darkelvenangel, my compiz is working fine. I'm only having issues with some aplications and games. Blender behaves strangly if I try to run it with the compiz effects enabled and games which require acceleration tend to flicker. Besides these...my Ati X700 is running ok.

---

### Post by ThinkDave on 2008-04-29
Im so sick of Ati I've got the same problem here shame its integrated on my laptop otherwise i would swapped it out for nvidia in a heartbeat... i thought the AMD takeover would help the linux drivers but they seem to be getting worse.

---

### Post by darkelvenangel on 2008-04-30
I FIXED IT!!

The problem for me at least.  Okay so You can't get the renderer to switch why?  My system was still using the old Gusty Kernel and not The new one.

The FIX
[LIST=1]
[*]Completly uninstall the fglrx drives
[*]Then install them again
[*]Install the "Linux-restriced-modules" FOR 2.6.24.16.18 KERNEL
[*]Edit your GRUB.CONF
[*]Reboot
[/LIST]
```

Grub.conf Excerpt
title Ubuntu
    root (hd1,5)
    kernel /vmlinuz-2.6.22-14-generic root=/dev/sda7 ro splash quiet vga=792
    initrd /initrd.img-2.6.22-14-generic
    quiet
title Ubuntu FIXED
root (hd1,5)
    kernel /vmlinuz-2.6.24-16-generic root=/dev/sda7 ro splash quiet vga=792
    initrd /initrd.img-2.6.24-16-generic
    quiet

```
I don't know if this will solve your problems but it certainly wasn't ATI fault that my system wasn't configured properly.  I now have compiz working great and everything seems good to go on the video end.

BTW it is important to note that if you tried any of these other fixes that you will need to unrestrict the fglrx module and use the Proprietary drivers manager.

oh yes the proof
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 1.4 (2.1.7412 Release)

```

---

### Post by hoobadoo on 2008-05-01
Is there anyway to fix the flickering in games once you get the drivers to work?

---

### Post by darkelvenangel on 2008-05-01
> **hoobadoo said:**
> Is there anyway to fix the flickering in games once you get the drivers to work?

What games are you running?  I haven't had any flicker problems yet.

---

### Post by hoobadoo on 2008-05-01
Any 3D game I have tried so far(OpenArena, Neverball, Billard-GL) they all have this little black flickering.

---

### Post by degenerate1991 on 2008-05-01
Ugh. ATI. Their driver (according to their website) doesn't even support my card. (X1950GT, hardly bleeding edge) Thank goodness I have a ubuntu laptop so I can actually get my work done. (curse office 07, my teachers are starting to use it) My windows machine is suffering from numerous issues. (bluescreens and data execution prevention klling explorer.exe) But hey, we can always hope for the future and I will always check the new catalyst drivers and am lanning to try again with 8.04.

---

### Post by darkelvenangel on 2008-05-02
> **hoobadoo said:**
> Any 3D game I have tried so far(OpenArena, Neverball, Billard-GL) they all have this little black flickering.

Well I have the same flicker now that I've tried out the 3d Games as well.

Looking at your xorg.conf I can suggest some adjustments.

[CENTER]**_/!\_ MAKE BACKUPS BEFORE YOU TRY THIS _/!\_**[/CENTER]
I also suggest that you know how to use command line file copying and an editor like nano
Add the following lines to your xorg.conf's Section "Device"
```
	Identifier	"Configured Video Device"
	Driver		"fglrx"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "off"	# [on|off]
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "on"	# [on|off]
####################################################
	Option      "DRI" "true"
	Option      "XAANoOffscreenPixmaps" "true"
```
By adding the above lines I was able to take my frame rate form ~76FPS to 400+FPS I have a lot of compiz running and this speed is reported by the benchmark plug-in.
[CENTER]
**_/!\_ MAKE BACKUPS BEFORE YOU TRY TO USE ANY OF THESE _/!\_**[/CENTER]
Here's a list of all the options you can set
```
# ### generic DRI settings ###
# === disable PnP Monitor  ===
#    Option                              "NoDDC"
# === disable/enable XAA/DRI ===
#    Option "no_accel"                   "no"
#    Option "no_dri"                     "no"
# === misc DRI settings ===
#    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
#   Option "DesktopSetup"               "horizontal"
#   Option "ScreenOverlap"              "0"
#   Option "GammaCorrectionI"           "0x00000000"
#   Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
#    Option "Capabilities"               "0x00000000"
#    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "off"	# [on|off]
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"	# [on|off]
# === Center Mode (Laptops only) ===
#    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
#    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
#    Option "Stereo"                     "off"
#    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
#    Option "FSAAEnable"                 "no"
#    Option "FSAAScale"                  "1"
#    Option "FSAADisableGamma"           "no"
#    Option "FSAACustomizeMSPos"         "no"
#    Option "FSAAMSPosX0"                "0.000000"
#    Option "FSAAMSPosY0"                "0.000000"
#    Option "FSAAMSPosX1"                "0.000000"
#    Option "FSAAMSPosY1"                "0.000000"
#    Option "FSAAMSPosX2"                "0.000000"
#    Option "FSAAMSPosY2"                "0.000000"
#    Option "FSAAMSPosX3"                "0.000000"
#    Option "FSAAMSPosY3"                "0.000000"
#    Option "FSAAMSPosX4"                "0.000000"
#    Option "FSAAMSPosY4"                "0.000000"
#    Option "FSAAMSPosX5"                "0.000000"
#    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
#    Option "UseFastTLS"                 "2"	# [0,1,2]
#    Option "BlockSignalsOnLock"         "off"	# [on|off]
#    Option "UseInternalAGPGART"         "no"	# [yes|no]
#    Option "ForceGenericCPU"            "no"
#	Option      "VideoOverlay" "off"
#	Option	    "UseFastTLS" "2"
#	Option      "EnablePrivateBackZ" "on"
```
[CENTER]**_/!\_ USING THESE CHANGES CAN BREAK XORG _/!\_**[/CENTER]

---

### Post by jocko on 2008-05-02
> **again617 said:**
> If anyone has some ideas as to what the problem is then I would love to hear them.

My computer:
IBM Thnkpad T41
ATI Radeon 7500

Your problem is that you are trying to install drivers that does not support your card.
ATI dropped support for that card a long time ago (if they ever did support it... the oldest drivers they list on their download page did not support anything older than 8500 and those drivers will not work on a current version of xorg).
But the open source driver should work.

---

### Post by hoobadoo on 2008-05-02
Well I added what you suggested but I still have flickering lines going across the screen :(

Anyone else have any suggestions?

---

### Post by darkelvenangel on 2008-05-02
the changes didn't solve the flicker problem for me either but it did speed up my fps.

You have to experiment with the setting to see what works best for you.
just be sure to make one change at a time so if something goes wrong you can fix it.

sadly I don't have the time to tinker with the setting right now

---

### Post by hoobadoo on 2008-05-02
Yea, the only problem is I have no idea what to change each thing to or what it will affect.

---

### Post by darkelvenangel on 2008-05-02
Turn compiz off and no more flicker.

---

### Post by hoobadoo on 2008-05-02
Wow...that worked! yay!

---

### Post by hoobadoo on 2008-05-03
You have any suggestions to increase my fps a little bit?

---

### Post by darkelvenangel on 2008-05-03
What's you current FPS?

You can use Compiz Benchmark plugin if you have it or glxgears.

I'm not sure what you should expect from you card.  I've got glxgears results of
21190 frames in 5.0 seconds = 4236.590 FPS
22028 frames in 5.0 seconds = 4404.414 FPS
21804 frames in 5.0 seconds = 4360.702 FPS
but this is unrealistic the Compiz benchmarks at approx 450 FPS.

Lets see what you have and I can suggest something  I'm assuming that your configuration hasn't changed?

---

### Post by hoobadoo on 2008-05-04
Using glxgears im getting:
1622 frames in 5.0 seconds = 322.667 FPS
1620 frames in 5.0 seconds = 322.168 FPS
1620 frames in 5.0 seconds = 323.535 FPS

I'm just wondering if I can boost the fps a bit...even on some not graphically intensive games im only getting 20-30 fps.

---

### Post by darkelvenangel on 2008-05-09
I've been looking into how to boost the FPS and there seems to be many Idea's and all the ones I've tried only boost preformance by a small fraction.

This is a hybrid of all the forums and wiki's I've read and my only problem is with compiz on any OpenGl app flicks including screen savers.

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "off"	# [on|off]
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"	# [on|off]
####################################################
	Option      "DRI" "true"
	Option      "XAANoOffscreenPixmaps" "true"
	Option      "TexturedVideo" "On"
       ### Set to 1 - better , set to 2 for compability, and 0 for basic
       Option      "UseFastTLS" "1"
       ### Experimental 
       Option      "Textured2D" "on"
       Option      "TexturedXRender" "on"
	Option      "BackingStore" "on"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
	Load	"dri"
EndSection
Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option  "Composite" "enable"
	####
	Option      "RENDER" "On"
	Option      "XVideo" "On"

EndSection

Section "ServerFlags"
        Option  "AIGLX" "on"
EndSection
```

I hope this helps give you some more FPS I really don't know the limits of your hardware.

---

### Post by Perwin on 2008-06-30
> **darkelvenangel said:**
> I FIXED IT!!

The problem for me at least.  Okay so You can't get the renderer to switch why?  My system was still using the old Gusty Kernel and not The new one.

The FIX
[LIST=1]
[*]Completly uninstall the fglrx drives
[*]Then install them again
[*]Install the "Linux-restriced-modules" FOR 2.6.24.16.18 KERNEL
[*]Edit your GRUB.CONF
[*]Reboot
[/LIST]
```

Grub.conf Excerpt
title Ubuntu
    root (hd1,5)
    kernel /vmlinuz-2.6.22-14-generic root=/dev/sda7 ro splash quiet vga=792
    initrd /initrd.img-2.6.22-14-generic
    quiet
title Ubuntu FIXED
root (hd1,5)
    kernel /vmlinuz-2.6.24-16-generic root=/dev/sda7 ro splash quiet vga=792
    initrd /initrd.img-2.6.24-16-generic
    quiet

```


If I may ask, what are the exact commands you used for each step?  What does your /etc/X11/xorg.conf file look like now?

My current situation is:
I am on a IBM T42 laptop, 1 GB memory, a ATI Radeon Mobile 7500 video card.  I am looking to get compiz running and so far no luck. The best I have is now enabling compiz I get a big white nothing.. The windows are there but I just see white.

I get the same Mesa error as this thread indicates. I have tried several fixes found on the net. Nothing so far. I just switched to Ubuntu for it's "Ease of Use". Unfortunately I am not used to it's commands or file placements.

 Any direct guides available from someone with the exact same hardware?

---

### Post by stchman on 2008-06-30
Has anyone just tried installing the proprietary driver via the command line?

```
sudo apt-get install xorg-driver-fglrx
```

The package says it supports the X700 under Hardy.

[http://packages.ubuntu.com/hardy/xorg-driver-fglrx](http://packages.ubuntu.com/hardy/xorg-driver-fglrx)

---

### Post by paulg on 2008-07-03
> **Perwin said:**
> 
My current situation is:
I am on a IBM T42 laptop, 1 GB memory, a ATI Radeon Mobile 7500 video card.  I am looking to get compiz running and so far no luck. The best I have is now enabling compiz I get a big white nothing.. The windows are there but I just see white.


As stated to someone else in the thread, try using the open source drivers. To do this you need to edit your xorg.conf file. (gksudo gedit /etc/X11/xorg.conf)

Change the driver line from "fglrx" to "ati" (I assume you are trying to use this driver since that was this thread was initially about loading the restricted driver). There may be other options you need to turn off, I just don't know the hardware, but this should in general, be the fix for your problem. You are using mesa as it is a generic fall back vga driver when the default driver fails to load - since it can't load because it doesn't support your card. The open source driver support for the 7500 should be fairly good and should include 3D support so you may still be able to use compiz.

---

### Post by Perwin on 2008-07-08
> **paulg said:**
> As stated to someone else in the thread, try using the open source drivers. To do this you need to edit your xorg.conf file. (gksudo gedit /etc/X11/xorg.conf)

Change the driver line from "fglrx" to "ati" (I assume you are trying to use this driver since that was this thread was initially about loading the restricted driver). There may be other options you need to turn off, I just don't know the hardware, but this should in general, be the fix for your problem. You are using mesa as it is a generic fall back vga driver when the default driver fails to load - since it can't load because it doesn't support your card. The open source driver support for the 7500 should be fairly good and should include 3D support so you may still be able to use compiz.

paulg , thank you.  I am now able to run Compiz on my IBM T42.
I am using the new Ubuntu 8.0.4 Hardy heron kernel version is 2.6.24-19-generic
with a ATI video card found with `lspci | grep ATI`

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

Just to post ,  I tried several driver installs from other forum posts with no results, White screens would be the best I would get.

 With most of the posts in this thread and Paulg's assistance it works, though at times the window manager seems to lock up from time to time if I switch from compiz to metacity often.

So even though I asked for it, I tried a few steps and am not sure what exactly the combination was to get it fully working however. I did install the Envy package but it did not seem to help me.

first let me point out I found this in the forums
`dpkg --get-selections > installed-software`, this creates the list of packages installed in my system.

`grep envy installed-software`
 output:
envyng-core					install
envyng-gtk					install
envyng-qt					install
fglrx-kernel-source-envy			install
xorg-driver-fglrx-envy				deinstall

these are the drivers I found installed.
`grep driver installed-software`
cupsddk-drivers					install
cupsys-driver-gutenprint			install
xorg-driver-fglrx				install
xorg-driver-fglrx-envy				deinstall


And of course Paulg's help, here is my /etc/X11/xorg.conf

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon (vesa)"
	Busid		"PCI:1:0:0"
#	Driver		"vesa"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"v4l"
	Load		"glx"
	Load		"dri"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (vesa)"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
	Vendorname	"ATI"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "Extensions"
        Option  "Composite" "enable"
	####
	Option      "RENDER" "On"
	Option      "XVideo" "On"

EndSection

Section "ServerFlags"
	Option	"AIGLX"	"on"
EndSection

---

### Post by catonthewebbb on 2009-10-26
hi dont know if the right person will get this but if you are the right person you will know what i mean when i say you have an angel ***.If its not you then no offence,just trying to locate someone

---

