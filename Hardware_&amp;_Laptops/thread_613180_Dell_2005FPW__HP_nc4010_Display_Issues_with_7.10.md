---
title: "Dell 2005FPW / HP nc4010 Display Issues with 7.10"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by qbert00001 on 2007-11-14
All  -

I installed 7.10 on my HP nc4010 a few weeks back, and have been struggling to get it to play nicely with my widescreen Dell 2005FPW monitor ever since.  Display is fine on the native laptop display -- no issues there.  However, when docked and using the Dell monitor, I have several problems, including recurring streaks across the screen, occasional machine hang-up, and spontaneous X server restarts after the machine has been idle for some period of time, typically while the screen saver is active.  Additionally, when I boot up the login screen only takes up the amount of space that it would on the native laptop display, and once I log in the toolbar must be manually dragged to the 'bottom' of the screen (that is, the bottom of the screen when using the larger display) and when I click the maximize button on application windows it only 'maximizes' to the size of the native display (to make them larger, I must manually drag them out).  

Here are some particulars of the machine:
HP nc4010
On-board ATI graphics card
Generic HP docking station
Dell 2005FPW widescreen connected via docking station analog port (no DVI support)  

Below is my xorg.conf -- I'm sure more info might be needed.

Apologies if this looks similar to other posts, but I have spent several weeks browsing the forums and trying some of the steps suggested therein, but to no avail.

```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection
 
Section "Module"
        Load "GLCore"
        Load "bitmap"
        Load "ddc"
        Load "freetype"
        Load "glx"
        Load "vbe"
EndSection
 
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection
 
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
 
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection
 
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection
 
Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection
 
Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection
 
Section "Device"
        Identifier      "ATI Technologies Inc Radeon IGP 330M/340M/350M"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "VBEModes" "true"
EndSection
 
Section "Monitor"
        Identifier      "Dell 2005FPW"
        Option          "DPMS"
        HorizSync       30-83
        VertRefresh     56-75
        Modeline "1680x1050" 146.2 1680 1784 1960 2240 1050 1052 1058 1089 -Hsync +Vsync
EndSection
 
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon IGP 330M/340M/350M"
        Monitor         "Dell 2005FPW"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1680x1050" "1024x768" "800x600" "640x480"
                Virtual         2048 2048
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1680x1050" "1024x768" "800x600" "640x480"
                Virtual         2048 2048
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1680x1050" "1024x768" "800x600" "640x480"
                Virtual         2048 2048
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1680x1050" "1024x768" "800x600" "640x480"
                Virtual         2048 2048
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1680x1050" "1024x768" "800x600" "640x480"
                Virtual         2048 2048
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1680x1050" "1024x768" "800x600" "640x480"
                Virtual         2048 2048
        EndSubSection
EndSection
 
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
 
# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

---

### Post by BRRFOC on 2007-11-14
No idea whether this will help, I've been having video display problems with Dell 1704 FPV, and for my Gutsy 7.10 desktop, I changed BIOS video memory setting from 1MB to 8MB and that seemed to do it.  Hope its this easy for you, but if not here is what another user suggested:

FROM USER TRIPTOL posted 11/13/07
You might want to experiment with setting a vga= argument in your /boot/grub/menu.lst (vga=791 for instance).

You might want to check this link: [http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html](http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html)
_

---

### Post by qbert00001 on 2007-11-14
On my nc4010, I was already set at 32MB for video memory.  On a hunch, I doubled it to 64MB, and things *appear* to be running smoother now.  However, Gnome still wants to put things, like dialog boxes of description boxes where they would be for the native laptop display.  However, if increasing the video memory will help with X stability this is a step in the right direction.  

What a bummer though -- my previous install (SuSE 9.2) had no troubles with 32MB...less application RAM.

---

### Post by Triptol on 2007-11-15
If you still have it, you might want to have a look at the xorg.conf that suse produced. You could try by running a live suse from CD/DVD. See if you find any interesting differences...

---

### Post by vbbasti on 2007-11-23
If you have an answer for this problem, please report it. I have the same problem as you!

Greetings Basti

---

