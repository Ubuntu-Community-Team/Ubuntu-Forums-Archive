---
title: "Low screen resolution"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by _sAm_ on 2007-07-23
The resolution on my screen is to low. This happened after I reinstalled Ubuntu sice I got a new gpu, 
I have been reading some guides, but now I am only confused and unsure, so I would bee Very glad if someone could help me.

My screen is an Eizo s1910([http://www.eizo.com/support/discontinued/lcd/s1910.asp](http://www.eizo.com/support/discontinued/lcd/s1910.asp)).
My gpu is a a nVidia 8800 serie.

I have not installed any nvidia drivers, and I don't want to either– I only want to get the correct resolution witch are “1280x1024”. 

I have made a backup of the xorg.conf file with this command sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
. But I don't know how to restore this backup without a GUI, so before I trying any suggestion here I would like to know. 
 
And here are some parts of my xorg.conf -file:  

Section "Monitor" 
	Identifier	"Generic Monitor" 
	Option		"DPMS" 
	HorizSync	28-51 
	VertRefresh	43-60 
EndSection

Section "Screen" 
	Identifier	"Default Screen" 
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]" 
	Monitor		"Generic Monitor" 
	DefaultDepth	24 
	SubSection "Display" 
		Depth		1 
		Modes		"1024x768" "800x600" "640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth		4 
		Modes		"1024x768" "800x600" "640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth		8 
		Modes		"1024x768" "800x600" "640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth		15 
		Modes		"1024x768" "800x600" "640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth		16 
		Modes		"1024x768" "800x600" "640x480" 
	EndSubSection 
	SubSection "Display" 
		Depth		24 
		Modes		"1024x768" "800x600" "640x480" 
	EndSubSection 
EndSection

I know of the script you can run, but I don't know what to answer. So, is it possible for me to just manually add the wanted resolution? 

I have checked and found some information about my screen:

Horizontal Scan Frequency; Analog: 24.8 ~ 80 kHz (Automatic) 
Digital: 31 ~ 64 kHz

Vertical Scan Frequency; Analog: 50 ~ 75 Hz (Automatic)
Digital: 59 ~ 61 Hz, (VGA Text: 69 ~ 71 Hz)

Resolution; 1280 dots x 1024 lines

Dot Clock (Max.); Analog: 135 MHz, Digital: 108 Mhz
Display Colors; 16 million colors (max)

---

### Post by scompany on 2007-07-23
To restore backup just type:
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Try modifying your Screen section in xorg.conf to look like this:

> Section "Screen"

Identifier "Default Screen"
Device "nVidia Corporation G80 [GeForce 8800 GTS]"
Monitor "Generic Monitor"
DefaultDepth 24

SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

EndSection

Then restart your xorg or computer.

If this don't change resolution, go to System - Preferences - Screen Resolution and try to change it there.

---

### Post by _sAm_ on 2007-07-23
Thanks for your answer:-) 

I tried what you said but it didn't turn out well, now Ubuntu wont start X. I have printed out the command to restore my backup but I don't get any terminal; do you know how can I run it?

Edit; 
Ok, I have now tried the restore command but it didn&#8217;t work out. I got an error saying no such files? I checked the command I typed by pressing key up.

---

### Post by _sAm_ on 2007-07-24
I have now found out why I got an error when trying to restore the backup. I said I used the command &#8220;sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup&#8221;, but I forgot that I had changed it to  xorg.conf_backup

So now X is up and running again, thanks to this site [http://www.linuxcommand.org/](http://www.linuxcommand.org/) As soon as I got time I will try that tutorial twice so I to can handle this by my self.  

But I still need help to get the correct resolution, anyone that has any tip? :(


Edit; 
I dont get it, I have changed the xorg.conf to this;

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-64
	VertRefresh	59-61
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1080x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection

The I restarted X (with no problem), but I still CANT change the resolution. Hope someone can help me out.

---

### Post by _sAm_ on 2007-07-24
I just wanted to post to say that I have managed to fix the problem, the correct resolution is now back.

I guess this is an good example that shows that Linux is way less user friendly then windows - I am looking forward to the new xorg.file that will come with next Ubuntu.

---

