---
title: "Kohjinsha 7.10 problems"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by mc_ruggiero on 2007-10-21
I have not been able to install the latest verson of Ubuntu onto my Kohjinsha. The distro boots, but it stalls when it starts to load.  Anyone have any luck?

Thanks,

Michael

---

### Post by cybrough on 2007-11-18
I had the same experience with 7.10.  7.04 works, except I don't have sound in my applications i.e flash, mp3. I do have system sounds.   I'm looking for some help here on this forum.

---

### Post by felichas on 2007-12-02
> **mc_ruggiero said:**
> I have not been able to install the latest verson of Ubuntu onto my Kohjinsha. The distro boots, but it stalls when it starts to load.  Anyone have any luck?

That's because the initial graphic configuration guess that ubuntu does for you isn't correct.

If you just want your ubuntu to start, boot once in recovery mode
*# mv /etc/init.d/gdm S30gdm /etc/init.d/gdm K30gdm*
*# init 2*

If you want to fix your xorg configuration, you will have to use the amd graphic driver and set up resolution to 800x480.
 - using the amd driver is easy because the binary comes with ubuntu
 - but 800x480 is not a standard resolution for the amd binary, and therefore we need a modeline for it.
*$ sudo vi /etc/X11/xorg.conf*
make sure you include these lines (or alike)
```
Section "Device"
	Identifier	"Geode"
	Driver		"amd"
	BusID		"PCI:0:1:1"
	Option		"Panel Geometry" "800x480"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modeline	"800x480" 31.500 800 860 940 1000 480 508 511 525 -hsync -vsync
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Geode"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection	"Display"
	Modes		"800x480"
	EndSubSection
EndSection
```
*$ startx*
If everything runs fine, you may reenable gdm in the boot process.
*$ sudo mv /etc/init.d/gdm K30gdm /etc/init.d/gdm S30gdm*

---

### Post by punong_bisyonaryo on 2008-02-25
I'm considering buying one of the SH series, the one with 600MHZ A100 Intel processor. I would like to know how it performs with Linux? Can the Intel GPU do any Beryl/Compiz?

---

### Post by tdhedengren on 2008-02-26
> **punong_bisyonaryo said:**
> I'm considering buying one of the SH series, the one with 600MHZ A100 Intel processor. I would like to know how it performs with Linux? Can the Intel GPU do any Beryl/Compiz?

I picked up a Kohjinsha with the 900 MHz version of A100 in Japan the other day. Gonna install Ubuntu on it today (unless the jetlag kills me...), so I'll post about it later on. Never done any Beryl/Compiz stuff though, but it should work, since the GPU is 945 based. Then again, I'm no expert. :)

---

### Post by punong_bisyonaryo on 2008-02-26
> **tdhedengren said:**
> I picked up a Kohjinsha with the 900 MHz version of A100 in Japan the other day. Gonna install Ubuntu on it today (unless the jetlag kills me...), so I'll post about it later on. Never done any Beryl/Compiz stuff though, but it should work, since the GPU is 945 based. Then again, I'm no expert. :)

That's cool! Tell me how it goes. I might consider buying one used since it's really cheap. And if the stars are right and a lot of the hardware works with Ubuntu, that'll be a big push for me.:)

Did I mention that it's cheap?:D

---

### Post by chewearn on 2008-02-26
I have been following another kohjinsha thread here for awhile:
[http://ubuntuforums.org/showthread.php?t=517816](http://ubuntuforums.org/showthread.php?t=517816)

It still looks like hit and miss with this baby; haven't persuade me to put in the dough to get one.

---

### Post by tdhedengren on 2008-02-27
> **punong_bisyonaryo said:**
> That's cool! Tell me how it goes. I might consider buying one used since it's really cheap. And if the stars are right and a lot of the hardware works with Ubuntu, that'll be a big push for me.:)

Did I mention that it's cheap?:D

It's a nifty little machine for sure!

Well, installed from external DVD, no problems. Mouse and sound works, wired internet connection as well, and running the Ralink build mentionend in [the other thread]("http://ubuntuforums.org/showthread.php?t=517816") made it recognize the wireless, but I haven't been able to get WPA working yet.

Ubuntu is pretty fast, lightning compared to Vista. Still a bit to go before it's fully functional though.

---

