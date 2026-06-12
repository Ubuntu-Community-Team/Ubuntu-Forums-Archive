---
title: "Multiple Monitor Setup"
date: 2009-02-18
forum: Hardware
---

### Post by RockClimb on 2009-02-18
Hello!

(My question is below) I recently upgraded the hardware in my system and also made the decision to switch Linux distro to Ubuntu. I have over the last 12 or so years run, Slackware, RedHat, Suse, Mandrake, Gentoo, Caldera among many others. My hat is off to the developers :KS of Ubuntu! :D This is by far the best Linux distro I have ever installed! Keep up the great work! Now on to my question....

I switched over from Gentoo to Ubuntu 64 bit version, and the hardware upgrade was nearly everything in the box. Under Gentoo I had a 3 monitor desktop and I would like to do the same under Ubuntu. The Gentoo setup was a real pain to do. Can anyone point me to a good guide for this? I will say that while I know my way around a linux box, I still need pointers and help from time to time. 

I have a Gigabyte GA-MA790GP-DS4H motherboard with a built in ATI Radeon HD 3300 video card and a XFX Radeon HD4850 Dual head card. I tried the ATI Catalyst Control Center but it only shows the XFX card and set those 2 monitors at different resolutions.

My second question is.... Why did I stay with Gentoo for so long? ](*,)

---

### Post by teaker1s on 2009-02-19
have you checked out "twinview" or for that matter looked at the restricted hardware feature and let it install the ati driver and control centre

---

### Post by RockClimb on 2009-02-28
> **teaker1s said:**
> have you checked out "twinview" or for that matter looked at the restricted hardware feature and let it install the ati driver and control centre

I have not looked at "twinview", but I will look it over in a bit. I have managed to get it working.

All three screens up using the built in Radeon HD 3300 Card on a GigaByte MA790GP-DS4H mother board, the XFX Radeon HD4850 card, and the fglrx drivers (downloaded from ati). However, I can not get xinerama to work on all three screens, it will work on two screens with the HD4850. If I remember correctly, Xinerama developed problems with xorg version 1.3.0. I had restricted my gentoo install to anything less than that version because of that problem. I basically have 3 desktops but the mouse moves freely between them all and i can think of a few problems that this help actually help with. When closing glxgears on each desktop, it ID's them as X server ":0.0", X server ":0.1", and X server ":0.2"

Other weirdness: If I click on the firefox (Top Taskbar) icon on screen 0.1 or 0.2 it pops up an empty error dialog box and gnome-panel goes to 100% (per top) cpu usage and I can not run any other programs at that point unless I already have a terminal window open and run them from there. Killing gnome-panel with a signal 15 fixes the problem and the panel will respawn. It runs normally if I click on the icon on screen 0.0. All in all this is quite usable for what I need. I may just write a small bash script to check gnome-panel's cpu usage and kill it if it is at 100%.

Running 3 copies of glxgears (one on each screen):

screen 1: 6400-6700 FPS HD4850
screen 2: 6500-6800 FPS HD4850
screen 3: 1600-1800 FPS HD 3300

Running one copy on the fastest screen:

9100-9600 FPS

In case anyone is interested, here is a copy of my xorg.conf file. It has not been tweaked yet and may contain errors and/or unused sections, but it works. All of the "aticonfig-*[0]-2" entries added by hand. I just used the same naming method that aticonfig used.

```

Section "ServerLayout"
        Identifier      "aticonfig Layout"
        Screen  0       "aticonfig-Screen[0]-0" 0 0
        Screen  1       "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
        Screen  2       "aticonfig-Screen[0]-2" RightOf "aticonfig-Screen[0]-1"
        InputDevice     "Mouse0"        "CorePointer"
        InputDevice     "Keyboard0"     "CoreKeyboard"
EndSection

Section "Files"
        ModulePath      "/usr/lib/xorg/modules"
        FontPath        "/usr/share/fonts/X11/misc/"
        FontPath        "/usr/share/fonts/X11/Type1/"
        FontPath        "/usr/share/fonts/X11/100dpi/"
        FontPath        "/usr/share/fonts/X11/75dpi/"
EndSection

Section "Module" 
        Load    "GLcore"
        Load    "glx"
        Load    "dri"
        Load    "extmod"
        Load    "xtrap"
        Load    "record"
        Load    "dbe"
        Load    "freetype"
EndSection

Section "Extensions"
        Option  "Composite" "Disable"  #make DRI work with fglrx.
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "Protocol" "PS/2"
        Option          "Device" "/dev/psaux"
        Option          "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]-0"
        Option          "VendorName" "ATI Proprietary Driver"
        Option          "ModelName" "Generic Autodetecting Monitor"
        Option          "DPMS" "true"
        HorizSync       31.0 - 81.0  
        VertRefresh     56.0 - 76.0  
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]-1"
        Option          "VendorName" "ATI Proprietary Driver"
        Option          "ModelName" "Generic Autodetecting Monitor"
        Option          "DPMS" "true"
        HorizSync       31.0 - 81.0  
        VertRefresh     56.0 - 76.0  
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]-2"
        Option          "VendorName" "ATI Proprietary Driver"
        Option          "ModelName" "Generic Autodetecting Monitor"
        Option          "DPMS" "true"
        HorizSync       31.0 - 81.0  
        VertRefresh     56.0 - 76.0  
EndSection

Section "Device"
        Identifier  "Configured Video Device"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]-0"
        Driver          "fglrx"
        Option          "DesktopSetup" "horizontal"
        BusID           "PCI:2:0:0"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]-1"
        Driver          "fglrx"
        BusID           "PCI:2:0:0"
        Screen          1
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]-2"
        Driver          "fglrx"
        BusID           "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]-0"
        Device          "aticonfig-Device[0]-0"
        Monitor         "aticonfig-Monitor[0]-0"
        DefaultDepth    24
        SubSection "Display"
                Modes   "1280x1024" "1024x768" "800x600" "640x480"
                Depth   24
        EndSubSection
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]-1"
        Device          "aticonfig-Device[0]-1"
        Monitor         "aticonfig-Monitor[0]-1"
        DefaultDepth    24
        SubSection "Display"
                Modes   "1280x1024" "1024x768" "800x600" "640x480"
                Depth   24
        EndSubSection
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]-2"
        Device          "aticonfig-Device[0]-2"
        Monitor         "aticonfig-Monitor[0]-2"
        DefaultDepth    24
        SubSection "Display"
                Modes   "1280x1024" "1024x768" "800x600" "640x480"
                Depth   24
        EndSubSection
EndSection

```

---

### Post by RockClimb on 2009-03-04
> **teaker1s said:**
> have you checked out "twinview" or for that matter looked at the restricted hardware feature and let it install the ati driver and control centre

From what I have read, twinview is for nvidia cards, not ati. Please let me know if I am mis-interpreting this.

---

### Post by teaker1s on 2009-03-05
maybe this link will help
[http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")

---

### Post by RockClimb on 2009-03-06
> **teaker1s said:**
> maybe this link will help
[http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")

OK, after reading this, twinview is for nvidia cards and does not apply in this case as both video cards are ati hardware. But that really does not matter as it now works! :P The last changes I made did kill Compiz though. I do not know if it is possible to get Compiz and a tv card to happily co-exist, but for me, the important things are working. I will continue tweaking the settings and update the example config file as I learn more.

---

### Post by Willleung on 2009-03-10
mate, nice set up, you are lucky, i got a 780G mobo, running 2 monitors, tried addin a HD 3450 card, nothing worked.  

Can only boot into Ubuntu with the onboards, on the 3450 it wouldn't boot, not with Live USB, or HDD installation, can't even boot with a CD.. 

XP works thru..

---

