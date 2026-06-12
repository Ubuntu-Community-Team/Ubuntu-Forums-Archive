---
title: "Toshiba Tecra 8200 full screen display on 7.10"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by DawaYe on 2007-10-25
Can anyone assist?

After 7.10 is installed the  OB Trident vidoe card only displays a portion of the full desktop capacity, leaving a trim on both sides black.

I am using a generic driver, not the trident driver and would like to have full screen display ccapability.

Thanks in advance
David
:guitar:

---

### Post by FosterFire on 2007-10-29
What method did you use to install and what version do you have running?

I downloaded from [www.ubuntu.com](www.ubuntu.com) and made the image CD but I have had the install crash 3 times..so far.

---

### Post by schibros on 2007-11-20
I have the same problem too with mine. Im trying to install 7.10 from the live cd i downloaded and burnt from the internet. I used the wubi-cdboot so i can run the live cd. Is there another method i can use in running the live cd? Cos everything i have been reading says boot from cd and nobody has said anything about this wubi-cdboot file. My laptop doesnot seem to be able to boot up with that particular cd. 

When use the CD with the wubi-cd boot and use the second option of booting with a generic vesa graphic driver, i still get to see my desktop partially and the rest of the display looks corrupt.

Please i need help seriously.

Thanks in advance.

---

### Post by davis2k on 2008-04-22
Anything on this? I just installed 8.04 RC on my Toshiba Tecra 8200 and I too have a maximum resolution of 800x600 and I would like to get the full 1024x768 going. Anyone!? Anywhere?! Please help?

---

### Post by some1l8 on 2008-05-27
it seems trident generic driver is fine, but ubuntu cant configure display right in xorg.conf. afte a week researching. i finally found the following settings. it's not perfect, shift about 5 pixels to right, but display is definately more acceptable now.

add following lines into your xorg.conf

```

Section "Device"

	Identifier "Trident CyberXP"

	#Busid	"PCI:10:0"
	Driver "trident"
	#Vendorname	"Trident"
	Option "UseFBDev" "true"

	Option "DPMS"

	Option "Display1400"

	# Option "CyberShadow" "false"

	# Option "CyberStretch" "true"

	Option "NoAccel" "false" 	
	VideoRAM 16384

	Option "BackingStore" "On"

	Option "saveunders" "On"

EndSection



Section "Monitor"

	Identifier "Toshiba Tecra 8200 1400x1050 LCD"

	VendorName "Toshiba"

	ModelName "xsvga+"

	HorizSync 28-90

	VertRefresh 40-110

	Option "DPMS"

	# ModeLine "1400x1050" 107.85 1400 1450 1500 1999 1050 1058 1070 1150

EndSection



Section "Screen"

	Identifier "Default Screen"

	Device "Trident CyberXP"

	Monitor "Toshiba Tecra 8200 1400x1050 LCD"

	DefaultDepth 16

	# DefaultFbBpp 24

	SubSection "Display"

		Depth 16

		Modes "1400x1050" "1280x1024" "800x600"

	EndSubSection

	SubSection "Display"

		Depth 24

		Modes "1400x1050" "1280x1024" "800x600"

	EndSubSection

EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection

```
i'm still looking for solution for '5 pixel shift right', anyone can help?

---

