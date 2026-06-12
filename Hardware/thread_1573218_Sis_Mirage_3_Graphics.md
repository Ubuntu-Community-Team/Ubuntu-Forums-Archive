---
title: "Sis Mirage 3 Graphics"
date: 2010-09-12
forum: Hardware
---

### Post by india.shashwat on 2010-09-12
I am completely new to LINUX environment and have installed Ubuntu first time.

My Actual Display resolution is 1280 x 800.

But I am getting only 800 x 600 as a max display resolution in Monitor Setting. My monitor is also showing as Unknown Monitor.

How can I install graphics drive in my laptop...? be remember i am new to ubuntu.

one more thing is that, I have downloaded Graphics driver for LINUX from SIS website but its extension is "o-402". Its a 234 KB file. may be this my Driver..?

---

### Post by kuro_kid on 2010-09-12
read this thread [http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38) it explain how to work with this vga step-by-step.
hope it will help you. Just ask if you have any problem.

---

### Post by india.shashwat on 2010-09-12
Thanks

But please keep an eye on my thread. I may ask anything if needed.

---

### Post by kuro_kid on 2010-09-12
sure, i will help you till you can get 1280x800 resolution

---

### Post by sanderj on 2010-09-12
Ouch. A S3 video chipset. I once had a laptop with a S3 video chipset. You had to beg S3 employy Barros Lee to get a (binary) driver, which I never got ... :-(

That was the last time I bought a laptop with a non-open video chip driver.

---

### Post by india.shashwat on 2010-09-12
> **kuro_kid said:**
> sure, i will help you till you can get 1280x800 resolution
I complete it all as given. But still I am getting 800 x 600. I try the complete again. But from now on when I stop gdm servce then an message occurs saying something like 'Your window will be resume after one minute. I pressed OK. then I can see console window but before them I was blind till start gdm service. Please help..

---

### Post by india.shashwat on 2010-09-12
I type "[FONT=Courier New][COLOR=Red]sudo apt-get install miredo[/COLOR][/FONT]". Everything got complete.
What should i do now..?

---

### Post by india.shashwat on 2010-09-12
> **india.shashwat said:**
> I type "[FONT=Courier New][COLOR=Red]sudo apt-get install miredo[/COLOR][/FONT]". Everything got complete.
What should i do now..?
I go to ipv6.google.com. Its looking same as google.com

What to do now..? please reply..?

---

### Post by india.shashwat on 2010-09-12
> **sanderj said:**
> Ouch. A S3 video chipset. I once had a laptop with a S3 video chipset. You had to beg S3 employy Barros Lee to get a (binary) driver, which I never got ... :-(

That was the last time I bought a laptop with a non-open video chip driver.
I downloaded a file from SIS website named "sis_drv.o-402". is this my binary driver..? if yes then how to install that...? help me soon..

---

### Post by sanderj on 2010-09-12
> **india.shashwat said:**
> I go to ipv6.google.com. Its looking same as google.com

What to do now..? please reply..?

Congratulations ... you now have IPv6 connectivity. (which does not have to do with your S3 problem).

---

### Post by india.shashwat on 2010-09-12
I am getting an Error message (Titled Ubuntu is running in low graphics mode) every time i boot.

Msg contains:

The following errors encountered. You may need to update your configuration to solve this.

(EE) open/dir/fb0 No such file or directory
(EE) Screen(s) found, but none have a usable configuration.


Please help me.. cant work at 800 x 600 resolution..

---

### Post by kuro_kid on 2010-09-13
can you post your /etc/X11/xorg.conf

---

### Post by india.shashwat on 2010-09-13
Section "ServerLayout"
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
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "dri2"
    Load  "glx"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card0"
    Driver      "fbdev"
    VendorName  "Silicon Integrated Systems [SiS]"
    BoardName   "771/671 PCIE VGA Display Adapter"
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

---

### Post by india.shashwat on 2010-09-13
Check my thread
[http://ubuntuforums.org/showthread.php?t=1573218](http://ubuntuforums.org/showthread.php?t=1573218)
I posted the content inside file..

---

### Post by kuro_kid on 2010-09-13
[solved].

---

