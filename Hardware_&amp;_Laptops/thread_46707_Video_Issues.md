---
title: "Video Issues"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by larued on 2005-07-05
I succesfully installed Warty Warthog on a Compaq Armada 7710MT. Only problem is it is rediculously huge and i can't log in the right way, i can't even see more than the word language. I know you can cahnge the video setting somewhere, but im not sure where or what to cahnge it to. The max screen size is 800x600. Any help would be appreciated.

---

### Post by henriette_holm on 2005-07-07
If 4.10 uses xorg you can edit the file /etc/X11/xorg.conf - DON'T forget to make a backup first. Look for the part that says - Section "Screen" - maybe you need to change the modes?

And a bit OT: Why did you not use 5.04?

-Henriette

---

### Post by byourg on 2005-07-07
The file your looking for is /etc/X11/XF86Config-4. Here is a partial of my file as I have a Compaq Armada 7400 and I am using Warty on this laptop.

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. ViRGE/MX"
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

---

### Post by larued on 2005-07-07
How would i fix that in the original installation? as i can't get any farther than the main login screen, and i can't use 5.10 yet beacause its not here yet. I need to be able to set that up in the installation somewhere, anyone know where?

---

### Post by henriette_holm on 2005-07-08
I'm not quite sure I understand you. Can you install Ubuntu or does your trouple start when you try to install it?

If you get to the main login screen (a graphical one, right?) the X server must be working, or?`

-Henriette

---

### Post by larued on 2005-07-13
[QUOTE=henriette_holm]I'm not quite sure I understand you. Can you install Ubuntu or does your trouple start when you try to install it?

If you get to the main login screen (a graphical one, right?) the X server must be working, or?`

-Henriette[/QUOTE]
 I can install it, its just that when it boots up ubuntu thinks its running on a larger monitor than I have. My monitor only supports 800x600 at largest, and ubuntu tries to display it so large that all that i can see when i boot is the word language which belongs in the far lower left corner, not in large words across my screen. So i need to change the monitor setup during the install.

---

### Post by larued on 2005-07-13
[QUOTE=larued]I can install it, its just that when it boots up ubuntu thinks its running on a larger monitor than I have. My monitor only supports 800x600 at largest, and ubuntu tries to display it so large that all that i can see when i boot is the word language which belongs in the far lower left corner, not in large words across my screen. So i need to change the monitor setup during the install.[/QUOTE]
 does anyone have any help?

---

### Post by ilmw on 2005-08-09
[QUOTE=larued]I can install it, its just that when it boots up ubuntu thinks its running on a larger monitor than I have. My monitor only supports 800x600 at largest, and ubuntu tries to display it so large that all that i can see when i boot is the word language which belongs in the far lower left corner, not in large words across my screen. So i need to change the monitor setup during the install.[/QUOTE]

Press Ctrl-Alt-Backspace when you see the large login. This will bring you to the console mode. Then edit the file as previous replies (especially #2 and #3) according to your monitor setting.

---

