---
title: "Precise Pangolin with ATI Radeon - Open Source vs Proprietary Driver"
date: 2012-04-27
forum: Hardware
---

### Post by Lamukra on 2012-04-27
Hallo!

I jsut moved from oneiric to precise and wondering if I should continue using Open Source ATI driver or should I start using Proprietary Driver for my ATI card

Any suggestion or anyone there already tried this one?

---

### Post by Lemuriano on 2012-04-27
As I understand default Unity and Gnome Shell used 3D and the proprietary drivers offer that capability.  But you can use Unity 2D with the free drivers.

Regards.

---

### Post by coffeecat on 2012-04-27
> **Lemuriano said:**
>  But you can use Unity 2D with the free drivers.


You can use Unity 3d with the open source drivers with many, if not most, ATI Radeon cards.

@Lamukra, which ATI card do you have? I find the default open source driver gives me Unity 3d and all I need with the HD4350, HD5450 and HD6450 cards. Gamers might need the proprietary driver, but otherwise the open source one should be good.

---

### Post by TBABill on 2012-04-27
I have experienced much lower heat levels with the proprietary driver versus the open source driver. That alone sold me on the proprietary driver for a laptop because it runs cooler, which extends battery life as well.

---

### Post by coffeecat on 2012-04-27
Yes, I've read about the heat levels, which would certainly be a consideration with laptops. Those 3 GPUs I mention are all PCIe cards and passively cooled moreover - no fan. In a compact micro-ATX case they run at about 75 Celsius with the OS driver. Hotter than I would like but not a problem

---

### Post by Lemuriano on 2012-04-27
[QUOTE=coffeecat;11879088]You can use Unity 3d with the open source drivers with many, if not most, ATI Radeon cards.

Thanks for clarifying!

---

### Post by Lemuriano on 2012-04-27
> **coffeecat said:**
> You can use Unity 3d with the open source drivers with many, if not most, ATI Radeon cards.

Thanks for clarifying!

---

### Post by Lamukra on 2012-04-27
> **coffeecat said:**
> You can use Unity 3d with the open source drivers with many, if not most, ATI Radeon cards.

@Lamukra, which ATI card do you have? I find the default open source driver gives me Unity 3d and all I need with the HD4350, HD5450 and HD6450 cards. Gamers might need the proprietary driver, but otherwise the open source one should be good.

I am using ATI Radeon HD 5650 1GB With 1 GB dedicated and up to 2740 MB Shared memory on My Sony Vaio VPCEB1S1E

Open Source was always giving me better performance on this Laptop, dunno about precise yet, that is why I am asking. Right now tried Xorg-Edgers with Open Source it gives me some tearing like in Software center for ex. top icons are totally teared off, but without xorg they are OK and not tearing at all. Of course I have Xorg.conf configured as well for open source and not for proprietary. Good point about heat levels as well. This is an issue I have to deal with as well. Dunno yet how.

If I would like to install proprietary driver is it better to do through Ubuntu additional drivers activation or through downloading latest from amd?

Right Purging Xorg-Edgers PPA and reverting to Originally installed, going to try with proprietary through Ubuntu's additional drivers activation!

---

### Post by Lamukra on 2012-04-27
Need Some help here! Take a look on what I have after installing FGLRX through ubuntu repos, with Jockey


```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.556] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    21.599] (WW) Falling back to old probe method for fglrx
[    21.749] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    21.825] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    22.048] (WW) fglrx(0): Option "VendorName" is not used
[    22.048] (WW) fglrx(0): Option "ModelName" is not used
```

---

### Post by Lamukra on 2012-04-27
```
fglrxinfo
```


```
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 5000 Series 
OpenGL version string: 4.2.11627 Compatibility Profile Context

```

---

### Post by Lamukra on 2012-04-27
```
lspci -nn | grep VGA
```

```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series] [1002:68c1]

```

---

### Post by Lamukra on 2012-04-27
If Ia going to System Settings -> Details -> Graphics

I see there Driver VESA:MADISON and Experience Standard

---

### Post by galerie on 2012-04-30
I upgraded from oneiric to precise yesterday morning, and cannot use 3D version of unity and got hang and freeze sometimes when startup and shutdown.

Just now I finished reinstalling my laptop with fresh install of precise but still experience same problem. 
still sad bout' that. 

Still trying now. there's some written posted during startup before ubuntu logo with loading sign...
still trying to read it, cause it happen so fast.

before I do another trial and error I would love and listen carefully to any advice from all of the forum member.

FYI... my laptop spec is :
Dell inspiron 14R N4010
core i5
my VGA ati radeon 550v (if I could remember correctly) recognized as radeonHD 4650 when I used oneiric with proprietary driver before

I will provide any more information if needed. just tell me and I will let you know.
tnx before for any respond and pardon me for my bad spelling and grammar.

---

### Post by Lamukra on 2012-04-30
> **galerie said:**
> I upgraded from oneiric to precise yesterday morning, and cannot use 3D version of unity and got hang and freeze sometimes when startup and shutdown.

Just now I finished reinstalling my laptop with fresh install of precise but still experience same problem. 
still sad bout' that. 

Still trying now. there's some written posted during startup before ubuntu logo with loading sign...
still trying to read it, cause it happen so fast.

before I do another trial and error I would love and listen carefully to any advice from all of the forum member.

FYI... my laptop spec is :
Dell inspiron 14R N4010
core i5
my VGA ati radeon 550v (if I could remember correctly) recognized as radeonHD 4650 when I used oneiric with proprietary driver before

I will provide any more information if needed. just tell me and I will let you know.
tnx before for any respond and pardon me for my bad spelling and grammar.

could you please post output of this
```
lspci -nn | grep VGA
```

and this

```
cat /var/log/Xorg.0.log | grep EE

```

and this

```
cat /var/log/Xorg.0.log | grep WW

```

---

### Post by Lamukra on 2012-04-30
Ou... Do you know precisely what is model of your video card ???

---

### Post by galerie on 2012-04-30
> **Lamukra said:**
> could you please post output of this
```
lspci -nn | grep VGA
```and this

```
cat /var/log/Xorg.0.log | grep EE

```and this

```
cat /var/log/Xorg.0.log | grep WW

```
pardon me for the late answer cause it's already 4.00 AM in my country  now. been sleeping while searching answer for my problem :D

tnx for u'r fast respond.
these are results codes u'd provided
```
cat /var/log/Xorg.0.log | grep EE

```
```
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI M96 [Mobility Radeon HD 4650] [1002:9480]
```
```
cat /var/log/Xorg.0.log | grep EE

```
```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.957] (II) Loading extension MIT-SCREEN-SAVER
[    21.014] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    21.072] (EE) Failed to load module "fglrx" (module does not exist, 0)
```
```
cat /var/log/Xorg.0.log | grep WW

```
```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.883] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.883] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.884] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.885] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.885] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.885] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    21.014] (WW) Warning, couldn't open module fglrx
[    21.072] (WW) Warning, couldn't open module fglrx
[    21.076] (WW) Falling back to old probe method for vesa
[    21.076] (WW) Falling back to old probe method for fbdev
[    22.988] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
```
> **Lamukra said:**
> Ou... Do you know precisely what is model of your video card ???
if I remember correctly, maybe wrong :D
my Graphic card is ati radeon HD 550v (recognized as radeon HD 4650 when I used proprietary driver on oneric)
any other information needed just ask :D
tnx for every advice

---

### Post by Lamukra on 2012-04-30
> **galerie said:**
> pardon me for the late answer cause it's already 4.00 AM in my country  now. been sleeping while searching answer for my problem :D

tnx for u'r fast respond.
these are results codes u'd provided


Well, it seems the same problem that I had in the beginning just with another card. Your machine does not have FGLRX module installed. I recommend to install it with help of amd.com page. Download driver for your card from there and install it.
After you will install it run commmand 

```
aticonfig --initial
```

It will create xorg.conf file in your /etc/X11 folder

After you can tweak it as you wish.

BUT

Don't rush with this solution. Think first and try with Open-Source driver first, you might get better performance with that than with proprietary driver. I installed proprietary driver because I had trouble with heat level and fan speed in Precise more than I had previously. Fan was going crazy and laptop heating like hell, you could almost fry on it. In previous version of Ubuntu I did not have so much trouble with heat levels when I used open-source ATI driver, buy in Precise it got crazy and proprietary driver installation saved me big time. But not installing it from Jockey(Additional Driver in System Settings) but through amd.com download page and installing it manually.
So I will recommend you to use radeon driver for your card first, then if it will not work you try fglrx...

---

### Post by Lamukra on 2012-04-30
Here is my xorg.conf for my ATI Radeon HD 5650 that I always used with my card and had a great 3D performance, much better than with fglrx. Copy Paste it into /etc/X11/xorg.conf. If you don't have one create one.

```

Section "ServerLayout"
	Identifier     "DualHead"
	Screen      0  "LaptopScreen"
EndSection

Section "ServerFlags"
	Option	"AIGLX" "on"
EndSection

Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "dbe"
	Load  "glx"
	Load  "type1"
	Load  "freetype"
	Load  "record"
EndSection

Section "Device"
	Identifier	"ATI Radeon HD 5650"
	Driver		"radeon"
	Option		"EXAVSync" "True"
	Option		"ColorTiling" "on"
	Option		"RenderAccel" "true"
	Option          "EnablePageFlip" "true"
	Option 		"DRI" "true"
	Option		"AccelMethod" "EXA"
	Option          "Monitor-LVDS" "Left Monitor"
	BusID       	"PCI:1:0:0"
	Option          "Monitor-LVDS" "VaioLCD"
        Option          "Monitor-HDMI-0" "BraviaLCD"
	Option		"IgnoreEDID" "true"
	Screen		0
EndSection

Section "Monitor"
	Identifier   "VaioLCD"
	Option 	     "DPMS"
EndSection

Section "Monitor"
	Identifier   "BraviaLCD"
	Option 	     "DPMS"
EndSection

Section "Screen"
	Identifier "LaptopScreen"
	Device     "ATI Radeon HD 5650"
	Monitor    "VaioLCD"
	DefaultDepth    24
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group "video"
	Mode 0666
EndSection

Section "Extensions"
	Option	"Composite" "Enable"
	Option	"RENDER" "Enable"
	Option	"RANDR" "Enable"
	Option	"DAMAGE" "Enable"
	Option  "GLX" "Enable"
EndSection

```

After you created it, restart the machine and if you will fail to boot then boot into root shell from recovery menu and

```
rm /etc/X11/xorg.conf
```

reboot again

If you will succeed to boot then post the output of commands again

```
cat /var/log/Xorg.0.log | grep EE

```
```
cat /var/log/Xorg.0.log | grep WW
```

---

### Post by galerie on 2012-04-30
> **Lamukra said:**
> Well, it seems the same problem that I had in the beginning just with another card. Your machine does not have FGLRX module installed. I recommend to install it with help of amd.com page. Download driver for your card from there and install it.
After you will install it run commmand 

```
aticonfig --initial
```It will create xorg.conf file in your /etc/X11 folder

After you can tweak it as you wish.

BUT

Don't rush with this solution. Think first and try with Open-Source driver first, you might get better performance with that than with proprietary driver. I installed proprietary driver because I had trouble with heat level and fan speed in Precise more than I had previously. Fan was going crazy and laptop heating like hell, you could almost fry on it. In previous version of Ubuntu I did not have so much trouble with heat levels when I used open-source ATI driver, buy in Precise it got crazy and proprietary driver installation saved me big time. But not installing it from Jockey(Additional Driver in System Settings) but through amd.com download page and installing it manually.
So I will recommend you to use radeon driver for your card first, then if it will not work you try fglrx...
tnx Lamukra
after upgrading I tried to use catalyst 12.4 from amd websites but no success. I experienced problems I mentioned before.
now I want to try the open source. could you tell me how to install it correctly cause I have read askubuntu about this but still cant figure the right way. or any link to the tutorial how to install radeon driver for my graphic?
cause I only know basic things bout computer.

I tried the tutorial from [this link]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide") for installing the proprietary driver
but failed.
first time I tried it have error that mentioned about DKMS (I forgot the exact info) but i got 2 error
[]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide")

---

### Post by Lamukra on 2012-04-30
Don't pay attention on names right now in xorg.conf file, this file should work with your system as well, just don't make any mistake in xorg.conf or you will get parse error in there (like forgot to close quotes or wrong section closing)

---

### Post by Lamukra on 2012-04-30
> **galerie said:**
> tnx Lamukra
after upgrading I tried to use catalyst 12.4 from amd websites but no success. I experienced problems I mentioned before.
now I want to try the open source. could you tell me how to install it correctly cause I have read askubuntu about this but still cant figure the right way. or any link to the tutorial how to install radeon driver for my graphic?
cause I only know basic things bout computer.


Check, I posted it above your last post :)... Your radeon driver is already installed in system, you just have to make use of it now with help of xorg.conf file which you should create in /etc/X11 folder

---

### Post by Lamukra on 2012-04-30
> **galerie said:**
> tnx Lamukra
after upgrading I tried to use catalyst 12.4 from amd websites but no success. I experienced problems I mentioned before.

Did you run this command after installing Catalyst Driver????

```
aticonfig --initial
```

This command creates xorg.conf file to make use of your installed driver??? It is very important

---

### Post by galerie on 2012-04-30
pardon me for missing your post. :D

it seems I experienced heat problem like yours 
now I'm trying to install catalyst again, I will read the tutorial more carefully this time.
I will post the result when it is done.
hope this time I will success
tnx Lamukra you are such a big help for me. :D

---

### Post by Lamukra on 2012-04-30
You are very welcome, it is my pleasure to help, I was some days back on your place and was searching for help as well, totally understand you! :)

---

### Post by galerie on 2012-04-30
Hi Lamukra
Tnx for all your guide
now I am finally installed catalyst 12.4
but I have same message as your posting in page 1
```
lspci -nn | grep VGA

02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI M96 [Mobility Radeon HD 4650] [1002:9480]
```
```
cat /var/log/Xorg.0.log | grep EE
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   577.293] (II) Loading extension MIT-SCREEN-SAVER
```
```
cat /var/log/Xorg.0.log | grep WW
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   577.291] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   577.291] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   577.313] (WW) Falling back to old probe method for fglrx
[   577.332] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[   577.373] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[   577.980] (WW) fglrx(0): Option "VendorName" is not used
[   577.980] (WW) fglrx(0): Option "ModelName" is not used
[   578.542] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
```

when I see in System settings>Details>graphic>VESA:M96
is it okey or not?

---

### Post by Lamukra on 2012-04-30
> **galerie said:**
> Hi Lamukra
Tnx for all your guide
now I am finally installed catalyst 12.4
but I have same message as your posting in page 1
```
lspci -nn | grep VGA

02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI M96 [Mobility Radeon HD 4650] [1002:9480]
```
```
cat /var/log/Xorg.0.log | grep EE
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   577.293] (II) Loading extension MIT-SCREEN-SAVER
```
```
cat /var/log/Xorg.0.log | grep WW
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   577.291] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   577.291] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   577.313] (WW) Falling back to old probe method for fglrx
[   577.332] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[   577.373] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[   577.980] (WW) fglrx(0): Option "VendorName" is not used
[   577.980] (WW) fglrx(0): Option "ModelName" is not used
[   578.542] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
```

when I see in System settings>Details>graphic>VESA:M96
is it okey or not?

For now it is perfectly normal, as I am trying to solve this **** now by myself as well, I have VESA:MADISON in the same place where you have M96. I asked guys about this maybe problem in this thread

[http://ubuntuforums.org/showthread.php?p=11892923#post11892923](http://ubuntuforums.org/showthread.php?p=11892923#post11892923)

But I can help you with some other lines, I mean to get rid of them, lets start

Find and install these packages

xfonts-cyrillic
xfonts-100dpi
xfonts-75dpi

in order for these line to go away

```
[   577.291] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   577.291] (WW) The directory "/usr/share/fonts/X11/75dpi"
```

Then ALT+F2 --> gksu nautilus
Then go to /etc/X11 and open xorg.conf
Find monitor section and delete the lines which begin with

```
Option "VendorName"
Option "ModelName"
```

save document and close, this will make these lines to go away

```
[   577.980] (WW) fglrx(0): Option "VendorName" is not used
[   577.980] (WW) fglrx(0): Option "ModelName" is not used
```

After all this restart, and lets wait for response in thread above about  these lines

```
[   577.313] (WW) Falling back to old probe method for fglrx
[   577.332] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[   577.373] (WW) fglrx(0): board is an unknown third party board, chipset is supported
```

I don't know what to do about this line

```
[   577.291] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
```

and as well this line

```
[   578.542] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
```

It is probably connected with your USB Mouse that is attached to you laptop but it is not that serious and for now we may ignore it if everything works :)

---

### Post by galerie on 2012-04-30
well since you are facing same problem and made a new thread than I may have to follow you to that thread :D
yes you are right bout the last two lines it is told bout my mouse and keyboard that attached to a USB Hub :D
let's move to your thread 
great thanks

---

### Post by Lamukra on 2012-04-30
> **galerie said:**
> well since you are facing same problem and made a new thread than i may have to follow you to that thread :d
yes you are right bout the last two lines it is told bout my mouse and keyboard that attached to a usb hub :d
let's move to your thread 
great thanks

very welcome!!!

---

