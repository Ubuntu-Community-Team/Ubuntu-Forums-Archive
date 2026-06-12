---
title: "Ubuntu 9.10 nvidia drivers on Acer Aspire 5738z"
date: 2010-02-21
forum: Hardware
---

### Post by mujanovic on 2010-02-21
It seems that I cannot install nvidia drivers on my laptop Acer Aspire 5738z which has nVIDIA GEFORCE G105M graphic card. When I install it following instructions that worked for others I get a split screen on my next login (split in 6 tiles). What should I do to get normal screen (roll back to non-nvidia drivers) or how can I fix this to work? Please help me because it seems that other suggestions to fix this do not work for me.
Thanks to anyone who answers!

---

### Post by Mythrall on 2010-03-01
I've got the same problem with my Acer 5739G laptop. I've got the Nvidia GeForce GT 240M card in my laptop. I've read that this card isn't supported by the official release signed off by Canonical (185) and that the 190.53 drivers from the site are required. After installing those drivers I've still got the same problem and I'm currently researching any/every solution. I'll keep you posted if I've successfully bypassed this problem.

---

### Post by Mythrall on 2010-03-02
I've finally gotten mine to work :)
There was a very helpful article at [this site]("http://jens.yelles.se/2009/07/02/drivers-for-nvidia-geforce-g105m/") that gave a decent stubbing of the xorg.conf file and the configurations needed to bypass the problems we've been seeing. With just a few minor tweaks I was able to get rid of my 6screen problem.

Here's my xorg.conf file that works with my system. 

NOTE: if you use the example xorg.conf file from the article I've linked to you'll have to change every single quote symbol because they copy over as the stylized quote and not the one that the OS expects (my file posted already has that done). 
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
	Option "NvAGP" "0"
	#    Option "UseInt10Module" "True"
	#    Option "UseEDID" "False"
	Option "ExactModeTimingsDVI" "True"
	Option "ModeValidation" "NoHorizSyncCheck,NoDFPNativeResolutionCheck,NoExtendedGpuCapabilitiesCheck,NoWidthAlignmentCheck,NoVertRefreshCheck"
EndSection

Section "Monitor"
	Identifier     "Configured Monitor"
	VendorName     "Unknown"
	ModelName      "AUO"
	#    HorizSync       30.0 ? 100.0
	#    VertRefresh     55.0 ? 110.0
	#    DisplaySize    344 193
	#    Mode    ?1366?768?
	#    DotClock    69.5MHz
	#    HTimings    1366 1414 1446 1437
	#    VTimings    768 771 775 806
	#    EndMode
	# Modeline ?1366?768?   69.50  1366 1414 1446 1437  768 771 775 806
	Modeline "1366?768"   69.50  1366 1414 1446 1473  768 771 775 806 -hsync -vsync
	# Modeline "1366?768q"   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync
	#    Option "DPMS" "True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth    24
	Option         "TwinView" "0"
	SubSection     "Display"
		Modes    "1366?768"
		Depth       24
	EndSubSection
EndSection

```

---

### Post by Bedrox on 2010-04-13
And another happy customer here on an Acer Extensa 5635G. Thanx to Mythrall for posting the 'requoted' config file.

---

