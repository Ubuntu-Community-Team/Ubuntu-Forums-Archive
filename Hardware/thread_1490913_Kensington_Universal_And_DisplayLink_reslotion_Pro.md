---
title: "Kensington Universal And DisplayLink reslotion Problem"
date: 2010-05-22
forum: Hardware
---

### Post by Face_Man on 2010-05-22
Hello all,

I am trying to connect to my LG 40 inch TV using Kensington Universal Multi-Display Adapter on Ubuntu 10.04 64bit.I was able to do so however, the maximum reslotion i got is 1280 x 1024. The Kensington Adapter support  up to a 2048 X 1152 resolution and the LG TV support up to 1920x1200 resolution but i am
unable to get highter resolution for my TV.

here what i did so far


```
sudo apt-get install libusb-dev xorg-dev 
```

Install libdlo-0.1.2
	```
./configure && sudo make install && make check 
```

Install udlfb
```
	git clone http://git.plugable.com/webdav/udlfb
	make && sudo make install
```

Install xf-video-udlfb
	```
git clone http://git.plugable.com/webdav/xf-video-udlfb
	make && sudo make install
```

```
sudo apt-get install xserver-xorg-video-displaylink
```

xorg.conf
```
Section "ServerLayout"
    Identifier     "My Server Layout - configure"
    Screen  0      "DisplayLinkScreen" 0 0
    Screen  1      "Default Screen" RightOf "DisplayLinkScreen"
    Option         "Xinerama" "off"
EndSection

Section "Device"
	Identifier	"Default Device"
	BusID 		"PCI:1:0:0"
	Driver		"nvidia"
	VendorName  	"nVidia Corporation"
    	BoardName   	"nVidia Corporation G72M [GeForce Go 7400] (rev a1)"
 	Option		"NoLogo"	"True"
	#Option 	"ConnectedMonitor" "dfp, dfp"
	#Option 	"TwinView" "1"
	#Option	 	"Metamodes" "1280x1024,1920x1200; 1024x768,NULL"
 	# Option 	"NoTwinViewXineramaInfo"
EndSection

Section "Device"
    Identifier      	"DisplayLinkDevice"
    driver          	"displaylink"
    Option  		"fbdev" "/dev/fb1"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
 	Monitor         "Default Monitor"
   	SubSection 	"Display"
        	Depth   24
        	Modes   "2048X1152@60" "1920x1200@60" "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
	
    	EndSubSection
EndSection

Section "Screen"
    	Identifier      "DisplayLinkScreen"
    	Device          "DisplayLinkDevice"
	Monitor         "DisplayLinkMonitor"
  	SubSection "Display"
        	Depth   24
        	#Modes	"1920x1200" "1920x1080" "1600x1200" "1680x1050" "1440x900" "1280x1024"
 		Modes   "2048X1152@60" "1920x1200@60" "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
	EndSubSection
EndSection


Section "Monitor"
    Identifier   "Default Monitor"
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@75" 107.2 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
    ModeLine       "1280x768@75" 103.0 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@75" 136.5 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
    ModeLine       "2048x1152@60" 197.97  2048 2184 2408 2768  1152 1153 1156 1192  -HSync +Vsync
EndSection

Section "Monitor"
    Identifier      "DisplayLinkMonitor"
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@75" 107.2 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
    ModeLine       "1280x768@75" 103.0 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@75" 136.5 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
    ModeLine       "2048x1152@60" 197.97  2048 2184 2408 2768  1152 1153 1156 1192  -HSync +Vsync
EndSection
 
Section "Module"
    	Load  "extmod"
    	Load  "glx"
	Load  "record"
    	Load  "dri"
    	Load  "dri2"
    	Load  "dbe"
	Load "bitmap"
	Load "ddc"
	Load "freetype"
	Load "lbx"
	Load "int10"
	Load "type1"
	Load "vbe"
EndSection


Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    ModulePath   "/usr/local/lib/xorg/modules"
    ModulePath     "/usr/local/lib/xorg/modules/drivers"
EndSection

```

Laptop lspci
```
	00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
	00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
	00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
	00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
	00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
	00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
	00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
	00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
	00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
	00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
	00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
	00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
	00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
	01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
	06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
	08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
	08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
```


I also try to compile displaylink-mod-0.3 and this is what i got 

```
~/Desktop/DisplayLink/displaylink-mod-0.3/displaylink$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=~Desktop/DisplayLink/displaylink-mod-0.3/displaylink modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  ~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.o
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c: In function ‘displaylink_edid_to_reg’:
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:85: error: ‘struct detailed_pixel_timing’ has no member named ‘hactive_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:91: error: ‘struct detailed_pixel_timing’ has no member named ‘vactive_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:97: error: ‘struct detailed_pixel_timing’ has no member named ‘hblank_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:97: error: ‘struct detailed_pixel_timing’ has no member named ‘hsync_offset_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:101: error: ‘struct detailed_pixel_timing’ has no member named ‘vblank_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:101: error: ‘struct detailed_pixel_timing’ has no member named ‘vsync_offset_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:101: error: ‘struct detailed_pixel_timing’ has no member named ‘vsync_offset_lo’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:105: error: ‘struct detailed_pixel_timing’ has no member named ‘hblank_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:106: error: ‘struct detailed_pixel_timing’ has no member named ‘hsync_pulse_width_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:109: error: ‘struct detailed_pixel_timing’ has no member named ‘vblank_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:110: error: ‘struct detailed_pixel_timing’ has no member named ‘vsync_pulse_width_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:110: error: ‘struct detailed_pixel_timing’ has no member named ‘vsync_pulse_width_lo’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c: In function ‘displaylink_set_video_mode’:
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:242: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long int’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:249: error: ‘struct detailed_pixel_timing’ has no member named ‘hactive_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c: In function ‘displaylink_setup’:
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:308: error: ‘struct detailed_pixel_timing’ has no member named ‘hactive_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:311: error: ‘struct detailed_pixel_timing’ has no member named ‘hactive_hi’
~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.c:312: error: ‘struct detailed_pixel_timing’ has no member named ‘vactive_hi’
make[2]: *** [~Desktop/DisplayLink/displaylink-mod-0.3/displaylink/displaylink-usb.o] Error 1
make[1]: *** [_module_~Desktop/DisplayLink/displaylink-mod-0.3/displaylink] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [all] Error 2
```



Any help would be much appreciated.

---

### Post by dxxvi on 2011-09-05
Hi,

Have you found any resolution for that problem yet?

Regards.

---

