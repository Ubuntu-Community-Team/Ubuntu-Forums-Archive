---
title: "Increasing screen resolution"
date: 2009-11-05
forum: Hardware
---

### Post by ranc1d on 2009-11-05
Hi,

I have just installed Ubuntu 9.10 on a PC with a Nvidia graphics card (unfortunately I do not know the model of the card - I "inherited" this PC).

The installation was a success but the maximum screen resolution is 800 x 600 and I'm not able to increase it further.

I'm suspecting that the card hasn't been detected or the relevant driver is not installed.

Is there any way of increasing the resolution? 
How should I go about installing the driver? 
Also, as I do not know the model of the Nvidia card, is there a "general" one that I can use? 

Apologies if my questions sound stupid as I'm a newbie in this.

Thanks in advance.

---

### Post by realzippy on 2009-11-05
To install nvidia-driver:

System/administration/restricted drivers

---

### Post by ranc1d on 2009-11-05
Hi realzippy,

Thanks for the reply.

I'm not able to find that option in 9.10.  

Do I need to activate anything ?

---

### Post by realzippy on 2009-11-05
so maybe its an old nvidia card.You should know the model to get a driver.Open a terminal,type:
[B]sudo apt-get install sysinfo
[/B]
After sysinfo installed,type **sysinfo** to start the app.

---

### Post by ranc1d on 2009-11-05
Hi realzippy,

Thanks for the help ! 

I can now see the card model. It's :

nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev15)
Subsystem : nVidia Corporation Device 0006

So I guess the next step is to download the relevant driver, right?

Would you also be so kind as to provide the steps as to how I can install the driver once I've downloaded it?

Thanks !

---

### Post by ranc1d on 2009-11-05
ok.. some updates...

1) managed to download NVIDIA-Linux-x86-71.86.11-pkg1.run
2) successfully installed the above 

But when I go to System->Preferences->Display, I get the popup :

It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's too instead?

Clicking 'Yes' will bring up the 'NVIDIA X Server Settings' with some options checked. The left side of this popup has the title 'nividia-settings Configuration' but that's it.

Clicking 'No' will bring me to the 'Display Preferences' popup whereby the maximum screen resolution is still 800 x 600 (which was what I was trying to increase in the first place).

I have checked the /etc/X11/xorg.conf file and there's nothing inside.

What else do I have to do?  

Thanks

---

### Post by njsharp on 2009-11-06
ranc1d, you and I seem to be at precisely the same point.  The GUI brought up by YES is a tiny fraction of what I was expecting from experience of modern NVIDIA card linux drivers:

eg  [http://www.flickr.com/photos/tarotoast/1461847980/](http://www.flickr.com/photos/tarotoast/1461847980/)

Incidentally, you can also launch it at Applications/System tools/NVIDIA X Server Settings though you may need first to right click on Applications/Edit Menus, then click on System Tools then tick the NVIDIA box.  It's the same as what you have seen already, but IF we get this doing ALL the things it should, the above is a quicker way to the NVIDIA GUI.

Hard work this bit.

---

### Post by njsharp on 2009-11-06
Oh, and also, try this in a root terminal:

root@u910i386:/home/nick# nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


The (nearly useless) GUI comes up, but note the error message.

---

### Post by njsharp on 2009-11-06
New research: AFAIK, nvidia-glx-71 DID still exist in 9.04 but has been dropped in 9.10 and I think on one web page I saw it has been "obsoleted by nvidia-glx-96".  But surely, it hasn't?!  There is no support for RIVA TNT in '96 is there?

So I am reinstalling 9.04 and plan to download nvidia-glx-71 on that.  My previous build on the PC in question was 9.04 but on a voodoo card, so I have no previous experience with the TNT on that.

Watch this space!

If it all works fully, then we should call for '71 to be put back in 9.10 I think?

---

### Post by ranc1d on 2009-11-10
Hi njsharp,

Thanks for your reply.

More updates of what I've done.

1) reinstalled using 9.04 (trashed 9.10)
2) installed NVIDIA-Linux-x86-71.86.11-pkg1.run successfully
3) installed Envyng

From Envyng, I can see that the "NVIDIA 71.86.08-0ubuntu1" is ticked so I guess this is the driver that's currently in use. However, I do see the following also but they are not "Compatible" and "Recommended" :
- 180.44-0ubuntu1
- 173.14.16-0ubuntu1
- 96.43.10-0ubuntu1

Going to System -> Preferences -> Display, I'm still seeing the maximum resolution as 800 x 600.

I tried enabling the "71.86.08" version in Envyng, and after rebooting, the system couldn't even start complaining of graphics incompatibility and had to use the default configuration to continue the boot up.

I think there's compatibility issues or the card is not supported.

It's hard getting the graphics card to work.

---

### Post by njsharp on 2009-11-10
Sorry to report that I've reached the "give up" point.  As I salvage bits from old desktop PCs, I have several old video cards.  I've tried 9.04 and 9.10 with Voodoo3 3dfx, NVIDIA RIVA TNT2, NVIDIA GeForce2 MX 100/200, and the motherboard S3 ProSavage8 chip.  Everything works in part, but they all are flawed in some way.  I get instant total freezes, automatic reboots of the X server, etc etc etc.

The PC itself is not, on paper, too bad: 2x512MB DRAM, 1.7GHz P4, and it has multipassed Memtest86+.  But it doesn't owe me anything - it was all free as in $$s!

Warning: some of the below might be in error; I confess I did not take notes!

I never got the TNT2 NVIDIA drivers to run properly.  It is easier with 9.04 because that card does seem to need the 71 package, which seemingly has been dropped from the 9.10 distro - 96 does NOT support that card.  Using 9.10 and the NVIDIA site driver, I got:

ERROR: NV-CONTROL extension not found on this Display

and so just the single "nvidia-settings Configuration" option on the left of their tool.

Using 9.10 and the GeForce2 card, and therefore the 96 package I got the whole nvidia tool options, and DID correctly discover the monitor, and DID offer more than 1024x786 resolution, but using the tool to set eg 1280x1024x60Hz usually froze everything.

So, sadly, I've run out of patience, incentive, and lack the skills and knowledge to take this any further, and am somewhat wary of U9.10 now anyway.  There have been mumblings in the press that it might be sensible to wait a month or so until enough fixes have hit the repository to make it as solid as 9.04 now seems to be.  I have used 9.04 since it was released and have had almost no issues with it at all.

Good luck with your attempts though!

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
I had to come up with a workaround to get my geforce 4 to go above 800x600 in jaunty or karmic.
[This]("http://ubuntuforums.org/showthread.php?t=1320785") describes my plight.
BTW, I had to get this all working before I could enable the proprietary driver. Before generating a proper xorg.conf I was limited to 640x480 with the proprietary driver and "auto-detect"

---

### Post by ranc1d on 2009-11-10
Hi ST3ALTHPSYCH0,

Thanks for your reply.

Like njsharp, I'm just about to give up. It's so hard and frustrating to get it to work.

Anyway, I've read the link to your post and on running "gksudo nautilus", I'm getting the 
following errors :

Initializing nautilus-gdu extension

** (nautilus:1664): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1664): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1664): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> inode/directory
--> root
--> l2049
Shutting down nautilus-gdu extension

(nautilus:1664): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:1664): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 4 elements at quit time

I'm not able to proceed as the xorg.conf wasn't even created.

---

### Post by darkshadow on 2009-11-10
To install properly it is
System > Administration > "Hardware Drivers"

It was renamed from restricted drivers but most people instinctively write the old name.

---

### Post by ST3ALTHPSYCH0 on 2009-11-11
That was in an attempt to not have to guess where you put the file.
Try this. Run  Screens and Graphics from the 8.04 Live CD. Copy the xorg.conf from the /etc/X11/ directory on the live CD and put it anywhere on your harddrive.
Reboot (w/ no live CD) and move the xorg.conf to your desktop.
Open a terminal
```

cd Desktop

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.works

sudo mv xorg.conf /etc/X11/xorg.conf

```

Reboot

Someone may come across this who can help you manually configure an xorg.conf, but this is the only way I was able to generate a working example.
Good luck!

---

### Post by ranc1d on 2009-11-11
Ok managed to generate the xorg.conf using "sudo X -configure".

Here's how it looks like :

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "dri"
	Load  "glx"
	Load  "dbe"
	Load  "record"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	BusID       "PCI:1:8:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card1"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82865G Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Now, how should I start adding the resolution parts to it? 

If configuring xorg.conf works (that's a BIG IF), does it mean that I no longer need to go to System -> Preferences -> Display to change the resolution as I can never see anything more than 800x600 there?

---

### Post by ST3ALTHPSYCH0 on 2009-11-11
If you can get a proper xorg.conf generated, you will still use that dialog, but it will have more options.... that is, unless you're using proprietary drivers. Then, you would use the vendor's config tool (for nvidia it's System>administration> Nvidia x server settings).

Alright, to generate from that xorg, you will need to run this command in terminal:
```

cvt x y z

```where x= horizontal resolution
y=vertical resolution
and z=refresh rate (e.g. 1280 1024 60 would be 1280x1024 at 60 Hz refresh)

This will generate a modeline which you need to cut and paste in the monitor section under model name.
For example:
```

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"

Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync


EndSection



```Next you will need to delete all but one subsection under screen. In the remaining subsection change depth to the color depth you want. Delete the viewport line. add a line that says modes and add all the mode you added above.
for example:
```

modes                "1280x1024@60" "1024x768@60"

```You only need one monitor and one scrren section unless you're running dual monitors.

Backup your xorg.conf before attempting anything.

DISCLAIMER:
I used the tool from the 8.04 live CD to generate my xorg.conf file. I am trying to use that file (that works on my machine) to get your file to the point that you can get the resolutions you want. However, I was not successful in generating a working example myself, only minor editing to my working example. Be prepared that this solution I just offered may not work.

BTW, The source of your errors with "gksudo nautilus" stems from the fact that it needs to be run from the run dialog, not terminal.
Good luck.

[Here's](http://ubuntuforums.org/showthread.php?t=1322278&page=2) some pointers from someone who does know how to properly edit xorg.conf.

---

### Post by ranc1d on 2009-11-12
Hi ST3ALTHPSYCH0,

Just tried out your suggestion and didn't work. I expected it.

Thanks for your effort !  It's greatly appreciated !

At least now I know more about the xorg config file.

I'm surrendering on this issue.

Cheers !

---

### Post by Mariane on 2009-11-12
I have had the same problem with a more recent nvidia card (geforce 8700). Here is the link, you might find some of the advice I was given useful to you. It ended with partial success, I'm running kde through gdm,  the icon text is on top of the icons on the desktop and not underneath it and the screen saver does not work. But the computer is at least usable which was hardly the case with 600x800 resolution. 

Also, you seem to know more than I do, so if I was able to sort out the problem following this advice you can do it too. 

[http://ubuntuforums.org/showthread.php?t=1323019&page=2](http://ubuntuforums.org/showthread.php?t=1323019&page=2)

Mariane

---

### Post by ST3ALTHPSYCH0 on 2009-11-12
I also have to say that I had to revert to the generic drivers to get stuff working and then put the proprietary driver back on top of the working generic configuration.

---

### Post by njsharp on 2009-11-15
Whilst I did give up on an earlier machine and video card, I'm pleased to report some success with old NVIDIA gear at last.

At the weekend, I got another old desktop tower but with a slightly higher spec that my previous and a GeForce2 MX 400.

I installed 9.10 i386 normally, then ran a total update manager from my ISP's Ubuntu mirror, then installed the NVIDIA '96 driver FROM the mirror (not from NVIDIA's site - though that might have worked just as well).

I have now been able to select 1280x1024@60Hz on a Hansol monitor.  It was a bit hard on the eyes because of flicker (even at 60Hz?  Hmmm?) so I backed off to 1152x960@auto refresh, which was fine, and a welcome extra from the 1024x768 which seemed the only option until I got the proprietary driver to work.

Actually, I am still chasing one small issue.  I clicked System/Preferences/Appearance/Visual (to turn 'normal' to 'none') and thought the machine had frozen.  It hadn't but was sucking up "101%" CPU for a while.   That happens on my 9.04 Toshiba laptop too, so it's nothing to do with NVIDIA or 9.10

I like to add System Monitor to a panel and preference everything on, so I can easily see when the machine goes a bit nuts!

Good luck folks, but I think you are really struggling with the older NVIDIA cards that are supposedly supported by the '71 driver set that is no longer (currently) part of the 9.10 distro.  I'd try my RIVA TNT2 in my latest tower (using the NVIDIA site), but I'm tired of reloading U910 umpteen times, so I'm now into "not broken so don't mess with it"!

---

### Post by njsharp on 2009-11-15
I miswrote:
1152x864@75Hz
Sorry

---

