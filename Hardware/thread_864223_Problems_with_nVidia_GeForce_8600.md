---
title: "Problems with nVidia GeForce 8600"
date: 2008-07-19
forum: Hardware
---

### Post by janki on 2008-07-19
I also posted this under *General Help* a couple of weeks ago, but I wasn't able to resolve the problem with the tips I got then. So I hope somebody here can help me.

I have installed Ubuntu 8.04 on my Fujitsu-Siemens laptop. To utilize the graphics card I decided to enable it via *System* > *Administration* > *Hardware Drivers*. The graphics card I have in the laptop I found using the command *lspci*:
----
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
----

My display has a maximum resolution of 1440x900 pixels, but now the maximum resolution I can choose under *System* > *Preferences* > *Screen Resolution* is 1024x768 pixels. I was recommended to install *EnvyNG*, which correctly detects my grapchics card. It also says that my grahics card is supported by the driver. However, when I try to change the resolution in *System* > *Preferences* > *Screen Resolution* (after the recommended restart) the maximum is still only 1024x768 pixels. And it still says that my display is unknown. Isn't there somewhere in the settings where I can just enter the resolution of my display?

I appreciate any help I can get on this matter. Thanks!

---

### Post by phidia on 2008-07-19
Your xorg.conf file may need to be reconfigured for the correct rez. Hardy actually deals with xorg differently than past releases of ubuntu. Check out the newer methods [here]("https://help.ubuntu.com/community/XORGHardy").

If you open a terminal and put "sudo nvidia-xconfig" that will sometimes refind your video & monitor and create a new xorg. It should also back up your old one but if you want to be extra safe you can back it up manually.

---

### Post by janki on 2008-07-19
Thanks for your quick response!

I tried the *sudo nvidia-xconfig*-command, but this didn't change anything. From the xorg.conf-file it looks like it's the section called *Monitor* which must be changed. Mine currently looks like the following:
----
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5	-	56.0
	Vertrefresh	56.0	-	65.0
	Gamma	1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection
----

So would it work if I just added a new *modeline*? And what should the numbers after the *resolution@refresh*-rate be?

---

