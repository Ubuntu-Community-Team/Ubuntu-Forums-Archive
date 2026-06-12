---
title: "How to change GDM (Login Screen) Resolution"
date: 2008-09-15
forum: General Help
---

### Post by Frank_TX on 2008-09-15
[B]
How to change GDM (Login Screen) Resolution[/B]

	In Terminal insert >
		**sudo gedit /etc/X11/xorg.conf**


	Scroll down and look for _*Section “Screen”*_,  Then add the red part if it is
	not there.  Replace the highlighted resolution with the desired resolution. 		Save and restart the computer. (*Replace refresh rate if needed*)



	Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
[COLOR="Red"]	SubSection "Display" 
		Depth	24 
#		Virtual	[COLOR="Blue"]1680 1050 [/COLOR]
		Modes   [COLOR="Blue"]"1680x1050@60" [/COLOR]
	        EndSubSection[/COLOR]
        EndSection



	Example for 1280x 1024 resolution with 60 refresh rate. 
		
	Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display" 
		Depth	24 
#		Virtual	         1280 1024
		Modes		"1280x1024@60" 
	EndSubSection
        EndSection




**This worked for me since the login screen had an odd resolution and once logged in it had the right resolution. Now login screen has correct resolution =) Hope this works for you! =)**

:P)

:lolflag:

---

### Post by arch0njw on 2008-09-16
Cool!  Thanks for sharing.  This is one of the really great things about the community!

---

