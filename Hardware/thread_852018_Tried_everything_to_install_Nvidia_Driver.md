---
title: "Tried everything to install Nvidia Driver"
date: 2008-07-07
forum: Hardware
---

### Post by leighpedder on 2008-07-07
I have Tried everything to install Nvidia driver, I have a Nvidia 7900GT, I have tried every command every little thing and I still get the black screen when I enable the driver and reboot the comp, and I can't enable visual effects. What xhould I do I am new to Linux to. I am about to go back to windows lol.

Please Help

Cheers in advance Leigh

---

### Post by overdrank on 2008-07-07
> **leighpedder said:**
> I have Tried everything to install Nvidia driver, I have a Nvidia 7900GT, I have tried every command every little thing and I still get the black screen when I enable the driver and reboot the comp, and I can't enable visual effects. What xhould I do I am new to Linux to. I am about to go back to windows lol.

Please Help

Cheers in advance Leigh

HI and welcome, when you state installing the nvidia drivers are you meaning the restricted drivers under system, administration?
What version of ubuntu are you using? 
Can you tell us which commands you used so we will not repeat what you have tried?

---

### Post by leighpedder on 2008-07-07
I am using Ubuntu 8.04, I have tried using the Envyng and that insalls then when I reboot the screen is black, 
I tried the sudo apt-get install nvidia-glx 
and then tried to edit the xorg.conf and nothing seems to work,
I then downloaded the driver from nvidia and then says have to be root to install.

What should I do

Cheers again

---

### Post by overdrank on 2008-07-07
> **leighpedder said:**
> I am using Ubuntu 8.04, I have tried using the Envyng and that insalls then when I reboot the screen is black, 
I tried the sudo apt-get install nvidia-glx 
and then tried to edit the xorg.conf and nothing seems to work,
I then downloaded the driver from nvidia and then says have to be root to install.

What should I do

Cheers again

Ok well the nvidia-glx is the wrong driver it should be the nvidia-glx-new. I would try Envy again and if you get the black screen then you can use the keys alt, ctrl, F1 and this will bring you to the command line and you can configure your xorg with this command. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` or you can boot into recovery mode and use the xfix option to hopefully correct the issue. If you still want to install the nvidia driver you downloaded from the site then post back and we can help with that also.

---

### Post by leighpedder on 2008-07-07
well I now have the driver enabled in the hardware drivers, but I can only get 800x600 and i can't enable the effects what else do i need to do to get better resulotion

Thanks Leigh

---

### Post by overdrank on 2008-07-07
> **leighpedder said:**
> well I now have the driver enabled in the hardware drivers, but I can only get 800x600 and i can't enable the effects what else do i need to do to get better resulotion

Thanks Leigh

Ok have you ensured that the nvidia is enabled under hardware dirvers?
 You can use synaptic manager and install the nvidia settings.then us the  alt, F2 keys and enter this command ```
gksu nvidia-settings
``` and there you can adjust your resolution.

---

### Post by leighpedder on 2008-07-07
it comes up with this error 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

how do i do I do this, sorry noob at linux
cheers leigh

---

### Post by overdrank on 2008-07-07
> **leighpedder said:**
> it comes up with this error 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

how do i do I do this, sorry noob at linux
cheers leigh

HI and this is what I thought was going to happen. Ok you can try and use Envy to uninstall the nvidia drivers and then reboot before installing the restricted drivers or Envy to install. I will be on for a bit but I worked last nite so if I do not respond I am sure someone will be able to assist.

---

### Post by starcannon on 2008-07-07
If Envy doesn't work out for you then you may want to try my guide, its how I do all of my Nvidia installs.

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

However you decide to go though, be sure to not skip steps in the tutorials you are using.

GL

---

### Post by stchman on 2008-07-07
> **leighpedder said:**
> I have Tried everything to install Nvidia driver, I have a Nvidia 7900GT, I have tried every command every little thing and I still get the black screen when I enable the driver and reboot the comp, and I can't enable visual effects. What xhould I do I am new to Linux to. I am about to go back to windows lol.

Please Help

Cheers in advance Leigh

That card should work perfectly after you enable the restricted driver (nvidia-glx-new).

Are you running Hardy?  If no then you will need Envy 0.9.10.

---

### Post by leighpedder on 2008-07-07
Ok, so I have the driver enabled but it can only go to 800x600 Res, and the same error when I try to get in to the nvidia settings
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server"

What else can I do.
thanks in advance

---

### Post by starcannon on 2008-07-07
Try running
```

gksudo nvidia-settings

```

make changes, and then save to xorg.conf through that gui.

---

### Post by mikewhatever on 2008-07-07
> **leighpedder said:**
> Ok, so I have the driver enabled but it can only go to 800x600 Res, and the same error when I try to get in to the nvidia settings
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server"

What else can I do.
thanks in advance

nvidia-xconfig didn't do a very good job in my case, but you can certainly try running <sudo nvidia-xconfig>, and then <sudo /etc/init.d/gdm restart> to restart xserver. Then try nvidia-settings again and if it tells you nvidia driver is not in use, post the output of the following command here <cat /etc/X11/xorg.conf>. If nvidia driver is in use, and only the resolution needs adjustments, post back and we will deal with that.

PS: Why did you try installing nvidia-glx from cli? Have you installed with Alternate or Desktop CD?

---

### Post by leighpedder on 2008-07-07
I tried the install guide still got the black screen, tried envyng again no luck,
here is my config

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1440	900
		Modes		"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection

Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection

Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "ServerFlags"
EndSection

I don't know what I am looking for lol

Cheers in advance

---

### Post by starcannon on 2008-07-08
Section "Device"
Identifier "Configured Video Device"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "vesa"
Screen 0
EndSection

You missed a step of the guide or something, Driver should say "nvidia" instead of "vesa". If your using the guide I wrote, run it again, skip NO steps, even if you've done them before, even if you've done them recently. If you go through it (step 13 the last step is optional but beneficial later) then you'll have a working nvidia setup.

---

### Post by leighpedder on 2008-07-08
Ok so I did everything again, and I get a black screen, I can't do anything. What else can I do.

Cheers Leigh

---

### Post by leighpedder on 2008-07-08
Ok so I tried to fix the Xserver in recovery mode and that didn't work, Some help me please.

Thanks in advance leigh

---

### Post by overdrank on 2008-07-08
> **leighpedder said:**
> Ok so I tried to fix the Xserver in recovery mode and that didn't work, Some help me please.

Thanks in advance leigh

Hi and I feel you frustrations. My son's system gave me fits with Hardy 8.04 and nvidia. I finally gave up and installed gutsy on his system. They only thing I can think of now is for you to go into synaptic and remove all the nvidia drivers and then try envy again. This may help or you can try to install the nvidia driver that you have downloaded before.

---

