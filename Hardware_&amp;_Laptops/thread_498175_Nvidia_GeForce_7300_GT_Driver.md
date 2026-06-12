---
title: "Nvidia GeForce 7300 GT Driver"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by narehart on 2007-07-11
Hi I have a Nvidia GeForce 7300 GT.  Right now I am running the restricted driver but was wondering if there was a better one and the best way to install it (not Automatix).

---

### Post by mcrosmar on 2007-07-11
> **narehart said:**
> Hi I have a Nvidia GeForce 7300 GT.  Right now I am running the restricted driver but was wondering if there was a better one and the best way to install it (not Automatix).

If you want to install the latest nVidia driver for your card, you can use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html").

---

### Post by narehart on 2007-07-11
Envy broke X last time I used it.

---

### Post by stchman on 2007-07-11
> **narehart said:**
> Hi I have a Nvidia GeForce 7300 GT.  Right now I am running the restricted driver but was wondering if there was a better one and the best way to install it (not Automatix).

If the restricted driver is working for you then I would stick with it.  I do.  I seriously doubt that there will be anything to gain by upgrading the driver.

---

### Post by MrMercutio on 2007-07-28
> **stchman said:**
> If the restricted driver is working for you then I would stick with it.  I do.  I seriously doubt that there will be anything to gain by upgrading the driver.

There is certainly something to gain - screen resolution. The max resolution (at least for me) is 1024x768 with the restricted drivers, but my montitor can handle 1600x1200. I'm used to that high a resolution, and I run Geforce 7300. My work process is hindered by this low a resolution because it seems I can't fit anything on screen. Hey, I'm used to the high resolutions, so don't kill me. :)

Unfortunately Envy seems to be down.

---

### Post by firmit on 2007-07-30
I had the same problem. My Acer AL1916W which supports 1600x900 was not listed. I found this link useful:
[http://answers.yahoo.com/question/index?qid=20070720171735AApY1oZ](http://answers.yahoo.com/question/index?qid=20070720171735AApY1oZ)

After completing, I was able to choose the correct resolution ( after reboot ).

Edit: I have the 7300GS.

---

### Post by MrHippocampus on 2007-07-30
You should easily be able to change the resolution of any nvidia card using the display configuration section of nvidia-settings (as long as your monitor is giving out correct EDID information that is...).

---

### Post by stchman on 2007-07-31
> **MrMercutio said:**
> There is certainly something to gain - screen resolution. The max resolution (at least for me) is 1024x768 with the restricted drivers, but my montitor can handle 1600x1200. I'm used to that high a resolution, and I run Geforce 7300. My work process is hindered by this low a resolution because it seems I can't fit anything on screen. Hey, I'm used to the high resolutions, so don't kill me. :)

Unfortunately Envy seems to be down.

The restricted driver is capable of doing 1600x1200.  Just edit your /etc/X11/xorg.conf file and add "1600x1200" in the line of resolutions.  I had to do this on my 7600GT equipped system to get the native 1280x1024 for my LCD.

---

### Post by SpikoPath on 2007-08-04
> **stchman said:**
> The restricted driver is capable of doing 1600x1200.  Just edit your /etc/X11/xorg.conf file and add "1600x1200" in the line of resolutions.  I had to do this on my 7600GT equipped system to get the native 1280x1024 for my LCD.

Thanks for this one, this sorted the problem

I've entered the code to copy and paste below, just copy and paste the "Mode" sections

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
```

Bring up a terminal window and type this

```
sudo gedit /etc/X11/xorg.conf
```

gedit is my text editor replace the gedit with the binary file name of the text editor that you are using.

---

### Post by Lord Shank on 2007-08-06
*sudo dpkg-reconfigure xserver-xorg*

Type that in terminal, and follow the steps.

Cheers

---

