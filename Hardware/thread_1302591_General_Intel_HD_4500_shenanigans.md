---
title: "General Intel HD 4500 shenanigans"
date: 2009-10-27
forum: Hardware
---

### Post by Lateralis on 2009-10-27
Greetings all! 

I had Ubuntu 9.04 installed on my Fujitsu Siemens laptop and all worked well.  Has the Intel HD 4500 graphics card which generally worked OK.  I only use the computer for work so funkaay graphics and uber awesome 3D isn't that important for me.  However, I did want to configure my desktop and user experience using Compiz, but found that it wouldn't load properly.  Again, wasn't so fussed so didn't go too far with it.  But I have now just updated to 9.10 from 9.04 and the graphics seem to have taken a slight and hugely annoying step backwards.  I use dual monitors all of the time, with additional monitor running at 1280x1024.  All was fine in 9.04, but in 9.10 I do not have the option to select this resolution.  I have 5 options - one 16:9 aspect ration and four 4:3 - but none of them are 1280x1024.  All of the other resolutions look **hideous**.  Can anyone tell me how to adjust the resolution on the external monitor?  

Secondly, I thought that in 9.04 I had proprietary Intel drivers but I genuinely can't remember.  Does anyone know if there have ever been Intel drivers that were selectable under System->Hardware Drivers?  

Thirdly, if anyone can tell me how to get Compiz to work I'd be ubre grateful.  At the moment I get the following after typing *compiz* into the command line:  

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (2304x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```


Many thanks in advance.  
Jim


Addendum: I've just tested out my screensaver (spirographX) and that is generally smooth but occasionally jerky.  Seems like generally the graphics performance has degraded after the update and has totally screwed up the options for my additional monitor.  =(

---

### Post by Lateralis on 2009-10-27
I think I have just "solved" my compiz "problems".  Hurrah!  

But everything else is outstanding. =(

---

### Post by Lateralis on 2009-10-28
Right, an update.  

I think I'm quite happy with the way I have configured everything on the laptop and basically looks just about how I want it.  I still have a few issues with compiz but they are my problems that I'm sure I can solve. 

I still have one majorly annoying issue surround my dual monitors though.  To reiterate: 

I'm on a laptop whose monitor works at 1280x800.  I connect an external monitor up to increase my workd productivity and this monitor works at 1280x1024.  I had this set up *perfectly* fine in 9.04, but since I upgraded the dual monitor setup does not work.  I get 5 screen resultions, namely:

1360*768, 1152*864, 1024*768, 800*600 and 640*480.  Needless to say these resolutions look utter crap and make the monitor unusable.  

My xorg.conf looks like this: 

```


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```


I am quite stuck here as I'm not that familiar with xserver commands or editing xorg.conf and none of the GUIs allow me to change the resolution to the correct one.  


Jim

---

