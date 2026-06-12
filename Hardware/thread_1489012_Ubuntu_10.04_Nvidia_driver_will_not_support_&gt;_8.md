---
title: "Ubuntu 10.04 Nvidia driver will not support &gt; 800x600"
date: 2010-05-20
forum: Hardware
---

### Post by Storello on 2010-05-20
This is my first time using Ubuntu and my first post so please be patient.  

I just replaced WindowsXP with Ubuntu 10.04 and I can't get the NVIDIA-Linux-x86-173.14.25-pkg1.run driver to support any display resolution higher than 800x600.  If I run the standard driver, my LCD HDTV that I'm using as a monitor shows that it is set at 1024x768 60Hz.  This is fine, but since it's using the CPU it can't keep up with streaming video and the result is a very annoying jitter.  This same hardware worked OK with WindowsXP.  The video card is an Nvidia GeForce FX 5200 that's attached to the VGA port on the monitor.  I also tried attaching it to the HDMI port but that did not display anything at all.  I also tried adding the "modes "1024x768" "800x600" "640x480" line in the xorg.conf file but that resulted in a blank screen.  

Here is the Nvidia section of the output from lshw -c display while I'm using the default driver:

 *-display
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 1
       bus info: pci@0000:03:01.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
       resources: irq:17 memory:de000000-deffffff memory:d0000000-d7ffffff(prefetchable) memory:df020000-df03ffff(prefetchable)

I'm guessing that the issue is that the Nvidia driver is trying to figure out what my monitor is to build a list of working resolutions but it doesn't know this monitor so it defaults to a max of 800x600.  If I could find a way to force it into 1280x768 with the Nvidia driver I think all would be good.

Any thoughts?

---

### Post by Storello on 2010-05-23
OK, this is getting frustrating.  I loaded Ubuntu 10.04 on another PC with an ATI Rage XL video card and I can't get it to display anything over 800x600 either.  It did work at higher resolutions using WindowsXP.  Here's the lshw -c display on this PC:

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Rage XL
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 27
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:fd000000-fdffffff ioport:d800(size=256) memory:fe9de000-fe9defff memory:48040000-4805ffff(prefetchable)

I've tried creating an xorg.conf file but that doesn't seem to do anything any thoughts?  Here's a copy of the xorg.conf:


Section "Device"
	Identifier	"ATI Technologies, Inc. Rage XL"
	Driver		"ati"
EndSection

Section "Monitor"
	Identifier	"Viewsonic"
	Modeline	"1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
	Option          "PreferredMode" "1024x768_60.00"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage XL"
	Monitor		"Viewsonic"
	DefaultDepth	24
	SubSection "Display"
        	Depth           24
       		Modes   "1024x768" "800x600" "640x480"
    	EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

---

### Post by Storello on 2010-05-23
Still talking to myself here.  OK.  I got the display optimized on the PC with the ATI video card via the xorg.conf file but using similar methods with the NVIDIA board have not worked.  I'll send out log files and more details later.

---

### Post by Storello on 2010-06-07
Good news - my display is working at higher resolutions and speed now.  Bad news - I had to buy another video card to do it.  I installed an NVIDIA GeForce GT 220 and all is good now.

---

### Post by hacjr on 2010-06-23
First post ever.  Using Ubuntu 10.04 and Nvidia GT220 card.  Can't get the card to initialize at all.  Always goes to the menu for low resolution mode/reconfigure/prompt/etc.

Tried the Nvidia drivers that come within Ubuntu and tried installing the latest driver from the Nvidia website.

What version of the driver are you using?  Thanks.

---

