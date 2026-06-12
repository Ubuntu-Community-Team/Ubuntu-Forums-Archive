---
title: "Getting my laptop resolution to 1600x1200"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by neverett on 2007-02-04
I'm running Feisty Fawn Herd 2 and have installed 915resolution.  I can't seem to figure out how to get my resolution to 1600x1200?  Or anything higher than 1200x800.  I have the Intel 945GM and I have a Presario V5204NR.  Does anyone know how to do this?  Thanks for any help in advance.

NE

---

### Post by gradedcheese on 2007-02-04
have you tried editing /etc/X11/xorg.conf and adding that resolution?

---

### Post by neverett on 2007-02-04
I have tried that, the highest I can get it to go is 1200x800.  Does anyone have any other ideas?  1200x800 is okay, but I like a little bit higher resolution than that.  Thanks for all the help in advance.

---

### Post by #Reistlehr- on 2007-02-04
did you make sure you have the correct drivers installed for the video card?

---

### Post by neverett on 2007-02-04
> **#Reistlehr- said:**
> did you make sure you have the correct drivers installed for the video card?

I'm not sure how to check to see if they're installed... can you help me out?

NE

---

### Post by KITTILUVER on 2007-03-12
Visit this site: [http://www.geocities.com/stomljen/readme.html](http://www.geocities.com/stomljen/readme.html)
A post by: Steve Tomljenovic

I followed everything, except /etc/init.d/boot.local. I changed that to /etc/init.d/bootmisc.sh for Ubuntu Feisty. My resolution of 1440x900 came up instantly after restart, and several weeks of "googling".

I don't believe any changes are needed to xorg.conf, but here is mine in that section of monitor and display. It shows some modifications that were made prior to the above paragraph, but no changes for that.

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel GMA 945"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
	Viewport	0 0
	Depth		24
	Modes 		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Hope this helps . . Tom :)

---

