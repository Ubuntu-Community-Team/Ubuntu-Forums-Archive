---
title: "Xorg 19&quot; Widescreen Issues"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by linuxteen15 on 2008-02-18
Helllo,

I am trying to connect my new Acer x193w 19" Widescreen monitor to my computer running Kubuntu Gutsy. My graphics card is an integrated intel 915. I am needing to set my resolution to 1440x900@60Hz.

I have tried multiple combinations of using the system settings option

I have tried running dpkg-reconfigure xserver-xorg but I get to the point about color depth and it kicks me out giving this:
```
mike@mikeg2:~$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080218175743
```

I am currently stuck with 1024x768 which of course is distorted

Sorry,  I realize this issue has been answered already (somewhat)
Any help would be appreciated

---

### Post by Yellow Pasque on 2008-02-19
Common problem, there's a tool to fix it.
```
sudo apt-get install 915resolution
```
See this page for instructions/info:
[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

---

### Post by linuxteen15 on 2008-02-19
OK I have tried that now, but it doesn't seem to be doing anything different, I'm probably doing something wrong though.

My settings after doing this in the system settings show that I am running 1440x900@60Hz, but my display is off-center and compressed. I did not see any changes from using 915resolution. 

Do you have any further advice on this? I have successfully gotten this monitor running on windows(dual-boot - 1440x900,75Hz, 32depth)

---

### Post by Oreo on 2008-03-20
I hope someone answers this. I have 915 resolution installed. I can run at 1280x800 mode, but running at 1440x900 causes a black bar on the left side of the screen about and 1 and half wide. (unused area) The part that is used becomes very sharp, but I wish it would go across the screen.

Oreo

---

### Post by tyyp88 on 2008-03-20
> **Oreo said:**
> I hope someone answers this. I have 915 resolution installed. I can run at 1280x800 mode, but running at 1440x900 causes a black bar on the left side of the screen about and 1 and half wide. (unused area) The part that is used becomes very sharp, but I wish it would go across the screen.

Oreo

I have a solution for that. First of all, you need to add **modeline** into your xorg.conf file.

You can get the modeline into xorg.conf automatically when you install drivers for your monitor. Get your drivers from CD or in monitor manufacture website.

In my case xorg.conf file:

```
Section "Monitor"
	Identifier	"SyncMaster"
	Vendorname	"Samsung"
	Modelname	"SyncMaster 932GW"
	Option		"DPMS"
	Horizsync	30-81
	Vertrefresh	56-75
	**modeline  	"1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync** 
EndSection
```

**Now REBOOT**

After that open terminal and type:

```
$ xrandr
```

There should now avaible mode smth. like 1440x900@60

And type in:

```
$ xrandr --output VGA --mode 1440x900@60

```

And the black bars are gone :)

---

### Post by Yellow Pasque on 2008-03-20
The quickest/easiest way to get a modeline is with cvt
```
cvt -v 1440 900 60.0Hz
```

---

### Post by Oreo on 2008-03-20
Thanks so much, Tyyp88 and Temüjin!

That worked!

The first time when I did the cvt command and copied the result, I didn't notice that the result had an underscore instead of an @ sign.
So when I pasted it into the Monitor section my xorg.conf file, it didn't work.

I added the 1440x900 resolution to the Modes in the Screen section as well. 

Thanks so much or helping me!

Oreo

---

### Post by linuxteen15 on 2008-03-28
Thank you this worked for me as well

However, when I reboot, the settings are gone and I have to run the command again. What is the best way that I can get this accomplished at boot/KDE startup?

---

### Post by tlm884 on 2008-03-28
Hey, 

I have done this and now the monitor is showing up properly but It still won't go to the proper resolution (1440 X 900) It is in the modeline and the mode in my xorg.conf and i did xrandr and it does not appear as an available mode.

Taylor

---

