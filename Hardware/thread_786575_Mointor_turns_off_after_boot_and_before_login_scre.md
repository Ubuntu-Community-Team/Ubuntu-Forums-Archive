---
title: "Mointor turns off after boot and before login screen due to Nvidia driver"
date: 2008-05-08
forum: Hardware
---

### Post by KenBW2 on 2008-05-08
**The problem:**
My monitor seems to be having a problem in that after it boots up with the Ubuntu splash screen and just before it shows the graphical login it displays:
> 
usplash 1024x768: Failed
usplash someresolutionthaticantremember: Failed
usplash somesmallerresolutionthatialsocantremember: Failed.
Using 800x600...

Or words to that effect, and then my monitor simply shuts itself off. After I Ctrl+Alt+Backspace it gives me a CLI login, and from there I did sudo rm /etc/X11/xorg.conf to make it sort itself out. Upon restart, this worked, although the Nvidia Restricted Driver is disabled - this had previously given me no problems. Whenever and however I reenable this driver the problem comes back. As stated, without the driver the display does function, but I can't use Compiz. I like Compiz :(

**Potential causes:**
This could be down to two things:
- Before I last restarted my computer I received quite a few system updates
- I "uninstalled" (i.e. used gparted to simply delete) my Kubuntu partition - causing problems with my GRUB etc, but that's another story...

**Extra factors:**
In an attempt to get my GRUB back i installed Ubuntu again on the partition where Kubuntu used to be, and now I can boot both successfully.
On the fresh Ubuntu install the NVidia drivers work fine - with all the updates installed. I tried copypasting the fresh Ubuntu's xorg.conf into the original Ubuntu's since all the hardware is identical but this just caused the problem again.

**Some specs:**
**OS:** Ubuntu 8.04 (both)
**Graphics card:** NV34 [GeForce FX 5200]
**Installed Driver:** "NVidia binary X.Org driver ('new' driver)" (This is disabled on original Ubuntu install)

Any help is greatly appreciated :)

---

### Post by sowelie on 2008-05-08
My guess would be a kernel related issue.  Which kernel are you booting into?  You can verify if there's a kernel module problem by looking at /var/log/Xorg.0.log after the error occurs.  To get to a console when your monitor blanks out, hit ctrl+alt+f1.  Look through the log file for (WW) and (EE), warnings and errors.

---

### Post by KenBW2 on 2008-05-08
Thanks for the insanely quick reply :)

(EE)'s that I found:
(EE) Unable to locate/open config file // Probably because I deleted it
(EE) open /dev/fb0: No such file or directory

I don't know how it could be due to the kernel as its the same Ubuntu install that I had used proviously. Or not?

---

### Post by sowelie on 2008-05-08
Well, not really the kernel, the kernel module, sorry about that.  Have you ever installed custom NVIDIA drivers?  You didn't see any (WW)s in the log?

---

### Post by KenBW2 on 2008-05-08
I don't really know what a kernel module is :S No, I haven't installed custom drivers - only the one(s) that Ubuntu installed for me.
No, there weren't any (WW)s. Is that because I opened it after I'd deleted xorg.conf? Should I do it again after I reenable the Nvidia driver and encounter the problem again?

Thanks again

---

### Post by KenBW2 on 2008-05-08
I had a go at reenabling the Nvidia driver (causing the problem again) and now have a copy of the Xorg.0.log file. These are the new (EE)s and (WW)s:
> 
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(WW) Configured Mouse: No Device specified, looking for one...


The one about Nvidia driver I assume is significant.
Any ideas?

---

### Post by sowelie on 2008-05-08
Yeah, that sounds like a kernel module mismatch.  Although there's usually something in there mentioning that.  Try this for me:

```
sudo aptitude remove nvidia-kernel-common nvidia-glx-new linux-restricted-modules
```

Watch out though, these packages may be used by other packages, so if you get any conflicts, take note of what is being removed so you can reinstall.

Also, what kernel are you running?  Use the command below to output it:

```
uname -r
```

EDIT: Forgot an important piece, after doing the remove, reinstall:

```
sudo aptitude install nvidia-glx-new
```

---

### Post by brigadoon on 2008-05-08
I had similar problems with my Nvidia driver. My solution can be found at...

[http://ubuntuforums.org/showthread.php?t=773391&highlight=Geforce+420+Go+Ubuntu+8.04](http://ubuntuforums.org/showthread.php?t=773391&highlight=Geforce+420+Go+Ubuntu+8.04)

You may need to tell the driver what display to use. I documented the critical lines I needed to add for my laptop in my post. I hope this helps.

---

### Post by KenBW2 on 2008-05-08
I tried both answers.

**@brigadoon**
Thanks for the suggestion, but the solution you posted didn't work :(. After Step 3 
> Re-start Envy. From the main window select NVIDIA and Install the NVIDIA driver (Manual Selection of the Driver). The driver version I selected was the 96.43.05 option. Select Apply and reboot the system when asked.
the problem reoccurs, meaning I couldn't perform Step 4. I tried editing the xorg.conf file anyway, but this solved nothing unfortunately and I had to restore the backup I made.
NVidia X Server Settings tells me that I don't have a NVidia driver in use.

**@sowelie**
I performed the uninstallation that you suggested. After a few "(Y/N/?)"s I was presented with this:
> 
The following packages will be automatically REMOVED:
  linux-generic linux-restricted-modules-2.6.22-14-generic 
  linux-restricted-modules-2.6.24-16-generic 
  linux-restricted-modules-generic 
The following packages will be REMOVED:
  linux-generic linux-restricted-modules-2.6.22-14-generic 
  linux-restricted-modules-2.6.24-16-generic 
  linux-restricted-modules-generic nvidia-kernel-common 


I am unsure of which of these I should reinstall - I don't want to reinstall what you just told me I need to get rid of...

The graphics continue to work, but the NVidia driver is no longer listed in my System/Administration/Hardware Drivers.

uname -r gives me "2.6.22-14-generic" if that helps any...

Thanks for your continued help.

---

### Post by sowelie on 2008-05-08
Okay, I can see you have multiple versions of the kernel modules installed.  Run the remove command I sent before and say yes.  That'll remove all of them so you can start fresh.  Once you're done reinstall the nvidia-glx-new package.

---

### Post by KenBW2 on 2008-05-09
I tried what you suggested - still no joy :(

Screens and Graphics shows me that I'm using the ""NVIDIA GeForce FX (generic)" driver

NVidia X Server Settings says
> 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

nvidia-xconfig just causes the problem to reoccur, forcing me to restore my backed up xorg.conf.

System/Administration/Hardware Drivers is empty, saying that I have no proprietary drivers in use.

My xorg.conf file is a mess (well, not that I know what I'm looking at) - it has 7 sections that refer to my monitor. Is that right? I've attached it, but here's the crucial bits:

Just to be sure - this is my **working configuration**

> 
Section "ServerLayout"
	Identifier	"Default Layout"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1280x960@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection


I'm about ready for moving to a fresh install of Ubuntu which among other things gives me Hibernate functionality. Just means migrating all my settings and applications. Eugh.

Is there anything else you can suggest which might solve my problem?

Thanks.

---

### Post by brigadoon on 2008-05-11
I reviewed your xorg.conf file that you attached to the post a few days ago.

Try the following changes to your xorg.conf file...

Change line 39 from...

***	Driver		"nv"***

to...

***	Driver		"nvidia"***

It looks like you need to repeat this change on line 80 as well. Looks like you have two monitors in your file. The driver install adds the nv in place of nvidia to the xorg.conf file.

After making these changes see if it works. If it still doesn't work you may need to tell the driver what type of display to use. Make the following edit to the xorg.conf file. In the ***Screen*** section after line 39 add the following in a new line...

***	Option		"UseDisplayDevice"	"DFP"***

I am assuming you are using a flat panel display. If not you may need to look at the nvidia driver configuration manual for the option setting that matches your display device. Change the DFP to what ever the manual says it should be. Under the same section I needed to add the following as well...

***	Option		"AddARGBGLXVisuals"	"True"***

If the display still doesn't work try adding that line as well.

I would strongly recommend using Envy to remove and install the drivers. Use Envy to uninstall any drivers previously installed prior to installing a different driver. In my post I manually selected the second driver option. I think you need to select the first driver listed manually. Envy lists 3 driver options to manually install. Try the first one. Make sure the edits above are made to the xorg.conf file. Any edits to the xorg.conf file need to be made with the x-windows session stopped. If it still doesn't work try the second driver. Then try the third if all else fails.

Let me know how it turns out.

---

### Post by KenBW2 on 2008-05-11
Thanks for the advice brigadoon

As I only have one monitor would it be better/less confusing to remove some of the other sections associated with monitors/screens?

With regard to your assumption of flat panel: no, I still live in the days of CRTs and no desk space :P Does this change anything?

I'm aiming for a resolution of 1152x864 if that helps any.

Could you please advise on any changed I need to your advice, since I don't want to make things worse by putting incorrect configuration in?

Thanks alot

---

### Post by brigadoon on 2008-05-11
> **KenBW2 said:**
> Thanks for the advice brigadoon

As I only have one monitor would it be better/less confusing to remove some of the other sections associated with monitors/screens?

With regard to your assumption of flat panel: no, I still live in the days of CRTs and no desk space :P Does this change anything?

I'm aiming for a resolution of 1152x864 if that helps any.

Could you please advise on any changed I need to your advice, since I don't want to make things worse by putting incorrect configuration in?

Thanks alot

There is an old programmer's saying, ***"Better is the enemy of good."***

Do not make changes to the xorg.conf if you can avoid it. Deleting sections can cause other functions to stop. If good works then leave it. Trying to make it better when good gets it done sometimes turns into disaster. ](*,)

If you have a desktop model with a crt display just try the ***nv*** to ***nvidia*** change. This may fix it right away. I don't know what the CRT call out option would be in the driver instruction manual. If I have time I'll see if I can find it. The ***DFP*** option switch will not work for a CRT display.

---

### Post by KenBW2 on 2008-05-11
The nvidia change didn't work. I think I'm going to make a fresh install of Ubuntu anyway - as well as Compiz, I'll be able to get other things like Hibernate which I've missed sorely - and with this being my first Linux install, all the mistakes I made early on when I didn't know what i was doing will be rectified.
I'll leave this install there for now until I need the space for something else (I'm thinking of trying Fedora soon) in case some great ideas arise.

Thanks for all your help guys, sorry it hasn't been very fruitful :(

---

