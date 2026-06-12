---
title: "Resolution problems with Dell Latitude C600 - Hardy 8.04"
date: 2008-07-24
forum: Hardware
---

### Post by Jeconti on 2008-07-24
Before I'm immediately flamed for being a newbie and not investigating the forums prior to posting. I have followed the recommendation of the forums and other posts that suggest forcing resolution modes in xorg.conf

This has not worked. Max resolution is still 800x600.

Below is my xorg.conf file, shown where appropriate. I have reverted it to it's original status before I started adding anything. Any help on this one?

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"

Identifier "Generic Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by overdrank on 2008-07-24
> **Jeconti said:**
> Before I'm immediately flamed for being a newbie and not investigating the forums prior to posting. I have followed the recommendation of the forums and other posts that suggest forcing resolution modes in xorg.conf

This has not worked. Max resolution is still 800x600.

Below is my xorg.conf file, shown where appropriate. I have reverted it to it's original status before I started adding anything. Any help on this one?

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"

Identifier "Generic Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Configured Video Device"
EndSection

Hi and have you used the command ```
gksu displayconfig-gtk
``` and change your settings there. Also how much memory is in the system as it shares with the graphics?

---

### Post by Jeconti on 2008-07-24
Solved. Thank you.

---

### Post by dmatthys on 2008-11-22
I changed my settings there and it said it worked. However under System>Preferences>Screen resolution its still showing as 800x600 any ideas

   Dell Latitude C600 
   Ati Rage Mobility
   Dell Laptop Monitor 1024x768

I rebooted the system after i changed the settings via the command line as instructed above/below depending on how your view is set

I also have tried the command reconfigure xserver xorg.conf

I have also tried configuring my xorg.conf file manually heres what i have now it has been modified however i have only been using ubuntu for about a week so im not sure i did it right 

Section "Device"
 Identifier "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
 Driver "ati"
 BusID "PCI:1:0:0"
     # External monitor is a viewport into the panel
            Option "MetaModes" "1024x768-1280x1024"
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 Option "DPMS"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
 Monitor "Generic Monitor"
 DefaultDepth 16
 SubSection "Display"
  Depth 1
  Modes "1024x768"
 EndSubSection
 SubSection "Display"
  Depth 4
  Modes "1024x768"
 EndSubSection
 SubSection "Display"
  Depth 8
  Modes "1024x768"
 EndSubSection
 SubSection "Display"
  Depth 15
  Modes "1024x768"
 EndSubSection
 SubSection "Display"
  Depth 16
  Modes "1024x768"
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes "1024x768"
 EndSubSection
EndSection

I have tried to figure several options out on my own and none of them have worked and i searched the net and this thread was the closest i found to my situation sorry imma noob but im learning quickly and enjoying the experience the more i learn ubuntu is way better then windows i can almost change anything about the way it looks 

except my screen resolution lol someone please help

---

