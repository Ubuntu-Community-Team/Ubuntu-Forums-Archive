---
title: "Wrong screen resolution. Please help"
date: 2011-02-10
forum: Hardware
---

### Post by Sinopa on 2011-02-10
So my old HIS radeon HD 4650 graphics card broke down today and I have tried to use the onboard graphics card and I can't get higher screen resolution then 1024x768 :(

The onboard graphics card is a [FONT=arial, helvetica][SIZE=2]NVIDIA GeForce 6100 nForce430 and the monitor is an Acer AL2216W.

I have installed the proprietary driver, but I still get only 1024x768 and Ubuntu can't detect the Acer monitor.

I tried to follow some tutorials on how to edit the xorg.conf, but everything I have tried doesn't work. 

I have been trying all day to get 1680x1050 60Hz, but I have given up. Can someone please help me? 

Wish I could afford a new graphics card, but at the moment I can't :(
[/SIZE][/FONT]

---

### Post by gufide on 2011-02-10
we can force a higher resolution in the xorg.conf configuration, press alt + F2 then enter:
```
gksudo cp  /etc/X11/xorg.conf  /etc/X11/xorg_back.conf
gksudo gedit /etc/X11/xorg.conf
```go to the screen section, go in the option mode then erase all resolutions and enter your own

if your X server doesn’t start correctly, boot in recovery mode and, go to the root console and enter```
rm  /etc/X11/xorg.conf
mv /etc/X11/xorg_back.conf /etc/X11/xorg.conf
```

---

### Post by Sinopa on 2011-02-11
[FONT=Arial][SIZE=2]So as I wrote above 

[/SIZE][/FONT]> I tried to follow some tutorials on how to edit the xorg.conf, but everything I have tried doesn't work", [FONT=arial, helvetica][SIZE=2][FONT=Arial]
I tried to enter my own resolution, but then didn't work either[/FONT][/SIZE][/FONT].[FONT=arial, helvetica][SIZE=2][FONT=Arial] I'm stuck at 1024x768. So could you please be more specific? HOW do I do this? 
[/FONT] 
This is my xorg.conf

[/SIZE][/FONT][HTML]
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Default Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150SE nForce 430"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Default Device"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

[/HTML]

---

### Post by Grenage on 2011-02-11
Before we go down the xorg.conf route, have you tried using the nvidia-settings utility?  It it's not installed:

```
sudo apt-get install nvidia-settings
```

If it is:

```
gksu nvidia-settings
```

---

### Post by Sinopa on 2011-02-11
I think that it first have to detect what kind of monitor I have. How do I add that to xorg.conf?

As I also wrote above it's an Acer AL2216W and I want it to be set to 1680x1050, 60Hz.

---

### Post by Grenage on 2011-02-11
> **Sinopa said:**
> I think that it first have to detect what kind of monitor I have. How do I add that to xorg.conf?

As I also wrote above it's an Acer AL2216W and I want it to be set to 1680x1050, 60Hz.

If the nvidia-settings tool doesn't work out, I'm more than happy to help you with the xorg.conf.

---

### Post by Sinopa on 2011-02-11
> **Grenage said:**
> Before we go down the xorg.conf route, have you tried using the nvidia-settings utility?  It it's not installed:

```
sudo apt-get install nvidia-settings
```If it is:

```
gksu nvidia-settings
```

Yes, I have tried that. That was the first thing I tried. It thinks my monitor is a CRT monitor with max res. at 1024x768.

---

### Post by Sinopa on 2011-02-11
> **Grenage said:**
> If the nvidia-settings tool doesn't work out, I'm more than happy to help you with the xorg.conf.

Oh thank you, thank you, thank you. I had hoped some kind soul would do that. I know that the problem is in the xconf, I just don't know how to edit it the way I want.

---

### Post by Grenage on 2011-02-11
Here we go; you can add more modes (resolutions) if you need them:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "ACER"
	ModelName "AL2216W"
	HorizSync 31 - 80
	VertRefresh 56 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "GeForce 6100"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1680x1050"
	EndSubSection
EndSection
```

---

### Post by Sinopa on 2011-02-11
Oh my god. It wooooorks. WOOOHOOO :D
You are a life saver Grenage :)
I now have 1680x1050 resolution, but the refresh rate is only 53Hz. How can I change that to 60Hz? I can select only 50Hz, 52Hz and 53Hz.

---

### Post by Sinopa on 2011-02-11
> **Sinopa said:**
> Oh my god. It wooooorks. WOOOHOOO :D
You are a life saver Grenage :)
I now have 1680x1050 resolution, but the refresh rate is only 53Hz. How can I change that to 60Hz? I can select only 50Hz, 52Hz and 53Hz.

I solved it :)

Again I just want to say thank you  again Grenag. You a savior :)

---

### Post by Sinopa on 2011-02-11
I thought I had solved it, but it didn't stick. So I still have 53Hz and not 60Hz.

---

### Post by Grenage on 2011-02-11
Howdy. :)

I've never done it, but I think you can specify the refresh rate in the mode:

```
Modes "1680x1050_60"
```

---

### Post by Sinopa on 2011-02-11
> **Grenage said:**
> Howdy. :)

I've never done it, but I think you can specify the refresh rate in the mode:

```
Modes "1680x1050_60"
```

Hei på deg ;) (that's howdy in norwegian) :)

I tried that, but that didn't work. Still have 53Hz.
I tried to change HorizSync and VertRefresh after reading a thread and got it up to 54Hz, but the screen got blurry. So I changed it back to HorizSync 31 - 80 and VertRefresh 56 - 75 that was in your xorg.
I'm afraid to change HorizSync and VertRefresh when I don't know what I'm doing because I don't want to break the only monitor I've got :)

---

### Post by Grenage on 2011-02-11
> **Sinopa said:**
> Hei på deg ;) (that's howdy in norwegian) :)

I tried that, but that didn't work. Still have 53Hz.
I tried to change HorizSync and VertRefresh after reading a thread and got it up to 54Hz, but the screen got blurry. So I changed it back to HorizSync 31 - 80 and VertRefresh 56 - 75 that was in your xorg.
I'm afraid to change HorizSync and VertRefresh when I don't know what I'm doing because I don't want to break the only monitor I've got :)

Hej! (as close as I can get to Norway - Sweden).

Ok, change the mode back to "1680x1050", then add a modeline, so it looks like this:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "ACER"
	ModelName "AL2216W"
	HorizSync 31 - 80
	VertRefresh 56 - 75
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "GeForce 6100"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1680x1050"
	EndSubSection
EndSection
```

The frequency values I used for your monitor (horizontal/vertical) are correct according to the monitor's manual.

---

### Post by Sinopa on 2011-02-11
Strange... I still get only 53Hz.

---

### Post by Grenage on 2011-02-11
> **Sinopa said:**
> Strange... I still get only 53Hz.

Looking at some other material, it appears that the graphics card can't cope with that resolution at that frequency.  That seems odd to me, but others have reported the same problem (~50hz).

Try swapping the two 24 bit references for 16.

---

### Post by Sinopa on 2011-02-11
> **Grenage said:**
> Looking at some other material, it appears that the graphics card can't cope with that resolution at that frequency.  That seems odd to me, but others have reported the same problem (~50hz).

Try swapping the two 24 bit references for 16.

Tried that now and it still didn't work.
Well, atleast I have 1680x1050 and that is the most important thing :)

Thank You for ALL your help Grenage :)

---

### Post by Grenage on 2011-02-11
Any time; it's just a shame we couldn't get 60mhz.

---

### Post by smathai on 2011-03-15
I ran into exactly the same situation. After following everything on this thread I had the 1680x1050 resolution but something was wrong with the frequency.

I used the nvidia xserver settings to set it to 60Hz, but that shifted the screen to the right.

I then used the monitor's own menu settings to reset it and presto! Everything was good again!

---

