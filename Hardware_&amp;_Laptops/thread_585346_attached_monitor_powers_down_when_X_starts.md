---
title: "attached monitor powers down when X starts"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by crazytigger on 2007-10-21
So i upgraded to gutsy and everything went fine until - oops.. I get the usual splash screen and console lists during boot and the attched monitor works fine.

As soon as X starts my attached monitor powers down, leaving me with just the LCD on the laptop working... as this screen has large holes in it where a rather over zealous ex-girlfried decided to throw golf balls at it this leaves me in a bit of a pickle. There is almost no useable screen area on the LCD at all.

I found i can Ctrl+Alt F1 and get back to fullscreen console which wakes the attached monitor up, i can then go and edit xorg.conf

Ive spent all day trying to reconfigure xorg - it was a bit of a mess so now the important bits look ike this:

Any help or pointers would be greatly appreciated - im completely stuck and unable to use X at all.

```

Section "Device"
        Identifier      "ATI Radeon Primary"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "MergedFB" "true"
        Option          "MetaModes" "1024x768-1024x768 1024x768-1024x768"
        Option          "MergedDPI" "100 100"
	Option		"MonitorLayout"	"LVDS, CRT" <--I dont know what this does really
EndSection

Section "Device"
        Identifier      "ATI Radeon Secondary"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Screen          1
EndSection


Section "Monitor"
        Identifier      "Internal Monitor"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
EndSection


Section "Screen"
        Identifier      "Internal Screen"
        Device          "ATI Radeon Primary"
        Monitor         "Internal Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "ATI Radeon Secondary"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Internal Screen" #ive tried External screen and also putting both screen in which crashes X
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by jtekUSA on 2007-10-21
I have the same issue except it was after doing a fresh installation of Gusty Gibbon (7.10).  I first did the upgrade via the software manager and no problems on the docking port.  But, I had some weird issues with my network and video card (did not get the new look) so opted to do a fresh install.  Gusty already installs the Nvidia drivers on first boot (glad to see that) but I do not have the control panel anymore.  Stupid me - I did not save or print out the instructions I found that told me how to set up my Nvidia card under Feisty Dawn.

Unlike you, I am not able to see my laptop screen when I am docked (Dell Latitude D620).  The previous trick of doing a FN Key - F8 is not working - well, it is as I can scroll my screen around on my laptop screen (I am able to open just enough to see most of the screen to reboot).

This does not make me happy as I had 7.04 working perfectly with the exception of the external speakers on my docking port.  Ubuntu is the first Linux distro I have found that installs with little to no issues on my laptop.

I will continue searching for those instructions and hope someone can provide some enlightenment on how to get this working again.  I do recall there being a tweak to the monitor setting but can't recall what to do.  Guess that is why I am still a newbie.  :-D

---

### Post by jtekUSA on 2007-10-21
What a difference a good night's sleep can make.  :lolflag:

I found the documentation I used to get my Nvidia card working under Feisty Dawn.  As  side note, I always do my installs off the docking port - easier installation.  I did a test and found that when I installed the drivers per the instructions, Ubuntu would always work on my docking port without fail.  I will try this with Gutsy and see what happens.

Here is the link:  [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html")

Not sure if this helps anyone and I will report back if it works for me.:-k

---

### Post by jtekUSA on 2007-10-23
No go so far - installed the NVidia control panel onto my menu as that was all that was needed (new drivers already installed).  The loading screen appears but then blinks out when I am being taken to the login screen.  I guess that is when X starts.  ;-)

---

