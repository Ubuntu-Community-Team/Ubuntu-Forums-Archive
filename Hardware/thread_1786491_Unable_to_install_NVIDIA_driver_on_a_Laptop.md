---
title: "Unable to install NVIDIA driver on a Laptop"
date: 2011-06-19
forum: Hardware
---

### Post by Gobin on 2011-06-19
Hello all,

I know the problem I'm describing here was mentioned in many previous threads, but sadly the solutions suggested there didn't work for me.
I would really appreciate your help...

I'm new to Ubuntu and tried to install v. 11.4 on my new Dell Inspirion N5110, with NVIDIA GT525M graphics card.

Everything was fine (Unity worked), until I installed the recommended driver via 'Additional Drivers' in the 'System-->Administration':
Since then, Unity stopped working and only Gnome booted.

After trying to run "sudo nvidia-xconfing' as required, I got the massage:

"VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
Device section "Default Device" must have a Driver line."
(I checked the file. It really was missing).

Rebooting after that, didn't allow Gnome to boot at all, and forced me to delete xorg.conf via the terminal to get back to Gnome.

So I've tried:
Updating the drivers- same result.
Completely deleting every trace of Nouveau driver- same result.
Editing the xorg.conf manually and adding my graphic's card name- same result.
Installing 'Bumblebee'- stuck the computer and caused my mouse-pointer to shiver (I have no idea what that was).

Does anybody know how to fix that?

Thanks,
G.

P.S.
I'd like to apologize for any annoying grammatical errors.

---

### Post by phz_swe on 2011-06-19
You have an Nvidia Optimus setup. That means you have both an integrated Intel GPU and the (more or less) discrete Nvidia GPU. The thought is that the laptop should be able to seemlessly switch between them to save battery, but Nvidia have said it is impossible to do this on Linux, and haven't made any effort to develop a Linux solution.

However, you mentioned Bumblebee, which is a community-made solution that proves that it _is_ possible, and that Nvidia just don't care about the Linux segment for personal laptops. Bumblebee is still very rough, though, as you noticed (Nvidia isn't doing anything to help them).

Because of this I don't think you can use the Nvidia card with Nvidia's own drivers. If you delete your xorg.conf, what you in practice are doing is letting X use the Intel circuit exclusively. This leaves the Nvidia circuit unused, but I think it doesn't "turn it off", which might impact battery life.

If anyone has different experiences, please correct me. I'm not really touched by this. I have a very early dual graphics laptop, where I have the option to switch fully to the Nvidia card in the BIOS setup, which eliminates the problems with the two cards talking.

---

### Post by Gobin on 2011-06-30
Thanks for the replay.

---

### Post by m_pahlevanzadeh on 2011-10-07
I have an interesting problem with Inspiron n5110, dual card graphic, I installed fully nvidia driver and when i use 'lsmod |egrep -i nvidia' i get good result, Also when i use Xorg -configure :0 , and read exported xorg.conf file i see nvidia driver in it.But when i copy the given file to /etc/X11 and restart gdm3, i see gdm3 page, but i didn't see login widget in gdm3 page.And when i remove xorg file everything is OK.

I need to manipulating xorg.conf, So i must export it and cp it to /etc/X11, please help me...

exported xorg.conf :
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	Screen      3  "Screen3" RightOf "Screen2"
	Screen      4  "Screen4" RightOf "Screen3"
	Screen      5  "Screen5" RightOf "Screen4"
	Screen      6  "Screen6" RightOf "Screen5"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor3"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor4"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor5"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor6"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "nvidia"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "nouveau"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card2"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
	Identifier  "Card3"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
	Identifier  "Card4"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card5"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
	Identifier  "Card6"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen3"
	Device     "Card3"
	Monitor    "Monitor3"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen4"
	Device     "Card4"
	Monitor    "Monitor4"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen5"
	Device     "Card5"
	Monitor    "Monitor5"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen6"
	Device     "Card6"
	Monitor    "Monitor6"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

---

### Post by wackawacka on 2011-10-07
> **Gobin said:**
> Thanks for the replay.

phz_swe had a great response but what sticks out with regard to your initial question is that you said it worked before you went through the additional drivers.  

that's all the clue i need to know whether it's possible to get something working or not.  so while i agree with the argument presented by phz_swe, i disagree that this means anything for you because you saw it work before you tweaked it.  

if your statement was accurate and you did see it work, your option is to re-install and don't run additional drivers, or don't install any updates pertaining to nvidia.

---

### Post by wackawacka on 2011-10-07
> **m_pahlevanzadeh said:**
> I have an interesting problem with Inspiron n5110, dual card graphic, I installed fully nvidia driver and when i use 'lsmod |egrep -i nvidia' i get good result, Also when i use Xorg -configure :0 , and read exported xorg.conf file i see nvidia driver in it.But when i copy the given file to /etc/X11 and restart gdm3, i see gdm3 page, but i didn't see login widget in gdm3 page.And when i remove xorg file everything is OK.

I need to manipulating xorg.conf, So i must export it and cp it to /etc/X11, please help me...

exported xorg.conf :
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	Screen      3  "Screen3" RightOf "Screen2"
	Screen      4  "Screen4" RightOf "Screen3"
	Screen      5  "Screen5" RightOf "Screen4"
	Screen      6  "Screen6" RightOf "Screen5"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor3"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor4"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor5"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor6"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "nvidia"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "nouveau"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card2"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
	Identifier  "Card3"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
	Identifier  "Card4"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card5"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
	Identifier  "Card6"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen3"
	Device     "Card3"
	Monitor    "Monitor3"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen4"
	Device     "Card4"
	Monitor    "Monitor4"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen5"
	Device     "Card5"
	Monitor    "Monitor5"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen6"
	Device     "Card6"
	Monitor    "Monitor6"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```


you'll get a faster response if you start a new thread.

---

