---
title: "Just installed for first time stuck in 640x480"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by bleakcabal on 2005-06-05
Hi, I just installed Ubuntu minutes ago. 

My videocard is an ATI Radeon 9800 Pro 128 mb.

For some reason the desktop is in 640x480 60hz.

When I try to change the resolution ( using System->Preferences->Screen Resolution ) the only the only choice it lets me choose is 640x480.

Did I miss something during the installation ? 
How can I change this now ?

Forgive my total newbiness and lack of experience, I am totally new to this.

---

### Post by codemills on 2005-06-05
[QUOTE=bleakcabal]Hi, I just installed Ubuntu minutes ago. 

My videocard is an ATI Radeon 9800 Pro 128 mb.

For some reason the desktop is in 640x480 60hz.

When I try to change the resolution ( using System->Preferences->Screen Resolution ) the only the only choice it lets me choose is 640x480.

Did I miss something during the installation ? 
How can I change this now ?

Forgive my total newbiness and lack of experience, I am totally new to this.[/QUOTE]
 #>sudo /etc/X11/xorg.conf
(give ur normal user password)
find and edit the lines as show below
```

Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection


```

---

### Post by bleakcabal on 2005-06-05
I have the following :

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"ati"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"I"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"I"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

If I understand correctly this means that at 24 bits color depth I can choose all the resolutions which are listed in modes. I don't know they are not available...

---

### Post by crane on 2005-06-05
Find out what the specs are on your monitor. Especially your horzSync and VertSync. Then edit the section of you xorg.conf file.
> 
Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	31-65
	VertRefresh	55-120
#	HorizSync	28-49
#	VertRefresh	43-72
	Option		"DPMS"
EndSection
Those are the setting from my monitor so be sure to change then to whatever yours should be.
I would suggest using the # sign to comment out the old settings the just add your new ones. That way if there is a problem you can easily change it back.

*NOTE*
Setting these rates higher than recommended by manufacturer can cause damage or destroy a monitor.

---

### Post by bleakcabal on 2005-06-05
Ok thanks, I changed this, plus I removed all modes except 1024x768 at 24 depth and now it works correctly !

Thank you for your help everyone who awnsered.

---

### Post by Curlydave on 2005-06-05
It probably didn't set up right in the xorg config because it doesn't tell you that you need to use "space" to select your resolution, rather than a common first impression to hit "enter", which just skips the screen.

---

