---
title: "Nvidia Quadro NVS 140 missing resolutions"
date: 2009-08-15
forum: Hardware
---

### Post by shid007 on 2009-08-15
Hi there, for a long time I have this problem... I have Thinkpad R61 with 1680x1050 screen... The only resolutions that I can choose in nvidia-settings are 1680x1050, 1600x1024, 1440x900, 1280x960, 800x512, 720x450, 640x512 and 640x480. Where are all those resolutions like 1280x800 and 1024x768 gone? That display can show them, on windows I can set them on Linux I can't... Any ideas?

---

### Post by realzippy on 2009-08-15
..you can add your missing resolutions to a "modeline" in your xorg.conf.

[http://www.nvnews.net/vbulletin/showthread.php?t=51994](http://www.nvnews.net/vbulletin/showthread.php?t=51994)

post #2

...further questions?Ask!

---

### Post by realzippy on 2009-08-15
Open nvidia-setttings as root by typing in terminal:

gksudo nvidia-settings

Go to:
X Server Display Configuration
Go to:
X Screen tab
Hit button next to MetaMode
Choose your desired resolution
apply
save to X Configuration File

---

### Post by shid007 on 2009-08-15
Well... I changed my xorg.conf so that my monitor section looks now like this:```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
    Modeline "1024x768@60" 64.56 1024 1056 1296 1328 768 783 791 807
EndSection
```

but nothing has changed... I think that nvidia-settings stores its configuration somewhere else...

---

### Post by realzippy on 2009-08-15
[COLOR="SeaGreen"]Option "metamodes" "1024x768_60 +0+0; nvidia-auto-select +0+0"
[/COLOR]

Put this line in the "screen section",under default depth = 24.
If your Xserver does not start then,go to terminal (Alt+Ctrl+F3),
open editor and delete it:

sudo nano /etc/X11/xorg.conf

or backup before and replace:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup 
to backup    
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
to use backup in case of no Xserver
     

Did you try do add metamode with nvidia-settings?:

gksudo nvidia-settings

Go to:
X Server Display Configuration
Go to:
X Screen tab
Hit button next to MetaMode
Choose your desired resolution
apply
save to X Configuration File

---

### Post by shid007 on 2009-08-16
Well this doesn't work either...
I have my xorg.conf like this... and nothing happend...
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Option "metamodes" "1024x768_60 +0+0; nvidia-auto-select +0+0"
    EndSubSection
EndSection

```

Maybe I have an old version of nvidia-settings utility... when I click on add metamode it just duplicates what is selected right now... the metamode, you tell me to select isn't listed... I don't have 1024x768 in there... :( 

...Anyway, thanks!

Edit: my bad... I put it to wrong place... gonna try to change it ...

Edit2: actually it doesn't work either

---

### Post by realzippy on 2009-08-16
hm.
Have a look here:

[http://baudizm.blogsome.com/2005/09/27/ignoring-edid-to-impose-higher-resolution/](http://baudizm.blogsome.com/2005/09/27/ignoring-edid-to-impose-higher-resolution/)


Section &#8220;Device&#8221;
Identifier &#8220;your graphics card model&#8221;
Driver &#8220;your graphics card driver&#8221;
BusID &#8220;PCI:1:0:0&#8243;
[COLOR="SeaGreen"]Option &#8220;IgnoreEDID&#8221; &#8220;true&#8221;[/COLOR]
EndSection


...I'm pretty shure that you have to disable the monitor's edid detection some way in the xorg.conf
This I found also:

[http://www.thinkwiki.org/wiki/Install_Ubuntu_Intrepid_Ibex_on_a_T61p#EDID_misdetection](http://www.thinkwiki.org/wiki/Install_Ubuntu_Intrepid_Ibex_on_a_T61p#EDID_misdetection)

EDID misdetection

EDID (Extended Display Identification Data) might be misdetected for your display, which reduces the number of resolutions available in the NVidia X Server Settings application. (For example, I was unable to set my laptop's screen to 1024x768 for use with a projector during a presentation.) If you encounter this problem, add the following lines to /etc/X11/xorg.conf in the "Screen" section:

Option "UseEdidFreqs" "FALSE"
Option "HorizSync" "40-70"

Please test both xorg.conf entries,would start with second suggestion cause it's pretty similar to your problem.
Option "UseEdidFreqs" "FALSE"  and  Option &#8220;IgnoreEDID&#8221; &#8220;true&#8221;
should be the same.
Test this "screen" section :

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Option "UseEdidFreqs" "FALSE"
        Option "metamodes" "1024x768_60 +0+0; nvidia-auto-select +0+0"
    EndSubSection
EndSection

---

### Post by shid007 on 2009-08-22
Thanks!!! It worked I have changed my xorg.conf to this:```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "IgnoreEDID" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Option "UseEdidFreqs" "FALSE"
        Option "HorizSync" "40-70"
        #Option "metamodes" "1024x768_60 +0+0; nvidia-auto-select +0+0"
    EndSubSection
EndSection

```

I had to comment that metanodes line, because it was causing strange things :) but now I can select all resolutions I can think of:) Thanks!:)

Edit: Do you know how to mark this thread as Solved ?

---

