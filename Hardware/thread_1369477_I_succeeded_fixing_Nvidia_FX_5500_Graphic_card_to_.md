---
title: "I succeeded fixing Nvidia FX 5500 Graphic card to 1024x768 display"
date: 2010-01-01
forum: Hardware
---

### Post by haradeep on 2010-01-01
This one works for both ubuntu 9.04, 9.10 and kubuntu 9.04, 9.10.

Hi all,

I'm having Nvidia FX 5500 Graphic card.

I will tell you how to configure it to 1024x768 display.

1)Version Of Ubuntu: ubuntu version 9.04,9.10 and kubuntu 9.04, 9.10.
2)Type Of Hardware: Graphic card
3)Hardware Maker: Nvidia
4)Hardware Model: FX 5500

I will tell you in a detailed way.

After installation of ubuntu open

System-> Administration-> Hardware drivers

You will find two drivers to install.

NVIDIA accelerated graphic drivers(Version 173)[Recommended]
NVIDIA accelerated graphic drivers(Version 96)

Select version 96 and activate it. It takes some time to download, install, get activated and asks for reboot.

Reboot your system...

After rebooting it, it sets 640x480 display.

Open terminal

Applications-> Accessories-> Terminal 

In terminal type 
```
sudo gedit /etc/X11/xorg.conf
```
enter your password for authentication and open it.

In this file you will find data like this.

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

Replace above data with below data.

```
# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHzModeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

Section "Monitor"
    Identifier    "CM752ET"
    HorizSync     31-101
    VertRefresh    60-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768_75.00"
    EndSubSection
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

Reboot your system. You will get 1024x768 display in login page.

If you did not get 1024x768 display

Go to 

System-> preferences-> Display

and you will get a window asking...

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

Enter [No]

You can set your resolution there to 1024x768
______________________________________________________________

Other way to set resolution is 

Go to 

System-> Administration-> NVIDIA X Server Settings

Go to X Server Display configuration 

Find resolution and set 1024x768.

Try to set in display only, if you set in NVIDIA X Server Settings you have to set every time when you reboot.

For more details visit [http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

Thanks all, 
This is my first one on ubuntu.

---

### Post by Guillermox on 2010-01-08
Hi
Well i'm new in linux and my first problem was my video card, but with you help my problem as been fixed.

1million  Thanks .

---

### Post by haradeep on 2010-01-10
> **Guillermox said:**
> Hi
Well i'm new in linux and my first problem was my video card, but with you help my problem as been fixed.

1million  Thanks .

Great to hear from you. I'm very happy :D that my post is helpful.

---

