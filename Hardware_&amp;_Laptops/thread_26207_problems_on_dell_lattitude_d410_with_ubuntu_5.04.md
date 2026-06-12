---
title: "problems on dell lattitude d410 with ubuntu 5.04"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by wlx on 2005-04-12
I have installed ubuntu 5.04 on dell lattitude d410,and encountered some questions.
I will appreciate if anyone can help me.

1.  I can't activate the intel 2915 abg wireless card, and ubuntu find the device,but the name is unknown. I have tried to activate it in net-admin,but failure. When I pressed fn+f2 key nothing returned.
2.  I can't hibernate the notebook. Stand by function is ok,but nothing returned when I pressed fn+f1 key. It returned the same result as the stand by function when I clicked the menu:system->logout->hibernate computer.
3. How to connect the second display, for example, lcd, crt or project instrument. It would got a black screen and can't switch back when I pressed fn+f8 key. I have tried the i810switch, but it told me my chipset can't support lcd display. My video card is intel 915GML.

the attachment is result of dmesg command.

---

### Post by wlx on 2005-04-17
question 2 has solved.( I have forgotten setup a swap disk)

question 3 has partly solved with add some parameter in xorg.conf file.

---

### Post by remi on 2005-07-13
Hi, 

I've a Dell D410 too. I must use the vesa driver.
Can you post your xorg.conf please ?

---

### Post by wlx on 2005-07-16
[QUOTE=remi]Hi, 

I've a Dell D410 too. I must use the vesa driver.
Can you post your xorg.conf please ?[/QUOTE]
 This is the contents of my xorg.conf file.
> Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        65536
        Option          "UseFBDev"              "true"
        Option          "MonitorLayout" "CRT,LFP"
        Option          "Clone" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


---

### Post by brim4brim on 2005-07-16
[QUOTE=wlx]question 2 has solved.( I have forgotten setup a swap disk)

question 3 has partly solved with add some parameter in xorg.conf file.[/QUOTE]
 Is your card supported with the ipw2000 driver from Intel?  I have a D810 and that solved my wireless wows.

---

