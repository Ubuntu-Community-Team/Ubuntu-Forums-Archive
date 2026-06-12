---
title: "Nvidia Driver Increase Refresh Rate"
date: 2009-05-26
forum: Hardware
---

### Post by burakvarhan on 2009-05-26
Hello,

I am using Ubuntu 9.04 and Geforce Go 7400 graphics card is installed on my laptop. **Without** enabling Ubuntu Nvidia Accelerated Graphics Driver my machine works with 70Hz refresh rate. However when I installed the Nvidia Graphics Driver the refresh rate diminishes to 60Hz and by no means I could change it.

I would like to ask if it is possible to boost the refresh rate with Nvidia Graphics Driver by modifying xorg.conf file and how to do it?

My current xorg.conf file which works perfectly with 70Hz is below:

[COLOR="DarkGreen"]Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	# Power saving mode
	Option		"DPMS"
	HorizSync       30 - 110
	VertRefresh     50 - 150
	#1280x800 @ 70.00 Hz (GTF) hsync: 58.31 kHz; pclk: 98.89 MHz
	Modeline "1280x800_70.00"  98.89  1280 1352 1488 1696  800 801 804 833  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1280x800_70.00"
	EndSubSection
EndSection[/COLOR]

---

### Post by hotweiss on 2009-05-26
What's important is what is set in nvidia-settings.

Run it:

> sudo nvidia-settings

Go into X Server Display Configuration.

Now select your resolution and refresh rate.

Click Save to X Configuration File.

---

### Post by burakvarhan on 2009-05-26
> **hotweiss said:**
> What's important is what is set in nvidia-settings.

Run it:



Go into X Server Display Configuration.

Now select your resolution and refresh rate.

Click Save to X Configuration File.
Thank you very much for the reply. However, the maximum refresh rate appears to be 60Hz with Display Configuration tool. Yet I know that my hardware supports 70Hz.

Is there a workaround to do this manually instead of the tool?

---

### Post by hotweiss on 2009-05-27
If it's an LCD, the maximum refresh rate is 60. Are you sure it's 70? There is no way your notebook screen has a refresh rate of 70.

---

### Post by burakvarhan on 2009-05-28
Are you sure about this? Because right now my display preferences show that it is 70Hz and in fact my eyes are used to it because when it is 60Hz with Nvidia Driver it gets tired quickly...

---

### Post by hotweiss on 2009-05-28
> **burakvarhan said:**
> Are you sure about this? Because right now my display preferences show that it is 70Hz and in fact my eyes are used to it because when it is 60Hz with Nvidia Driver it gets tired quickly...

There are only two types of LCD refresh speeds 60 and 120 Hz. Notebooks only have 60 Hz screens.

---

