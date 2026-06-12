---
title: "Screen Resolution with Xorg.conf"
date: 2013-07-14
forum: Hardware
---

### Post by Sarcastic Cows on 2013-07-14
Hi everyone, I'm trying to change the default screen resolution for my monitor. I'm using a Radeon 5450 GPU but I'm using the open source drivers after no luck with installing the proprietary ones. 

I'm trying to change the resolution with Xorg.conf, but the screen resolution won't change from 1024x768.

[http://pastebin.com/ZvRyCRj8](http://pastebin.com/ZvRyCRj8)

^That's the Xorg.conf, however I've changed the card for Card1 after seeing that needed to be changed.

Any help would be apprieciated.

---

### Post by jp734 on 2013-07-14
How many monitirs are you using? Is this a 4 screen setup?

---

### Post by Sarcastic Cows on 2013-07-14
No, just 1. 

I don't know why Xorg has several items for each section

---

### Post by jp734 on 2013-07-14
Below is your revised xorg.conf file. Removed sections that are not needed for 1 monitor setup. You can try if you want but don't forget to make a backup copy of your existing one.

>     Section "ServerLayout"
            Identifier     "X.org Configured"
            Screen      0  "Screen0" 0 0
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
            Load  "glx"
    EndSection
     
    Section "InputDevice"
            Identifier  "Keyboard0"
            Driver      "kbd"
    EndSection
     
    Section "InputDevice"
            Identifier  "Mouse0"
            Driver      "mouse"
            Option      "Protocol" "auto"
            Option      "Device" "/dev/input/mice"
            Option      "ZAxisMapping" "4 5 6 7"
    EndSection
     
    Section "Monitor"
            Identifier   "Monitor0"
            Option "PreferredMode" "1366x768"
            HorizSync       30-80
            VertRefresh     55-75
            #Modeline "1368x768_60.00" 85.86 1368 1440 1584 1800 768 769 772 795 -HSync +Vsync
    EndSection

    Section "Device"
            ### Available Driver options are:-
            ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
            ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
            ### <percent>: "<f>%"
            ### [arg]: arg optional
            #Option     "NoAccel"                   # [<bool>]
            #Option     "SWcursor"                  # [<bool>]
            #Option     "EnablePageFlip"            # [<bool>]
            #Option     "AccelDFS"                  # [<bool>]
            #Option     "IgnoreEDID"                # [<bool>]
            #Option     "ColorTiling"               # [<bool>]
            #Option     "ColorTiling2D"             # [<bool>]
            #Option     "RenderAccel"               # [<bool>]
            #Option     "SubPixelOrder"             # [<str>]
            #Option     "AccelMethod"               # <str>
            #Option     "DRI"                       # [<bool>]
            #Option     "TVStandard"                # <str>
            #Option     "EXAVSync"                  # [<bool>]
            #Option     "EXAPixmaps"                # [<bool>]
            #Option     "ZaphodHeads"               # <str>
            #Option     "EnablePageFlip"            # [<bool>]
            #Option     "SwapbuffersWait"           # [<bool>]
            Identifier  "Card0"
            Driver      "radeon"
            BusID       "PCI:1:0:0"
    EndSection
     
    Section "Screen"
            Identifier "Screen0"
            Device     "Card0"
            Monitor    "Monitor0"
            DefaultDepth    24
            SubSection "Display"
                    Depth     24
                    Modes   "1366x768"
            EndSubSection
    EndSection

---

### Post by Sarcastic Cows on 2013-07-14
Thanks I'll try that.

---

### Post by Sarcastic Cows on 2013-07-14
> **jp734 said:**
> Below is your revised xorg.conf file. Removed sections that are not needed for 1 monitor setup. You can try if you want but don't forget to make a backup copy of your existing one.

It hasn't changed the screen resolution, but hasn't broken the system either, which all of my previous attempts have :P

---

### Post by jp734 on 2013-07-14
Check your xorg.0.log and see what's causing it not set it to 1366x768. Maybe it's not even using the configuration file. Sometimes that happens.

---

### Post by Sarcastic Cows on 2013-07-14
[http://pastebin.com/sc7PBT21](http://pastebin.com/sc7PBT21)

There's my xorg.0.log.

---

### Post by jp734 on 2013-07-14
What kind of monitor do you have and have you tried using xrandr?

---

### Post by Sarcastic Cows on 2013-07-14
I have an Acer S191HQL, and I've used xrandr to temporarily fix the problem but not to permanently fix the problem

---

### Post by jp734 on 2013-07-14
If you were able to fix the problem using xrandr, then I'll just use that. Create a script and call the script everytime you boot the pc.

---

### Post by Sarcastic Cows on 2013-07-14
Hi, do I use the #! /bin/bash? After that what do I type? The xrandr commands?

---

### Post by jp734 on 2013-07-14
Yup, then just save the script on your **/etc/xdg/autostart** folder. Don't forget to make it executabe and then make sure it is selected (check marked) to start up on boot.

Not sure what OS you're using but I'm using lubuntu and I can select what I want to start on boot when I go to **Preferences>Desktop Session Settings**

---

### Post by Sarcastic Cows on 2013-07-14
*Bekks *on the #ubuntu IRC channel told me that in the modeline I'd specifed 85 as the vertical refresh and that was contradictory to my VertRefresh line. Thanks for your time, however, jp734

---

### Post by Sarcastic Cows on 2013-07-14
OK, it's back to normal for some reason. It seems like the changes to xorg.conf aren't taking place

---

### Post by Sarcastic Cows on 2013-07-14
Double post. Sorry

---

### Post by jp734 on 2013-07-15
Seems like we're going to have to use xrandr. Before you do that though, is there a monitor configuration under /usr/share/X11/xorg.conf.d?

---

### Post by Sarcastic Cows on 2013-07-15
> **jp734 said:**
> Seems like we're going to have to use xrandr. Before you do that though, is there a monitor configuration under /usr/share/X11/xorg.conf.d?

Inside the xorg.conf.d, I can't see anything related to the monitor - only for the other devices

---

### Post by jp734 on 2013-07-15
Seem to me like xrandr will be your solution.

---

### Post by Sarcastic Cows on 2013-07-15
Never mind. Adamk on the IRC channel told me firstly that there was no modeline, secondly the modeline's screen resolution wasn't the same as the preferredmode line, and thirdly he gave me a barebones xorg.conf with just the monitor section. 

[http://pastebin.com/KSKDU1tx](http://pastebin.com/KSKDU1tx)

That was what he gave me.

---

