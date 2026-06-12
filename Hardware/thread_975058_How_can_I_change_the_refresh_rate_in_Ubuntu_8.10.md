---
title: "How can I change the refresh rate in Ubuntu 8.10"
date: 2008-11-08
forum: Hardware
---

### Post by _asc_ on 2008-11-08
Hello,

I have Ubuntu 8.10, an nVidia 6600GT graphics card and a Sony Multiscan G200 CRT. The monitor is not detected and so I'm stuck with a refresh rate of 60Hz (screen resolution settings show 50Hz, but nVidia settings and the monitor's info menu show 60Hz). I have already checked the xorg.conf file, but there is no information regarding screen resolution and refresh rate anymore. Since everything is supposed to be autodetected in the new Xorg version, I don't even know if changes to the xorg.conf file have any effect.

I would like to have a refresh rate of at least 85Hz. Can anybody help me with this problem?

---

### Post by m_l17 on 2008-11-08
Please post your /etc/X11/xorg.conf

---

### Post by _asc_ on 2008-11-08
**_My xorg.conf:_**

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by m_l17 on 2008-11-08
Give this a try:

Make a backup of your xorg.conf:

```
$ cd /etc/X11/

$ sudo cp xorg.conf xorg.conf.orig
```

You can name the backup whatever you like I just like to use .orig for original.

Add these lines to your xorg.conf, in the Section Monitor below Identifier:
        HorizSync       30-81
        VertRefresh     60

Very important make sure you use your monitor's specs only


Add theses lines to your xorg.conf, in the Section Screen below  DefaultDepth :

        SubSection      "Display"
        Depth           24
        Modes           "1920x1200_60"
        EndSubSection

Modes = resolution-you-would-like-to-use_refresh-rate-you would-like-to-use

example:
```
Section "Monitor"
	 Identifier	"Configured Monitor"
        [COLOR="Red"]HorizSync       30-81 <----- change for your monitors specs
        VertRefresh     60    <----- change for your monitors specs[/COLOR]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
       [COLOR="Red"]SubSection      "Display"
       Depth           24
       Modes           "1280x1024_85" <--- change to desired resolution and refresh rate
       EndSubSection[/COLOR]
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Then do:
```
$ sudo nvidia-settings
```

Then from X Server Display Configuration select the resolution, you previously used above 1280x1024 and refresh of 85hz.

Saving the X configuration File [while nvidia-settings is still open]:

$ sudo rm /etc/X11/xorg.conf

save file as /etc/X11/xorg.conf

reboot

If the above does not work for you you change everything back by:

```
$ sudo cp xorg.conf.orig xorg.conf
```

---

### Post by _asc_ on 2008-11-09
Hello m_l17,

I tried what you suggested and it worked! Thank you very much!

---

### Post by m_l17 on 2008-11-09
No problem I'm glad it worked :D

---

### Post by umzRV on 2008-12-01
I'd also like to add and say THANK YOU THANK YOU THANK YOU it finally worked. I've been dying to get out of 640x480!!! You sir, are a true hero.

---

### Post by m_l17 on 2008-12-01
> **umzRV said:**
> I'd also like to add and say THANK YOU THANK YOU THANK YOU it finally worked. I've been dying to get out of 640x480!!! You sir, are a true hero.

Your welcome and glad it helped :D

---

### Post by Weissbier on 2008-12-02
> **umzRV said:**
> I'd also like to add and say THANK YOU THANK YOU THANK YOU it finally worked. I've been dying to get out of 640x480!!! You sir, are a true hero.

I have solved it similar by letting it creating a new default x.conf file, which obviously activates/re-detect all possible screen-resotuins/refresh-rates of your screen at reboot.

[http://ubuntuforums.org/showpost.php?p=6290006&postcount=2](http://ubuntuforums.org/showpost.php?p=6290006&postcount=2)

Also my keyboard is now german again.

---

### Post by caravel on 2008-12-24
I was having a spot of bother with my CRT monitor not being detected, now all is ok thanks to the clear and concise info you have posted.

Many thanks

Caravel

---

### Post by hunbalu on 2009-02-26
Dear m_l17,

Could you please try (or do) help me as well?
I have an Ati Radeon X600Pro videocard and an Eizo F730 monitor.
Ubuntu recognizes my videocard but the monitor is unknow so I can't change the refresh rate so it is the base 60Hz.
By the monitor's spec. it could be 107Hz on 1280*1024 but it would be enough to have 100Hz on 1152*864

Thanks in advance,
Balu

My /etc/X11/xorg.conf is the following:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

---

### Post by ncr2k9 on 2009-04-08
I have a GeForce 6150SE embedded graphics chip and even though I've tried everything I still can't solve the problem of the resolution re-setting after login.

I set it to 1680x1060 @ 60hz and it looks ok on the login screen but afterwards it always re-sets to 1280x1024 @ 75hz. 

If I open system > preferences > screen resolution it looks really bad, I get really weird refresh rate options for 1680x1050, 50, 51, 52 and 108 hz. That can't be right because I have a Dell 228WFP 22" LCD monitor, and I'm sure max resolution is 1680x1050 @ 60hz. I dare not play with those settings, the nvidia-settings panel on the other hand seems to recognize everything properly.

I'd really appreciate any ideas or comments someone may have, I'm kind of new with Ubuntu. 

Thanks.

---

### Post by AKK9 on 2009-06-11
Wait, why don't you just change the settings in the GUI and then click Save Config before you apply?

That seems to work.

---

