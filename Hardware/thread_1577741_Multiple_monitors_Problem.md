---
title: "Multiple monitors Problem ?"
date: 2010-09-19
forum: Hardware
---

### Post by Face_Man on 2010-09-19
Hello all,
I am trying to setup xorg.conf for 2 monitors 
     1. Labtop monitors (LVDS1)
     2. External monitors (HDMI1)
so i need the  External monitor  to be the main screen and the Labtop monitor to be the External for it. However, all i got so far is a duble of one screen display on both screen. so if i open something it will be display on both screen.

$ xrandr
```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 214mm
   1600x900       60.3*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 520mm x 324mm
   1920x1080      60.0*+
   1280x1024      60.0  
   1360x768       59.8  
   1280x720       59.7  
   1024x768       60.0  
   800x600        60.3  
   720x480        59.9  
   640x480        60.0  
DP1 disconnected (normal left inverted right x axis y axis)

```

$ lspci
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

```

Section "ServerLayout"
	Identifier     	"X.org Configured"
	Screen		0	"LG-Screen"   0 0 
  	Screen      1  	"Labtop-Screen" RightOf "LG-Screen"
	InputDevice    	"Mouse0" "CorePointer"
	InputDevice    	"Keyboard0" "CoreKeyboard"
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/misc/"
	FontPath     "/usr/share/fonts/TTF/"
	FontPath     "/usr/share/fonts/OTF/"
	FontPath     "/usr/share/fonts/Type1/"
	FontPath     "/usr/share/fonts/100dpi/"
	FontPath     "/usr/share/fonts/75dpi/"
EndSection
 
Section "Module"
	Load  "dri2"
	Load  "record"
	Load  "extmod"
	Load  "dri"
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


Section "Device"
	#Option      "Monitor-LVDS1" "Monitor0"
    #Option      "Monitor-HDMI1" "Monitor1"
	Identifier  "IntelDevice"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Core Processor Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
	Option      "Monitor-LVDS1"  "LVDS"
    Option 		"Monitor-HDMI1"   "HDMI"
EndSection

Section "Monitor"
	Identifier   "LVDS"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "HDMI"
	VendorName   "LG"
	ModelName    "FULLHD"
EndSection

Section "Screen"
        Identifier "Labtop-Screen"
        Device     "IntelDevice"
        Monitor    "LVDS"
        SubSection "Display"
                #Viewport   	0 0
              	Depth		24
				Modes  		"1600x900"
				#Virtual         3520 900 
        EndSubSection
EndSection

Section "Screen"
		Identifier 	"LG-Screen"
		Device     	"IntelDevice"
		Monitor    	"HDMI"
		SubSection 	"Display"
			#Viewport   0 0
			Depth     	24
			Modes  		"1920x1080"
			#Virtual	3520 1080 
		EndSubSection
EndSection

```

any help would be much appreciated.

---

### Post by IcarusR on 2010-09-19
> all i got so far is a duble of one screen display on both screen. so if i open something it will be display on both screen.


If you want to have different desktop on each screen then you need to set-up an independent x session for each screen.

---

### Post by ubun2warrior on 2010-09-19
hi

i also want to have multiple monitors... that is what i have been trying to do .. plz explain gow to start an independent x session 

plz someone help !!! 
PS: this an SOS call...
ubun2warrior

---

### Post by IcarusR on 2010-09-19
ubun2warrior

> plz explain gow to start an independent x session

Google for it.

---

### Post by ubun2warrior on 2010-09-19
excellent !!!

eureka !!!

thank u so much ......

i am going there bye....

i will come back with some answer....

.....
........

---

### Post by Face_Man on 2010-09-19
> **IcarusR said:**
> If you want to have different desktop on each screen then you need to set-up an independent x session for each screen.

i do appreciate your help , however, i did mention i need the External monitor to be the main screen and the Labtop monitor to be the External for it. therefore, no i dont want to have a different desktop on each screen.

---

