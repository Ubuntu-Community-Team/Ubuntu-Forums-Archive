---
title: "Inspiron 1100 Graphics Issues"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by ebullient on 2007-10-19
Hi and thanks for looking.

I'm trying to install 7.10 final on an old Inspiron 1100.  It has 256MB and the Intel 845GL.  It's on loan from my folks for school work so I don't have much choice.

So here's my problem.  I've tried several different versions of Ubuntu and even tried Gentoo and I either got bad screen corruption or was forced into 640x480.  Perusing the internets I finally realized that the bios was pretty outdated and it wouldn't even let me change the video memory like some sites suggested.  So I updated it to A32 which is the most current.  Now I can increase it all the way to 8MB.  I was able to do alt-text install at full-screen, which was encouraging.  However, I still get screen corruption, only now I can actually see a dialog telling me Ubuntu will be running in low graphics mode and you have to configure it yourself if you want anything better and oh, would you like to configure or just login sir?  I've tried configuring it manually using this dialog, that doesn't work.  I've tried clicking through to low graphics mode and that doesn't work.  I get a screen full of vertical blue lines, and sometimes just plain screen corruption (pretty looking gradients that usually indicate your video card is fried).  The gdm sound plays, taunting me.  I can even login in blindly and hear the gnome startup sound, all the while getting occasional artifacts that give tantalizing glimpses of what I want to see.

Here's the kicker.  If I attach an external monitor when I load, I get perfect performance.  7.10 loads all the way into gnome, compiz-fusion is working at the middle setting, and it's running everything at 1280x1024 (I've saved the xorg.conf that does this and reload it whenever I want to fiddle in the gui).  From that I believe that it can't be the video card, it has to be how it's seeing my laptop display.  I've loaded up the nifty new screens and graphics gui and tried to enable it using that method and I always get the same results.

Looking at the logs it seems that when I leave it to load from ye-old laptop panel (and the associated xorg.conf) it fails.  Then it loads from xorg.conf.failsafe which doesn't work (it uses the vesa driver).  So here's the pertinent info:

Relevant sections from my xorg.conf:
```
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"intel"
	VideoRam 	32768
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	31.5-50.0
	VertRefresh	40-90
	Option          "UseEdidFreqs" "1"
	#Option		"DPMS"
EndSection
```

Interesting errors from /var/log/Xorg.0.log.old:
```
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(EE) intel(0): detecting sil164
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(EE) intel(0): Unable to read from DVOI2C_E Slave 236.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(EE) intel(0): ivch: Unable to read register 0x00 from DVOI2C_B:04.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): detecting tfp410
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(EE) intel(0): tfp410 not detected got VID FFFFFFFF: from DVOI2C_E Slave 112.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output VGA disconnected
(EE) intel(0): No valid modes.
```

Thanks for your time and help.  I've been googling and installing and configuring for like three days, so hopefully someone knows what I need to do.

I don't recall all the sites and threads I've seen, but I did try [http://ubuntuforums.org/showpost.php?p=1799642&postcount=15](http://ubuntuforums.org/showpost.php?p=1799642&postcount=15) with no luck.

---

### Post by ebullient on 2007-10-20
Well, it works if you use the vesa driver.  Not exactly an optimal solution but I guess it will tide me over till the intel driver comes into its own.

I still don't get why I can run it just fine on an external monitor at 1280x1024 using the intel driver and yet to run it on the builtin laptop panel I have to switch to the vesa driver.  Gr.

---

### Post by ceng1984 on 2007-10-20
ebullient,

I also have a Dell Inspiron 1100. I now have 7.10 installed. The graphics are working ok, so far. I have used this machine with 6.06 and 7.04. I did have to work at getting the correct resolution working. In my machine this is 1024x768 and I believe it is this for any 1100.  I'm no expert, but my understanding of LCD monitors is the proper setup (fewest problems) comes with using the native resolution for the screen.The original docs with this machine and all info I found online stated 1024x768 is the correct resolution. Try setting this.  Good luck.

ceng1984

---

### Post by ebullient on 2007-10-21
ceng1984 what bios version are you running?

Anyway, yes, I have been using 1024x768 for my laptop panel.  To clarify, I have a separate xorg.conf that works with my external monitor at 1280x1024 and one that works with my laptop display panel at 1024x768.  This is unnecessary, but I have two decently configured xorg.conf's that get results so I haven't messed with it.  The only difference between the two is the monitor section, one describing my external monitor and the other my laptop display panel.

So yes, I've set it to 1024x768 and it simply does not work unless I change the driver section to 'vesa'.  I've even run it on my external monitor at 1024x768.

To summarize:

Display runs on 1280x1024 external monitor with the 'intel' driver and desktop effects.

Display runs on 1024x768 internal display with the 'vesa' driver and no effects (I haven't bothered to test the effects).

Each of these displays have their own xorg.confs that I manually switch between using the command line, and each xorg.conf has the native resolution of its particular screen set in it.  I don't see any reason why I can't use the 'intel' driver with the internal display but I simply can't as far as I've seen.  I dearly want to, the vesa driver doesn't seem up to the same quality.

Thanks for the effort though.

---

### Post by superatrain on 2007-10-24
How about the SVIDEO port? Has anybody had any luck getting TV out to work?

Also, there is an app called i810switch. Supposed to switch between CRT and LCD. I haven't been able to get it working though, but I'm being stubborn and only trying the i810 drivers (NO VESA!)

Avoid the vesa driver if you can... basic things like scrolling down a basic html firefox page is really, really laggy...

---

### Post by walshf on 2007-10-26
Using two Toshiba Satellite 1100-S101laptops each with 512 MB I was able to execute from CD & install earlier versions of Ubuntu & Kubuntu ( <= 6.10 )

Using these Toshiba Satellite 1100-S101 with 512 MB I was able to execute from CD & install Ubuntu & Kubuntu ( 7.10 BETA  )

Using these Toshiba Satellite 1100-S101 with 512 MB I was unable to execute from CD or  install earlier versions of Ubuntu & Kubuntu ( 7.10 downloaded on 10/18/07 )
Symptom  - screen blanks soon ( a line or two ) after loading Gnome.  No cursor visible, but LCD backlight seems to be on, just no pixels illuminated.

It appears that this problem was introduced just before 7.10 was released, due to ??

perhaps the problem can be quickly isolated & corrected by reviewing the changes between the 7.10 BETA and the official release of 7.10

I did not attempt to obtain or to test the 7.10 release candidate of Unbuntu

Rick

---

### Post by ebullient on 2007-10-27
walshf what bios version do you have?  Have you increased the video memory in the bios?  Have you tried installing from an alternate cd and running it?

---

