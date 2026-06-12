---
title: "refresh rate"
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by william_nbg on 2006-06-16
I just upgrading from breezy to dapper and I'm trying to set everything up.

I'm having problems with my refresh rate, I can't get it  to set at anything other that '60'

I've tried everything I know:

Here is my xorg

Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
    HorizSync 30-95
    VertRefresh 50-160
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "1x1"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "1x1"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "1x1"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "1x1"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "1x1"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "1x1"
    EndSubSection

---

### Post by aanderse on 2006-06-16
Just want to double check ... are the actual values of your monitors HorizSync and VertRefresh the values in your settings; what is the brand name and model?

---

### Post by william_nbg on 2006-06-16
Thanks for your reply!

My monitor is an Eizo F77 and I found those rates on the internet.

Though, I'm not sure if I should change the monitor name??

---

### Post by tseliot on 2006-06-16
Try point 5 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

If that doesn't work, please try point 10 of the Problems Section

---

### Post by william_nbg on 2006-06-17
Thanks for you reply!

I tried step 5 in the trouble shooting section of your 'how to' (great work, by the way) and it still doesn't seem to want to read from my xorg file at all. I left only the "1280x1024" resolution in by in the screen resolution in pref I still get several resolutions to choose from but only 60 refresh. In Breezy I could go as high as 85. If I include a modeline it ingores this as well.

Here's part of my xorg as is:

Section "Device"
	Identifier	"NVIDIA Geforce 6600"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Eizo F77"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Geforce 6600"
	Monitor		"Eizo F77"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Any ideas you have would be great.

I really just want 1280x1024 at 75 refresh

---

### Post by 5ebastian on 2006-06-17
Hi
I have a problem that might be related to this. I was going to make a new post but I'll put it in here instead. 

I have been running Ubuntu since the release of 5.04 but now I have run into some problems that I can't find a solution to. 
I recently upgraded from Breezy to Dapper RC (with apt-get upgrade -d). After upgrade and reboot (when GDM should show up) my monitor says "Monitor is working out of scan range". 
Before that I see the bootscreen with progressbar etc and after boot is complete I can Ctrl-ALt-F1 and get a working commandline login. 

I have a Dell P990 ([http://support.dell.com/support/edocs/monitors/p990/specs.htm](http://support.dell.com/support/edocs/monitors/p990/specs.htm)) connected to a Creative Geforce2 64MB DDR graphics card. I used to run it at 1600x1200 at 75Hz refresh rate under Breezy with no problems. 

I thought this would be a simple problem with just editing xorg.conf (and it probably is), but the system seems to disregard anything I write there. Does GDM override the resolution settings in xorg.conf?

I have tried several things:

* Lower the settings in xorg.conf, including the horizontal and vertical frequency rages.  
* Done sudo dpkg-reconfigure xserver-xorg a couple of times. 
* Upgrading the system (apt-get) to be sure that the problem is not caused by a broken package in the release candidate but fixed in the final Dapper release. 
* Connecting another monitor (17" Dell), it gives no screen except textmode. 
* I have replaced my graphics card whith an old Geforce256. 
* When booting from a shipit Breezy live CD the monitor works (tried 1024x768,60Hz).
* When connecting the monitor to another computer (WinXP, (yeah I know)) works fine, even with high resolutions (1600x1200,75Hz,93.7kHz and 1600x1024,85Hz,91.3kHz). 

So: The monitor works, the graphics card works. But I still see no gnome or gdm. 

Here ([http://seb.aquilina.se/filer/xorg.conf-problem.8bh30lrt.slt/](http://seb.aquilina.se/filer/xorg.conf-problem.8bh30lrt.slt/)) are some of the xorg.conf setups I have tried, and also my latest Xorg.0.log. 

Does anyone have any suggestions? 
Hopefull that someone can help me out here. 
/Sebastian Bengtsson
(typed up under Windows xP)

---

### Post by BeatBoxRocker on 2006-06-17
Maybe this can help you.

Change the line of the desired resolution and add the refresh rate with _XX. You must replace XX with the value you want. For example:

Depth 24
Modes "1280x1024_75" "1024x768" "832x624" "800x600" "1x1"
EndSubSection

You can add this to every depth section that you use, but sure you'll only need it at 24 depth.

Saludos!

---

### Post by william_nbg on 2006-06-17
[QUOTE=BeatBoxRocker]Maybe this can help you.

Change the line of the desired resolution and add the refresh rate with _XX. You must replace XX with the value you want. For example:

Depth 24
Modes "1280x1024_75" "1024x768" "832x624" "800x600" "1x1"
EndSubSection

You can add this to every depth section that you use, but sure you'll only need it at 24 depth.

Saludos![/QUOTE]


Tried it, and several varations, but it simply jumps down to the next resolution: 1024x768 at 75 refresh.

It's strange, on Breezy it would take as high as 85, but I prefer 75

---

### Post by william_nbg on 2006-06-17
OK - Now I have it!!!

I put: Option "UseEDID" "False" in the device section which I got from TSEliot's great how to and then changed "1280x1024" to "1280x1024_75" and works like a charm.

Thanks for all the help, I few small pachage problems which I know how to handle and then my Dapper will be up to 100% as Breezy was.

Though, I'm not sure why Dapper doesn't like modelines???

---

### Post by william_nbg on 2006-06-17
[QUOTE=5ebastian]Hi
I have a problem that might be related to this. I was going to make a new post but I'll put it in here instead. 

I have been running Ubuntu since the release of 5.04 but now I have run into some problems that I can't find a solution to. 
I recently upgraded from Breezy to Dapper RC (with apt-get upgrade -d). After upgrade and reboot (when GDM should show up) my monitor says "Monitor is working out of scan range". 
Before that I see the bootscreen with progressbar etc and after boot is complete I can Ctrl-ALt-F1 and get a working commandline login. 

I have a Dell P990 ([http://support.dell.com/support/edocs/monitors/p990/specs.htm](http://support.dell.com/support/edocs/monitors/p990/specs.htm)) connected to a Creative Geforce2 64MB DDR graphics card. I used to run it at 1600x1200 at 75Hz refresh rate under Breezy with no problems. 

I thought this would be a simple problem with just editing xorg.conf (and it probably is), but the system seems to disregard anything I write there. Does GDM override the resolution settings in xorg.conf?

I have tried several things:

* Lower the settings in xorg.conf, including the horizontal and vertical frequency rages.  
* Done sudo dpkg-reconfigure xserver-xorg a couple of times. 
* Upgrading the system (apt-get) to be sure that the problem is not caused by a broken package in the release candidate but fixed in the final Dapper release. 
* Connecting another monitor (17" Dell), it gives no screen except textmode. 
* I have replaced my graphics card whith an old Geforce256. 
* When booting from a shipit Breezy live CD the monitor works (tried 1024x768,60Hz).
* When connecting the monitor to another computer (WinXP, (yeah I know)) works fine, even with high resolutions (1600x1200,75Hz,93.7kHz and 1600x1024,85Hz,91.3kHz). 

So: The monitor works, the graphics card works. But I still see no gnome or gdm. 

Here ([http://seb.aquilina.se/filer/xorg.conf-problem.8bh30lrt.slt/](http://seb.aquilina.se/filer/xorg.conf-problem.8bh30lrt.slt/)) are some of the xorg.conf setups I have tried, and also my latest Xorg.0.log. 

Does anyone have any suggestions? 
Hopefull that someone can help me out here. 
/Sebastian Bengtsson
(typed up under Windows xP)[/QUOTE]



I was somewhere similar right after my Dapper upgrade.

When my X wouldn't start I put in:

sudo dpkg-reconfigure -phigh xserver-xorg

and then

sudo /etc/init.d/gdm restart

which will genorate a new xorg.conf

and then I installed the nvidia driver according to TSEliot's How to

---

