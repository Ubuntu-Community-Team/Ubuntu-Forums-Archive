---
title: "Mouse freezes on right side of screen"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by tesseract1 on 2009-07-27
I just installed my ATI 4850x2 video card using the directions on [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

I restart my computer like it said.  When Ubuntu loaded, my mouse kept freezing when it reached the right side of the screen.  Ie, where the scroll bars for applications is.  It stops for a few seconds and is able to move again.  But whenever I bring my mouse back to the right side of the screen it behaves this way.  It's very annoying and I cannot find any solution to this.

This is my xorg.conf file:
[INDENT]```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    BusID       "PCI:4:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:5:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```
[/INDENT]

---

### Post by scrooge_74 on 2009-07-27
I think you are going to have a lot of problems with that ATI, you may need to use 8.04 instead of the latest Ubuntu.

---

### Post by tesseract1 on 2009-07-27
Could it be that it is searching for a second monitor because I don't have a second monitor.

---

### Post by scrooge_74 on 2009-07-29
Sorry I have no clue since I dont have any ATIs or 9.04 around.

Did you disable all the desktops effects?

---

### Post by tesseract1 on 2009-07-29
I found that commenting out this line:

Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"

Fixed the issue.  I don't know how it got there nor do I know what the line is for.

---

### Post by scrooge_74 on 2009-07-30
Maybe it was thinking you have two monitors

---

