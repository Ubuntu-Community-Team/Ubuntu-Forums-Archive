---
title: "Multiple Monitors/ Dual Head"
date: 2005-01-18
forum: Hardware &amp; Laptops
---

### Post by Nebula10111 on 2005-01-18
I'm trying to set up a dual head system on my laptop, or just a monitor as desktop extension. The graphics card is an ATI IGP 320M aka Mobility U1. I plug the monitor in and I get crazy wavy lines. Ok I'm new to this. Can somebody fill me in on this xinerama buisness. Im researching it a bit and getting somthingabout xinerama, althoughI'm not clear as to what it is. I guess I have to edit my XF86Config-4 file and add in the extra monitor, screen and device. Any help would be vastly appreaciated, thanks.

---

### Post by CompShrink on 2005-01-18
I don't know of any easy way to do this, sadly.

The way I got my second monitor up was by refering to the XF86Config-4 file i had from a backup of my previous suse 9.1 install, where i had the app SaX2 to set up the monitor with a gui (and autodetection).

You know what generally you have to do, now for the specifics of your monitor.... I hope someone else knows of an easier way.

Here's my server layout section:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Option		"Xinerama" "on"
	Option		"Clone" "off"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Screen 		"Second Screen" RightOf "Default Screen"
EndSection
``` 

Then for the Monitor and Device sections, follow the example of the monitor you already have, though of course it won't be exact...

---

### Post by Nebula10111 on 2005-01-19
Yeah I configured my XF86Config-4 file inputing the correct info for the second screen and device. But when I restared I got someweird error, about starting x. It couldnt start X for whatever reason. So maybe I had the server section wrong, I dont think I had the option syntax right, so I'll go ahead and try that.

---

### Post by Nebula10111 on 2005-01-19
Ok tried it. I'm positive I've got the XF86Config-4 file setup correctly, well almost sure, I have my second device section, my monitor with appropraite specs and screen. I setup the server layout section like yours but alas nothing. same issue it boots up and I get a to tty1 and then get a x server error. What is "Xinerama"? Maybe somthing is installed... not sure. Anyway thanks for the help.

---

### Post by Viro on 2005-01-20
[QUOTE=Nebula10111]Ok tried it. I'm positive I've got the XF86Config-4 file setup correctly, well almost sure, I have my second device section, my monitor with appropraite specs and screen. I setup the server layout section like yours but alas nothing. same issue it boots up and I get a to tty1 and then get a x server error. What is "Xinerama"? Maybe somthing is installed... not sure. Anyway thanks for the help.[/QUOTE]
 Instead of cloning the display, xinerama allows you to use the 2nd monitor as an extension of the primary monitor. So you can think of it as doubling your screen space by spreading your desktop over 2 monitors.

---

