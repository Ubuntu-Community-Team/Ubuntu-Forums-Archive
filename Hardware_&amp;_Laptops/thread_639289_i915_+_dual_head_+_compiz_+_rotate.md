---
title: "i915 + dual head + compiz + rotate"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by Ackowa on 2007-12-13
I'm using a Dell GX280 desktop which uses a intel i915 chipset.

I can get Compiz to work with xrandr on my dual screen setup (2 * DELL 1704 Flatpanels) running 1280*1024 in resolution on each.

My problem is that currently I have to have them above/below eachother to not go over the 2048 pixel max, if I rotate the screens I could set the to be Right/Left of eachother but when running that setup I have a realy high cpu usage on xorg, 50% cpu when moving a term and that is without running compiz.

Anyone that has similar problems/that know how to make it work?

Xorg.conf

Section "Module"
#        Load            "glx"
        Load            "GLcore"
        Load            "dri"
        Load            "v4l"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "DELL P992"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Monitor         "DELL P992"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
                Virtual 2048 2048
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
EndSection

Xrandr commands to add screens over/under eachother:
xrandr --output VGA --rate 60
xrandr --output VGA --off
xrandr --output VGA --auto
xrandr --output TMDS-1 --rotate normal
xrandr --output VGA --rotate normal
xrandr --output VGA --above TMDS-1

Xrandr commands to add screens next to eachother when rotated:
xrandr --output VGA --rate 60
xrandr --output VGA --off
xrandr --output VGA --auto
xrandr --output TMDS-1 --rotate left
xrandr --output VGA --rotate left
xrandr --output VGA --left-of TMDS-1

---

### Post by Ackowa on 2007-12-14
Another queastion: Anyone know how I can save my xrandr settings so that I don't have to set them after each reboot?

---

### Post by motin on 2008-01-26
You need to configure xrandr directly in xorg.conf in order to have them readily available after reboot. Read more here: [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)

---

