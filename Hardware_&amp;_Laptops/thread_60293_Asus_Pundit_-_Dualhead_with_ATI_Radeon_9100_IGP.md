---
title: "Asus Pundit - Dualhead with ATI Radeon 9100 IGP"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by miketech on 2005-08-27
Hi,

I have an Asus Pundit Barebone with an onboard ATI Radeon 9100 IGP.

The onboard card has a vga and a dvi output, so I wanted to use two monitors. On the dvi output I have a monitor with a 1280x1024 resolution and on the vga a monitor with 1024x768.

I wanna have one desktop with different resolutions on each screen and it should be possible to move a window from one screen to the other. This should work with xinerama.

My problem now is: It doesn´t work :)

I´ve tried a lot, but when using the X radeon driver I only can use one or none. After days of work I´ve tried the original ATI drivers. Now it seems to be possible to use both screens. When starting X both screens are activated, but I don´t see anything useful *g*

On both screens I have only a grey background and the mouse cursor only is a whit rectangle. I don´t see gdm. When trying to login gnome starts, but I only see some strange things. And after a few seconds my computer is hanging up.

I also tried the parameters for bigdesktop. But this doesn´t work too. I only can use the clone mode, then I see the same content on both screens with the same resolution. But I need different resolutions.

In order to see, if it should be generally possible to use both screens I installed windows. Here it works after 10 minutes of work :(

So there should be a way to get it working with linux too. Maybe you have an idea. I´ve already read a lot of postings and tried 100 different config files. 

Here is my current xorg.conf. Maybe it´s useful.

Greetings 

Mike

```

Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	InputDevices   "/dev/ttyS0"
	InputDevices   "/dev/ttyS1"
	InputDevices   "/dev/ttyS2"
	InputDevices   "/dev/ttyS3"
	InputDevices   "/dev/ttyS4"
	InputDevices   "/dev/ttyS5"
	InputDevices   "/dev/ttyS6"
	InputDevices   "/dev/ttyS7"
	InputDevices   "/dev/ttyS8"
	InputDevices   "/dev/psaux"
	InputDevices   "/dev/logibm"
	InputDevices   "/dev/sunmouse"
	InputDevices   "/dev/atibm"
	InputDevices   "/dev/amigamouse"
	InputDevices   "/dev/atarimouse"
	InputDevices   "/dev/inportbm"
	InputDevices   "/dev/gpmdata"
	InputDevices   "/dev/mouse"
	InputDevices   "/dev/usbmouse"
	InputDevices   "/dev/adbmouse"
	InputDevices   "/dev/input/mice"
	InputDevices   "/dev/input/event0"
	InputDevices   "/dev/pointer0"
	InputDevices   "/dev/pointer1"
	InputDevices   "/dev/pointer2"
	FontPath     "/usr/X11R6/lib/X11/fonts/truetype/"
	FontPath     "/usr/X11R6/lib/X11/fonts/URW/"
	FontPath     "/usr/X11R6/lib/X11/fonts/uni/"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc/"
EndSection


Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx"
    ##Load "dri" 
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "keyboard"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "Buttons" "9"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "imps/2"
	Option	    "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
	Identifier   "monitor0"
	VendorName   "Samsung"
	ModelName    "SyncMaster 181T"
	#HorizSync    30.0 - 81.0
	#VertRefresh  56.0 - 85.0
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier   "monitor1"
	VendorName   "Philips"
	ModelName    "150B"
	#HorizSync    30.0 - 60.0
	#VertRefresh  50.0 - 75.0
        Option "DPMS"
EndSection
  
Section "Device"
    Identifier "device0"
    VendorName "ATI"
    BoardName "ATI Radeon"
    Driver "fglrx"
    BusID "1:5:0"
    Option "mtrr" "off"
    Option "no_accel" "no"
    Option "no_dri" "yes"

#    Option "DesktopSetup" "0x00000001"
    #Option "DDCMode" "on"
    #Option "DPMS"
    Option "UseInternalAGPGART" "yes"
    Screen 0    
EndSection

Section "Device"
    Identifier "device1"
    BoardName "ATI Radeon"    
    Driver "fglrx"
    BusID "1:5:0"
    Option "mtrr" "off"
    Option "no_accel" "no"
    Option "no_dri" "yes"
#    Option "DesktopSetup" "0x00000001"
    #Option "DDCMode" "on"
    #Option "DPMS"
    Option "UseInternalAGPGART" "yes"
    Screen 1        
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "device0"
    Monitor "monitor0"
    DefaultColorDepth 24
    Subsection "Display"
        Depth 24
        #Virtual 1280 1024    
        Modes    "1280x1024" 
        #ViewPort 0 0
    EndSubsection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    Subsection "Display"
        Depth 24
        Modes    "1024x768" 
	#ViewPort 0 0
    EndSubsection    
EndSection

Section "ServerLayout"
    Identifier "Multihead layout"
    InputDevice "Generic Keyboard" "CoreKeyboard"
    InputDevice "Configured Mouse" "CorePointer"
    Screen  "Screen0" 0 0
    Screen  "Screen1" RightOf "Screen0" 
    Option  "Xinerama" "true"
EndSection


```

---

### Post by jedthehumanoid on 2005-08-27
Sorry no answer... ;-) 
But please post if you find a solution to this yourself.
I also have a pundit and been looking into a new screen with dvi to get tv-out to work alongside the screen (hardware doesn't support tv-out+vga). So i'd be happy to know if and how this works!  :)

Jedthehumanoid

---

