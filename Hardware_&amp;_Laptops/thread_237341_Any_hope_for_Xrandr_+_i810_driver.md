---
title: "Any hope for Xrandr + i810 driver?"
date: 2006-08-16
forum: Hardware &amp; Laptops
---

### Post by one_stinky_bum on 2006-08-16
Is there any hope for the Intel 915GM/GMS/910GML tablet PC toting kids who want to use Xrandr to flip the screen upside down without having to restart X? I'm using Xorg 7.0.0 using the i810 driver and even though I have AIGLX+Compiz going I can't get xrandr to work (some claim to have success after compiz). It crashes my Xserver. I'll see if I can post the output here. Do I need to upgrade to Xorg 7.1?

Ok, here I go - typing in xrandr -o left and bracing myself for the huge crash... [-o<

---

### Post by one_stinky_bum on 2006-08-16
Can't get the output of the error even when I do "xrandr -o left > xrandr.txt"
The X server crashes, outputs some stuff to the console and the system hangs with a blank black screen.

---

### Post by ltmon on 2006-08-17
Does the /var/log/Xorg.1.log say anything (the log of the last X server session you started previous to the current one)?

---

### Post by one_stinky_bum on 2006-08-17
I can't attach the file, so it's on pastebin - [http://www.pastebin.us/3267](http://www.pastebin.us/3267) 

I issued an "xrandr -o left" and when the X server crashed I copied the file over to my home directory so that it won't be overwritten or something.

Thanks.

---

### Post by Dougie187 on 2006-08-18
I can't get it to work either. I am using a Toshiba r10 tablet and when ever I use xrandr it freezes my computer and breaks x.

---

### Post by one_stinky_bum on 2006-08-18
does your digitizer work though (I'm guessing it is a Wacom so you're fine).

Mind posting your Xorg log file like I did? Hopefully someone would be around to help soon.

---

### Post by Dougie187 on 2006-08-20
Sure here is my Xorg.conf, It is a wacom and i got the table to work fine. Just whenever i do an xrandr -o right or xrandr -o 1 or anything like that my computer spits out alot of garbage really fast and then the screen just goes blank forever. I wish someone around here has used the screen rotation with an i810 before and can help.

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "GLcore"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dbe"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Intel Corporation 82852/855GM Integrated Graphics Device"
    Driver        "i810"
    Option         "XAANoOffscreenPixmaps"
    Option         "RandRRotation" "True"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-51
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82852/855GM Integrated Graphics Device"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Option         "AIGLX" "true"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
    Option     "Composite" "Enable"
EndSection

---

### Post by Dougie187 on 2006-08-24
Have you gotten anywhere with this yet?

---

### Post by one_stinky_bum on 2006-08-24
I got in touch with a guy who works on the Raven IBM tablet PC that has emperor linux on it. They got it to do X rotation and the tablet works perfectly, but I think it is a Wacom. The guy's email sounded like they are willing to charge me to make the tablet work on my M280... but I'm not willing to pay a penny. I just want to see how much they think that service is worth.

I've planned to look at the source files this weekend and see if I can fix/understand what is going on, before I start shooting emails to the names I find in the source files.

---

### Post by Dougie187 on 2006-08-28
I have my tablet working in linux. I just dont have the screen rotating. I dont know whats wrong with it though.

---

### Post by one_stinky_bum on 2006-08-28
Is your tablet a Wacom or a finepoint?

---

### Post by Dougie187 on 2006-08-30
Mine is a wacom. Yours?

---

### Post by one_stinky_bum on 2006-08-30
mine is a finepoint MP-800 in a Gateway M280.

Still can't get it to work. :(

---

### Post by Dougie187 on 2006-08-31
That sucks. I havent even heard of those. Are they any good? I had looked at getting a gateway but i thought it had a wacom as well. Well hopefully someone will have some solution for your tablet problem. No solution to the xrandr thing yet?

---

### Post by one_stinky_bum on 2006-09-01
Well, I can get "xrandr -o inverted" to work a bit under the latest quinn compiz and aiglx packages: the screen rotates and the mouse moves, but all the UI interface is frozen. Maybe a bug fix is in the works soon? Who knows.

---

### Post by Dougie187 on 2006-09-01
I cant get xrandr to rotate my screen at all. it does one of two things when i run it. It either logs me out. or it freezes the computer and leaves the computer on a black screen saying something about needing a reboot but it never rotates the screen and i have to do a hard reboot

---

### Post by one_stinky_bum on 2006-09-20
any updates anyone? Happily using your tablet? I'm still poking around for information, but nothing has turned up yet.

---

### Post by froghopper on 2006-09-26
I probably should not post here as it will cause a flurry of support requests that I probably not be able to solve but...

You can do on the fly rotation with i810, 855gm to be precise, as I have it working on my R10 Toshiba tablet. I think you need xorg "7.1" and as I had to compile it myself you may be better waiting for Edgy. But don't loose heart.

---

### Post by one_stinky_bum on 2006-09-26
Ha, I never knew people were cautious to post info due to support requests! I'm off to download the latest xorg.

I get screen rotation on my current dapper setup, but the screen freezes after 2 rotations.

---

### Post by qumak on 2006-09-30
just wanted to say that (albeit in gentoo) i have gotten rotation with the i810 driver working great on my gateway cx2610 with xorg 7.1 and v1.6.5 of the i810 driver.  also see my post [here]("http://ubuntuforums.org/showthread.php?p=1563274#post1563274") for info about the finepoint driver.

--qumak

---

### Post by Dougie187 on 2006-10-28
Well here is a little update. For some reason when i upgraded to edgy i can rotate fine. Though I havent got the pen to rotate too, because when i rotate now, the pen stays how it was before and the bottom left is now the top right of the screen (for inverted rotation). Did you get yours working?

---

### Post by one_stinky_bum on 2006-10-31
"xrandr -o inverted" inverts the screen but when I type something it doesn't show. "xrandr -o normal" returns things to the normal screen orientation and typing works again. 

At this rate, I'm not sure when Linux would be ready for tablet PCs.

---

### Post by Dougie187 on 2006-10-31
Ok. So I reinstalled Edgy. Without installing compiz or beryl (which ever you prefer) and the xrandr and xwacomset work perfectly. Now im working on writing a shell script that will check if the screen is in portrait or landscape and then rotate accordingly. And then I will assign that script to one of the tablet buttons.

---

### Post by Dougie187 on 2006-10-31
Ok. So i finished my script. Here is the base code. Not sure if you need to use xwacomset to rotate all the rest of the things yet or not, but just so you get the idea. Granted this will only work if you have xrandr working. And you have to run it once before it works. Also... I am not too familar with linux, so it just uses some file to tell what mode its in and then rotates accordingly. I wanted to use system variables but i dont really know how so i just used links to the rotate script.

#!/bin/bash
if [ -f ~/.landscape ]; then
        xrandr -o left
        xsetwacom set stylus rotate ccw
        unlink .landscape
        link rotate .portrait
elif [ -f ~/.portrait ]; then
        xrandr -o normal
        xsetwacom set stylus rotate
        unlink .portrait
        link rotate .landscape
else
        link rotate .landscape
fi

---

### Post by Zed on 2006-11-18
Of related interest (not useful for dynamically changing rotation), the i810 driver offers this option:

        Option "Rotate" "90"

which, if included in your xorg.conf's Device section will start the screen rotated. I keep my desktop monitor in portrait mode, and it's what I use.

---

