---
title: "Ati Radeon HDMI out to Television"
date: 2012-03-20
forum: Hardware
---

### Post by Deten on 2012-03-20
Hei,

I have a 1080P television which I connected my computer to.  I am using the default open source Radeon drivers.

The output is only 1080i to my TV and I want to know how I can adjust either xorg or KMS to output 1080P.

Thanks
Deten

---

### Post by Grenage on 2012-03-20
I believe that an xorg mordeline (without the interlace option) should give you a 1080p output.

---

### Post by Deten on 2012-03-20
Well the default output is 1080i as my TV detects and tells me.

Can you point me to how to adjust this setting in xorg mordeline?

Thanks!

---

### Post by Grenage on 2012-03-20
I have a general guide [here]("http://www.grenage.com/xorg.html"), and a modeline is added halfway down.  do you already have an xorg.conf? If so, you can post it here if you get stuck.

---

### Post by Deten on 2012-03-20
Based on this page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
there is no xorg.conf by default for the open source radeon driver, instead using KMS.

Would a pre-requisite for your instructions include disabling KMS?

As of now I haven't done anything to use a xorg.conf

**Edit** After looking at your link, it appears your first step is setting up xorg.conf :)

---

### Post by Grenage on 2012-03-20
That's right; if you have an xorg.conf - it will get used.  Generally, the most complicated part of creating a config is getting the vert/horiz rates, which the proprietary driver (which uses xorg.conf) generally grabs via EDID data.  You're using the open driver, but you can still normally attain the rates.

A modeline effectively negates the *need* for rates, but it's always nice to have a more complete config.

---

### Post by Deten on 2012-03-20
So, should I just manually create the xorg.conf file, or is there a command I should use in terminal to generate the file?

11.10 naturally

---

### Post by Grenage on 2012-03-20
Bingo, here's a template; I've left out the frequencies, as I don't know your TV make and model:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "unxnown"
	ModelName "unknown"
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
#Modeline "1920x1080_50.00"  141.50  1920 2032 2232 2544  1080 1083 1088 1114 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nouveau"
	VendorName "ati"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1920x1080"
	EndSubSection
EndSection
```

I've added two modelines, with one commented out; the uncommented modeline is for 60hz, and the commented section is for 50.  If the config fails, you could try commenting out the first modeline, and uncommenting the second.

Have an Ubuntu CD handy, so you can easily delete the config if something goes wrong (or you could log in via the terminal).

To use the config above:

```
gksu gedit /etc/X11/xorg.conf
```

Then copy and paste in the text, save, and reboot.

---

