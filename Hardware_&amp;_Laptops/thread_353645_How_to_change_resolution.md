---
title: "How to change resolution?"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by Villenya on 2007-02-04
I currently have Edgy running on inspiron E1505 with x1400. 

I am using 1605x1050 resolution right now but i want switch to 1280x800. The 1280x800 is not listed under the screen resolution preferences. how do i change to 1280x800 or any other resolutions?

---

### Post by jml on 2007-02-05
I have used this trick in Debian but not Ubuntu so try at your own risk.  Open a terminal and type in the following command.  sudo gedit.  After you type in your password, and gedit opens, open the file /etc/X11/xorg.conf.  Go to the section titled "screen"  Subsection "Display"  There will be several entries, with Depths ranging from 1 to 24.  (your system may differ)  In each subsection add to the line labeled Modes the resolution you want in the following format "1024x768"  Include the quotation marks and make sure a space separates each entry.  Save the file and then log out and log back in.  You should now have multiple choices for screen resolution.

Joe

---

### Post by juantao on 2007-02-05
Yes, this will work the same in Ubuntu as it does in Debian. One caveat; when adding the entry for "1280x1024" just follow the layout of what's already there. Mine looks like this: (as you can see, I don't go higher than "1280x1024"). The stanza to keep the screen from going 'blank' is at the end - I HATE the screen blanking feature - HATE IT!

Section "Monitor"
        Identifier      "DELL M990"
        Option          "DPMS"
        HorizSync       50-96
        VertRefresh     60-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Monitor         "DELL M990"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerFlags"
        Option "blank time" "0"
        Option "standby time" "0"
        Option "suspend time" "0"
        Option "off time" "0"
EndSection

---

### Post by Villenya on 2007-02-05
hm... here's my xorg.conf

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

i added "1440x900" resolution but it's still not displayed under change screen resolution.

but funny thing is i'm running 1650x1050 even though that option is not displayed in the xorg.conf. :(

---

### Post by ASteward on 2007-09-17
I'm in the same boat.  I added 1280x1024 to the list, but it wasn't available on the resolution list.

---

### Post by frenchcr on 2007-09-17
i got rid of **all** resolutions in xorg.conf bar the native res for my screen. works perfect. backup that .conf first before you change like this though.

i mean i got rid of all but native resolutions, from all sections of that file :)

---

### Post by John.Michael.Kane on 2007-09-17
> **ASteward said:**
> I'm in the same boat.  I added 1280x1024 to the list, but it wasn't available on the resolution list.

Resolution methods.adjust for which gpu your using.

[screen refresh rates....]("http://ubuntuforums.org/showthread.php?p=2605716#post2605716") 

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

Note: Make sure to have your lcd/crt manual, As you will need to refer to it for certain settings.

Another note For 50hz refresh rate issues with "nvidia based gpu's". You can disable Dynamic Twin View in /etc/X11/xorg.conf. Add the below option to xorg's card device section to turn it off.
```
Option "DynamicTwinView" "False"
```

---

### Post by Linicks on 2007-09-18
> **SD-Plissken said:**
> RAnother note For 50hz refresh rate issues with "nvidia based gpu's". You can disable Dynamic Twin View in /etc/X11/xorg.conf. Add the below option to xorg's card device section to turn it off.
```
Option "DynamicTwinView" "False"
```

I reported this ages ago to KDE bugs, and it turns out it is just a false report - the refresh rate is still 60Hz, but just the way it is read shows (incorrectly) 50Hz.

[https://bugs.kde.org/show_bug.cgi?id=136212](https://bugs.kde.org/show_bug.cgi?id=136212)

Setting the Option "DynamicTwinView" does indeed force it to read the value right, but it is not required.

Nick

---

