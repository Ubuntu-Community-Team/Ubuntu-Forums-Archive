---
title: "Connect Laptop To Tv(Plasma) via VGA"
date: 2009-01-12
forum: Hardware
---

### Post by ramtinoo on 2009-01-12
hi ! 

	
I've bought a VGA cable today !
I have tried to connect my Laptop(sony vaio VGN-FS415s) to my Plasma (Full-HD-Plasma-Stereo-TV, Panasonic, »TH-42PZ70«) but unfortunately has not worked. 

Grafik card :  	nVidia GeForce Go 6400 
VGA Cable :[IMG]http://static.actebis-images.com/productimages/I177788.jpg[/IMG]

how can I get my laptop connected with plasma ?? :)can someone help me Please?

l.g
R.f

---

### Post by ramtinoo on 2009-01-15
can someone HELP me PLEASEEEEE ???

---

### Post by ramtinoo on 2009-01-17
PLEASEEEEEEEEEEEEEEE ??? I need IT !!!

---

### Post by Healey on 2009-07-20
Hi

Did you ever resolve this problem ???   as I am having problems  as well

Regards

Healey

---

### Post by GoldenSun on 2009-07-20
usually it's plug n play for me.
Do you have the latest nvidia driver?

---

### Post by icyhandlz on 2009-07-20
make sure that the resolution on your computer is a resolution that the tv supports.  I had the same problem and found a resolution that my tv supported changed my resolution on the comp and everything worked just fine.   Hope this helps good luck

boomer

---

### Post by Healey on 2009-07-21
Hi

Thanks for the replies and sorry for my late reply

I added this to my Section "Monitor" in the xorg.conf

HorizSync       31.0 - 69.0
VertRefresh     59.0 - 86.0

It did not give me the 1360x768 that I get when I boot into windoze, but I get something like 1024x768 which is at least usable.

I will work on it some more but I really hate it when I am forced to admit that windoze does something quicker, easier and slicker than Ubuntu  -  LOL

Thanks

Healey

---

### Post by Healey on 2009-07-21
Hi

Perhaps I should start a new thread - As I did not start this one !!

However here is a little more info

I am using jaunty
The Monitor is a Panasonic TH-42PZ70B  (Plasma TV)
Graphics card is a Nvidia GEForce4 MX440  
I have a Desk top PC

Here is my Xorg.conf which gives me 1024x768, but what I would like is 1360x768 which I can get in Windoze !



Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

	# Custom modes
    Identifier     "Configured Monitor"
    HorizSync       31.0 - 69.0
    VertRefresh     59.0 - 86.0
    ModeLine       "1920x1080" 148.5 1920 1980 2028 2200 1080 1084 1089 1125
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"

##	Modes "1920x1080"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "PreferredMode" "1360x768"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection



I have tried using the nvidia X server settings gui which shows the 1360x768 that I want, but it looks wrong and it will not keep the settings on the next boot

Any one help please

Thanks

Healey

---

