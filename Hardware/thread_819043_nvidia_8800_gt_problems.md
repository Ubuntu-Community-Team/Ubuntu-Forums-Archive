---
title: "nvidia 8800 gt problems"
date: 2008-06-05
forum: Hardware
---

### Post by midnight0000 on 2008-06-05
Ok, for being a complete ubuntu noob, I managed to get most things set up properly. However, I want to have the cool little desktop compiz/beryl effects enabled. 

This is where I hit a wall. I have an NVIDIA GeForce 8800GT graphics card and the last time I tried to install the drivers for it, my screen freaked the hell out and I had to go into restore mode to fix broken stuff and restart X, all that good stuff.
For the record, it messed up my screen even when I booted to windows instead of ubuntu.

Is there a way that I can get my 8800 to work on my computer without any major problems like this again? I tried a program, downloading drivers, etc... said it can't detect and that its restricted.

Thanks for any help

---

### Post by Unix_Slayer on 2008-06-05
> **midnight0000 said:**
> Is there a way that I can get my 8800 to work on my computer without any major problems like this again? I tried a program, downloading drivers, etc... said it can't detect and that its restricted.


**[COLOR="Red"]You might want to print this out.[/COLOR]**


[B]Download the latest driver from NVidia:
[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
[/B]
**[COLOR="Red"]Step 1[/COLOR]**
        **in terminal window**

```
sudo apt-get install build-essential
```

           **Then :**

```
sudo apt-get remove nvidia*
```


**[this should get rid of all unwanted NVidia drivers. please check /lib/linux-restricted-modules/2.6.24.xx-generic/video and make sure there's no nvidia directory in there. There shouldn't be.] [xx = kernel version]**


[COLOR="DarkOrange"]Step 2[/COLOR]
         **on your keyboard**

**ctrl+alt+backspace**

**Wait for the drop out of X11.**

[COLOR="Blue"]Step 3[/COLOR]

**Login into terminal as yourself. Go to the directory where you downloaded the newest NVidia driver. **

**type :**

```
chmod a+x NVIDIA-Linux-x86-173.14.05-pkg1.run
``` 

**NVIDIA-Linux-x86-173.14.05-pkg1.run = name of the file you downloaded. If it's different, then make corrections.**


[COLOR="LightBlue"]Step 4[/COLOR]

**type in :**

```
sudo sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
```


**Follow directions on the screen.**

[COLOR="Lime"]Step 5
[/COLOR]
[B]Reboot, and you should be good as new. I don't use Envyng, or Compiz. I like a nice clean install of my devices.
[/B]
Good Luck

---

### Post by midnight0000 on 2008-06-06
is there a way to stop X without it logging me out?
whenever i do the stop command or ctl-alt-backspace method, it just logs me out and tells me to log back in, which doesnt help with the install

---

### Post by peitschie on 2008-06-06
Hi!

Short answer, no there is no way to restart X without logging out and in again.

Also, there is an easier method available.  You want to use a nifty little script called "Envy" ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)) which automates the above steps and is written specifically for Ubuntu.

To install this, open a terminal and do
```

sudo aptitude install envyng-gtk

```

Then launch it by entering the following:
```

sudo envyng -g

```

And select to install the Nvidia driver.  It should automatically download the driver, fix your xorg.conf, and then ask you to restart :)

Come back and ask if you have any issues :).  Good luck!

---

### Post by Unix_Slayer on 2008-06-06
> **midnight0000 said:**
> is there a way to stop X without it logging me out?
whenever i do the stop command or ctl-alt-backspace method, it just logs me out and tells me to log back in, which doesnt help with the install

After Step 1, you have to conrtol+Alt+Backspace. It takes you out of X11, otherwise you won't be able to install the NVidia driver.

---

### Post by Unix_Slayer on 2008-06-06
Please do not install Envyng. My way works flawlessly. Envyng just causes more problems, and won't install the newest driver above 169.

---

### Post by midnight0000 on 2008-06-06
> **Unix_Slayer said:**
> Please do not install Envyng. My way works flawlessly. Envyng just causes more problems, and won't install the newest driver above 169.
if i ctl alt backspace, it logs me out. how do i install the driver while logged out? if i log back in, it starts x11 back up again.

---

### Post by Unix_Slayer on 2008-06-06
> **midnight0000 said:**
> if i ctl alt backspace, it logs me out. how do i install the driver while logged out? if i log back in, it starts x11 back up again.


To install the driver, you have to logout, and do it before the X11 start. If X11 is running, you can't install the driver. Remember, we are dealing with Linux here, not Windows. When you install a driver for video in Windows, you have to reboot before the changes take effect. If you follow my steps it will work. I've used this method, and installed many different NVidia cards without a problem.

Step 1
in terminal window  <== means while in X11, in a terminal window. Not out of X11.




Step 2
on your keyboard

ctrl+alt+backspace

Wait for the drop out of X11.  <===== this is where it needs to drop.

---

### Post by jocko on 2008-06-07
ctrl+alt+backspace will RESTART xorg, not just kill it.
To kill xorg without restarting it, you need to type this command:
```
sudo /etc/init.d/gdm stop
```
Or:```
sudo killall gdm
```

---

### Post by Unix_Slayer on 2008-06-07
> **jocko said:**
> ctrl+alt+backspace will RESTART xorg, not just kill it.
To kill xorg without restarting it, you need to type this command:
```
sudo /etc/init.d/gdm stop
```
Or:```
sudo killall gdm
```

I'm using KDE4. Mine just dies on command. And restarts in term with a X.

---

### Post by jocko on 2008-06-07
> **Unix_Slayer said:**
> I'm using KDE4. Mine just dies on command. And restarts in term with a X.
Maybe you should have said that you use kde then, as the thread is labelled [ubuntu] people will assume that any advice you give will work in gnome.
Maybe kdm works different than gdm.

---

### Post by Unix_Slayer on 2008-06-07
**[SIZE="5"]Attention, Attention,[/SIZE]** please only follow these steps if you are using KDE4. Sorry about the misunderstanding.


I don't think it makes a difference. Either way, you drop to term.

---

### Post by stearic on 2008-06-07
> **jocko said:**
> ctrl+alt+backspace will RESTART xorg, not just kill it.
To kill xorg without restarting it, you need to type this command:
```
sudo /etc/init.d/gdm stop
```
Or:```
sudo killall gdm
```

Sense it's kde, you just need to replace kdm with gdm. Unless they changed something with it for kde4, that should be it. Should look like the following.
```
sudo /etc/init.d/kdm stop
```

---

### Post by Unix_Slayer on 2008-06-07
> **stearic said:**
> Sense it's kde, you just need to replace kdm with gdm. Unless they changed something with it for kde4, that should be it. Should look like the following.
```
sudo /etc/init.d/kdm stop
```

My method will work with any X11 program. And it's simple, even the kiddies can do it.

---

### Post by Sabata on 2008-06-09
I just used Unix_Slayer's method for my 8400GS and it worked great! :guitar: Now I can use Google Earth again. :) 

One quick question if I may. My login screen now looks like the top pic instead of the way it normally did as shown in the bottom pic (borrowed from psychocats ;) ). I can't get to "Options" in the bottom corner. How can I fix this? Thanks to all you folks for your help!

After installing the latest NVidia driver

[IMG]http://img263.imageshack.us/img263/1993/login2fl7.png[/IMG]

Before installation

[IMG]http://img516.imageshack.us/img516/9831/login1og6.png[/IMG]

---

### Post by stchman on 2008-06-09
> **midnight0000 said:**
> Ok, for being a complete ubuntu noob, I managed to get most things set up properly. However, I want to have the cool little desktop compiz/beryl effects enabled. 

This is where I hit a wall. I have an NVIDIA GeForce 8800GT graphics card and the last time I tried to install the drivers for it, my screen freaked the hell out and I had to go into restore mode to fix broken stuff and restart X, all that good stuff.
For the record, it messed up my screen even when I booted to windows instead of ubuntu.

Is there a way that I can get my 8800 to work on my computer without any major problems like this again? I tried a program, downloading drivers, etc... said it can't detect and that its restricted.

Thanks for any help

I have an 8800GT and all I did was enable the restricted driver and viola.  All things worked even Compiz.

You don't need to do anything special.  The nvidia-glx-new has everything you need.

---

### Post by stchman on 2008-06-09
> **Unix_Slayer said:**
> **[COLOR="Red"]You might want to print this out.[/COLOR]**


[B]Download the latest driver from NVidia:
[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
[/B]
**[COLOR="Red"]Step 1[/COLOR]**
        **in terminal window**

```
sudo apt-get install build-essential
```

           **Then :**

```
sudo apt-get remove nvidia*
```


**[this should get rid of all unwanted NVidia drivers. please check /lib/linux-restricted-modules/2.6.24.xx-generic/video and make sure there's no nvidia directory in there. There shouldn't be.] [xx = kernel version]**


[COLOR="DarkOrange"]Step 2[/COLOR]
         **on your keyboard**

**ctrl+alt+backspace**

**Wait for the drop out of X11.**

[COLOR="Blue"]Step 3[/COLOR]

**Login into terminal as yourself. Go to the directory where you downloaded the newest NVidia driver. **

**type :**

```
chmod a+x NVIDIA-Linux-x86-173.14.05-pkg1.run
``` 

**NVIDIA-Linux-x86-173.14.05-pkg1.run = name of the file you downloaded. If it's different, then make corrections.**


[COLOR="LightBlue"]Step 4[/COLOR]

**type in :**

```
sudo sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
```


**Follow directions on the screen.**

[COLOR="Lime"]Step 5
[/COLOR]
[B]Reboot, and you should be good as new. I don't use Envyng, or Compiz. I like a nice clean install of my devices.
[/B]
Good Luck

All you need to do is enable the restricted driver.  That is all.

---

### Post by Unix_Slayer on 2008-06-09
> **Sabata said:**
> I just used Unix_Slayer's method for my 8400GS and it worked great! :guitar: Now I can use Google Earth again. :) 

One quick question if I may. My login screen now looks like the top pic instead of the way it normally did as shown in the bottom pic (borrowed from psychocats ;) ). I can't get to "Options" in the bottom corner. How can I fix this? Thanks to all you folks for your help!

After installing the latest NVidia driver

Your resolution might be off. 
Show me the entries in your xorg.conf.

**Congratz btw.... I knew some of you could do it.**

---

### Post by Unix_Slayer on 2008-06-09
> **stchman said:**
> I have an 8800GT and all I did was enable the restricted driver and viola.  All things worked even Compiz.

You don't need to do anything special.  The nvidia-glx-new has everything you need.

Only with some cards. But your missing out on the new improvements from the new driver. Oh well.

---

### Post by Unix_Slayer on 2008-06-09
> **stchman said:**
> All you need to do is enable the restricted driver.  That is all.

Whatever makes your boat float. As long as it worked, that's what is most important.

---

### Post by Sabata on 2008-06-09
> **Unix_Slayer said:**
> Your resolution might be off. 
Show me the entries in your xorg.conf.

Here it is. I run at 1280x1024.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon May 19 00:33:37 PDT 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Hewlett-Packard"
    ModelName      "HP F1703 Flat Panel Monitor"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1792 1344
        Depth       24
        Modes      "1280x1024@60" "1280x960@75" "1280x960@60" "1400x1050@60" "1280x1024@75" "1400x1050@75" "1152x864@75" "1600x1200@65" "1024x768@60" "1600x1200@60" "1024x768@70" "1792x1344@60" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection
```

---

### Post by Unix_Slayer on 2008-06-09
> **Sabata said:**
> Here it is. I run at 1280x1024.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon May 19 00:33:37 PDT 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Hewlett-Packard"
    ModelName      "HP F1703 Flat Panel Monitor"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1792 1344
        Depth       24
        Modes      "1280x1024@60" "1280x960@75" "1280x960@60" "1400x1050@60" "1280x1024@75" "1400x1050@75" "1152x864@75" "1600x1200@65" "1024x768@60" "1600x1200@60" "1024x768@70" "1792x1344@60" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection
```


Try canceling out every other resolution.

#ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
 #   ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
  #  ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
   # ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
   # ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
   # ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
   # ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
   # ModeLine       "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
   # ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
   # ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
   # ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
   # ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
   # ModeLine       "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
   # ModeLine       "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
   # ModeLine       "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
   # ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
   # ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
   # ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection


I just hope your hertz are the right range. Let me know how it goes. **[COLOR="Red"]BUT Save a backup of your xorg.conf[/COLOR]**

go to /etc/X11 and type in term:

```
sudo cp xorg.conf xorg.conf.works
```

Then make your changes. Then you will need a reboot. If you black screen, you can copy your xorg.conf.works.


My config came out really easy:

```
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "LGE"
    ModelName      "LG L194WT"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection
```


It must have been the edid.

---

### Post by Unix_Slayer on 2008-06-09
> **Sabata said:**
> Here it is. I run at 1280x1024.

Also.... did you get that installed on the first shot? Just curious. It seemed to work out well for you.

---

### Post by Sabata on 2008-06-09
> **Unix_Slayer said:**
> Also.... did you get that installed on the first shot? Just curious. It seemed to work out well for you.

Yep. It worked like a champ the first time around. Your instructions were easy to understand and the routine is quick. Too bad I'm such a pitiful typist or it would have been twice as fast. :lol: 

The only slight issue I have is the login screen thingy. It's getting late so I will try your fix tomorrow. BTW, out of curiosity, what is the
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        **[COLOR="Red"]Virtual     1792 1344[/COLOR]**
        Depth       24
```
toward the end of my xorg.conf all about?

Thanks!

---

### Post by Unix_Slayer on 2008-06-10
> **Sabata said:**
> Yep. It worked like a champ the first time around. Your instructions were easy to understand and the routine is quick. Too bad I'm such a pitiful typist or it would have been twice as fast. :lol: 

The only slight issue I have is the login screen thingy. It's getting late so I will try your fix tomorrow. BTW, out of curiosity, what is the
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        **[COLOR="Red"]Virtual     1792 1344[/COLOR]**
        Depth       24
```
toward the end of my xorg.conf all about?

Thanks!

This is mine:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "MultiGPU" "on"
    Option         "SLI" "on"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

I think those virtual numbers could be your login screen problem. **[COLOR="Red"]You could save a copy of your xorg.conf[/COLOR]**, and edit that out to see if it works. Actually that is the problem. Virtual is showing a larger resolution. Either try putting in your real resolution in there and see what happens, or comment out the line. **[COLOR="Red"]_Either way, save your xorg.conf_[/COLOR]**

To backup the conf. Directory is /etc/X11   Then type:

```
sudo cp xorg.conf xorg.conf.hold
```


Let me know how things come out.

---

### Post by Sabata on 2008-06-10
OK, I saved a copy of xcorg.conf, edited the virtual line to 1280 1024, saved, then restarted and things are now back to normal, login screen and all.

Thank you, Mr. Unix_Slayer! :guitar:

---

### Post by Unix_Slayer on 2008-06-11
> **Sabata said:**
> OK, I saved a copy of xcorg.conf, edited the virtual line to 1280 1024, saved, then restarted and things are now back to normal, login screen and all.

Thank you, Mr. Unix_Slayer! :guitar:

No problem. I'm just here to spread the good word. Glad it worked out for you. Enjoy.

---

### Post by midnight0000 on 2008-06-11
yeah, but somehow neither that, envyng or slayer's methods work for me. it always installs the driver, but when i restart everything goes crazy, and i can tell it didnt work right from the start, when even my loading screens are messed up in resolution and alignment.  

another question... ive read in multiple places that if you're running a core 2 duo you should use the 64bit version of the desktop, however, im dual booting with 32 bit xp and have been using the standard 32 bit ubuntu. could this be an issue of any kind or am i actually doing something right?

---

### Post by Unix_Slayer on 2008-06-12
> **midnight0000 said:**
> yeah, but somehow neither that, envyng or slayer's methods work for me. it always installs the driver, but when i restart everything goes crazy, and i can tell it didnt work right from the start, when even my loading screens are messed up in resolution and alignment.  

another question... ive read in multiple places that if you're running a core 2 duo you should use the 64bit version of the desktop, however, im dual booting with 32 bit xp and have been using the standard 32 bit ubuntu. could this be an issue of any kind or am i actually doing something right?

It shouldn't be an issue. Follow the steps again. You might have missed something. I've setup so many people, and clients with the new NVidia driver.... I can do it in my sleep. Maybe you could show us your xorg.conf.  It's in directory /etc/X11

---

### Post by Jive Turkey on 2008-06-12
> **midnight0000 said:**
> yeah, but somehow neither that, envyng or slayer's methods work for me. it always installs the driver, but when i restart everything goes crazy, and i can tell it didnt work right from the start, when even my loading screens are messed up in resolution and alignment.  

another question... ive read in multiple places that if you're running a core 2 duo you should use the 64bit version of the desktop, however, im dual booting with 32 bit xp and have been using the standard 32 bit ubuntu. could this be an issue of any kind or am i actually doing something right?

I tried for a very long time to get the 64-bit driver to work with no luck, the installer had several complaints along the way, the restricted driver version didn't work either.  Imagine scouring the forums for a fix at 640x320 resolution!! Thats OK though, 32 bit works just fine.  You will absolutely have more issues with the 64-bit version of any OS atm.  The extra trouble is probably not worth the small performance increase you would get with x64.

---

### Post by Unix_Slayer on 2008-06-12
> **Jive Turkey said:**
> I tried for a very long time to get the 64-bit driver to work with no luck, the installer had several complaints along the way, the restricted driver version didn't work either.  Imagine scouring the forums for a fix at 640x320 resolution!! Thats OK though, 32 bit works just fine.  You will absolutely have more issues with the 64-bit version of any OS atm.  The extra trouble is probably not worth the small performance increase you would get with x64.

I agree.

---

### Post by chyneymon on 2008-06-12
Thanks Unix_Slayer! I am a noob and admittedly I was intimidated by the black screen when first I executed killall gdm. The 173.14.05 driver is working fine now. Just a question though - you mentioned a perf hack that you were using for this driver? Mind if you explain that a little bit? Thanks again.

---

### Post by tenmoi on 2008-06-12
> I tried for a very long time to get the 64-bit driver to work with no luck, the installer had several complaints along the way, the restricted driver version didn't work either. Imagine scouring the forums for a fix at 640x320 resolution!! Thats OK though, 32 bit works just fine. You will absolutely have more issues with the 64-bit version of any OS atm. The extra trouble is probably not worth the small performance increase you would get with x64..

Ha ha ha. So you don't know how to properly install the driver and you blame 64 bit Oses. Please search the 64 bit subforum to see how people are installing the driver. 

bursting my seam!!!

---

### Post by CLomax on 2008-06-12
I too have this problem; outlined in this thread ==> [http://ubuntuforums.org/showthread.php?t=825059](http://ubuntuforums.org/showthread.php?t=825059)

I was wondering if doing this:

[I]SubSection     "Display"
        Virtual     1440 900 ##1440x900 display #
        Depth       24
EndSubSection[/I]

Would make a difference. Thank you for your help.

---

### Post by midnight0000 on 2008-06-12
ok i MUST be doing at least something right, because i finally got the driver to install. but now my resolution is huge like xbox (800x600) and if i try to enable any graphical effects it just tells me they "cannot be enabled"

how the hell do i fix this? this is getting to the point where everything i do with ubuntu just turns into a graphical disaster

---

### Post by CLomax on 2008-06-13
> **midnight0000 said:**
> ok i MUST be doing at least something right, because i finally got the driver to install. but now my resolution is huge like xbox (800x600) and if i try to enable any graphical effects it just tells me they "cannot be enabled"

how the hell do i fix this? this is getting to the point where everything i do with ubuntu just turns into a graphical disaster

Paste your xorg.conf here; someone might be able to help.
 $sudo gedit /etc/X11/xorg.conf - and paste it all here.

---

### Post by Nikolo on 2008-06-13
Unix_Slayer thank you man! !  You ARE great! It all worked fine even with x86_64 ubuntu :). Really thx pal you helped me solve a major problem I had :)

---

### Post by Unix_Slayer on 2008-06-13
> **chyneymon said:**
> Thanks Unix_Slayer! I am a noob and admittedly I was intimidated by the black screen when first I executed killall gdm. The 173.14.05 driver is working fine now. Just a question though - you mentioned a perf hack that you were using for this driver? Mind if you explain that a little bit? Thanks again.

Perf hack? I don't recall saying that. I did say it was an easy fix to the NVidia new driver issue.

---

### Post by Unix_Slayer on 2008-06-13
> **CLomax said:**
> I too have this problem; outlined in this thread ==> [http://ubuntuforums.org/showthread.php?t=825059](http://ubuntuforums.org/showthread.php?t=825059)

I was wondering if doing this:

[I]SubSection     "Display"
        Virtual     1440 900 ##1440x900 display #
        Depth       24
EndSubSection[/I]

Would make a difference. Thank you for your help.

What's the resolution your looking for on your monitor?

---

### Post by Unix_Slayer on 2008-06-13
> **midnight0000 said:**
> ok i MUST be doing at least something right, because i finally got the driver to install. but now my resolution is huge like xbox (800x600) and if i try to enable any graphical effects it just tells me they "cannot be enabled"

how the hell do i fix this? this is getting to the point where everything i do with ubuntu just turns into a graphical disaster

You have to have super user right to edit the xorg.conf, or the xserver. It won't save to the conf if you don't use sudo in front of it.

---

### Post by Unix_Slayer on 2008-06-13
> **Nikolo said:**
> Unix_Slayer thank you man! !  You ARE great! It all worked fine even with x86_64 ubuntu :). Really thx pal you helped me solve a major problem I had :)

No problem. Glad I could help. Congratz....

---

### Post by CLomax on 2008-06-14
> **Unix_Slayer said:**
> What's the resolution your looking for on your monitor?

1440x900.
Not sure if adding that line would fix my problem though. I know I installed it correctly, I just need to tweak my xorg.conf; I have no idea what to put in though. Any help appreciated, thanks.

Xorg.conf as follows:

[I]Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
      Modes	   
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option	   "NoLogo" "True"
    Option "TripleBuffer" "true"
    Option "RenderAccel" "true"
    Option "AddARGBGLXVisuals" "true"
    Option "AllowGLXWithComposite" "true"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Virtual     1440 900
    EndSubSection
EndSection
[/I]

---

### Post by Unix_Slayer on 2008-06-14
> **CLomax said:**
> 1440x900.


[I]Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Virtual     [COLOR="Red"]1440 900[/COLOR]
    EndSubSection
EndSection
[/I]


This is your problem. Is this the correct resolution your looking for? Some of those Options in Section "Device" should be in Section "Extensions". Also.... those lines with the "true" on the options should be "True". With a captial "T". Otherwise I don't think those options will work. It might take it as false with the lowercase "t". My bottom "Extensions" read as the following:
```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

If your composite isn't enabled, your Option > **CLomax said:**
> "AllowGLXWithComposite" "true" might not be working.

---

### Post by CLomax on 2008-06-14
> **Unix_Slayer said:**
> This is your problem. Is this the correct resolution your looking for? Some of those Options in Section "Device" should be in Section "Extensions". Also.... those lines with the "true" on the options should be "True". With a captial "T". Otherwise I don't think those options will work. It might take it as false with the lowercase "t". My bottom "Extensions" read as the following:
```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

If your composite isn't enabled, your Option  might not be working.

Yes, this is the resolution I'm looking for, is there something I did wrong there, if so could you point me in the right direction, please?

And thank you for the protip with the capital T.

Is there anything else that needs changing? If you're wondering what my problem is exactly the link to another thread is a few posts above ^.

Cheers

---

### Post by midnight0000 on 2008-06-15
here's my xorg.conf

my resolution just keeps shrinking and shrinking... i know i installed the drivers right via Slayer's steps, someone help me get my screen the way it is. i really want a normal resolution with compiz/beryl usable

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
EndSection

---

### Post by tenmoi on 2008-06-16
You'd better do some searching on the forum.

Manually installing the driver is the best way.

[COLOR="Red"]first open synaptics and Completely remove linux-restricted-modules* and nvidia-glx*[/COLOR]

sudo apt-get install build-essential libxft-dev
ctrl + alt + f1
sudo /etc/init.d/gdm stop
sudo sh /path_to_your_nvidia.run # case-sensitivity
accept/OK all the way.
sudo /etc/init.d/gdm restart.

This has never failed, and never will, anyone with nvidia cards.

best of luck!

---

### Post by midnight0000 on 2008-06-16
i did exactly what you said after a complete fresh install of ubuntu. it tells me that the driver was installed successfully but when i restart it starts in low graphics mode and i cant get a resolution higher than 800x600 again. despite it still not working, your method was more to the point (especially since ctrl+alt+f1 helped a hell of a lot more than the backspace one). this will never end

---

### Post by tenmoi on 2008-06-16
> **midnight0000 said:**
> i did exactly what you said after a complete fresh install of ubuntu. it tells me that the driver was installed successfully but when i restart it starts in low graphics mode and i cant get a resolution higher than 800x600 again. despite it still not working, your method was more to the point (especially since ctrl+alt+f1 helped a hell of a lot more than the backspace one). this will never end

THis is sort of weird.

But what does sudo nvidia-settings give you? can you change the resolution with it?

what does glxgears give you? 

Post the contents of your /var/log/nvidia-installer.log

waiting for your post.

Don't know if this could help [http://www.nvnews.net/vbulletin/showthread.php?t=114771](http://www.nvnews.net/vbulletin/showthread.php?t=114771)

---

### Post by edwinw on 2008-06-19
Hi,

This thread has been quite helpful so far, I'm so close to getting my video card working but need a little bit of help still.  I don't have the same video card, my system is an Nforce2 motherboard with integrated Geforce4 MX video, so it uses the 96 series Nvidia driver.

To make a very long story short, I have followed Unix_Slayer's instructions exactly, and the driver appeared to install.  However, like Midnight0000 I only have a low graphics/resolution mode, 800x600.  It looks like glx is not loading.  In reply to tenmoi's questions, "sudo nvidia-settings" gives:

```

ERROR: NV-CONTROL extension not found on this Display.
ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.
ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.
ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

```

"glxgears" gives:

```

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

Here are some possibly relevant portions from /var/log/Xorg.0.log:

```

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.05  Tue Jan 22 20:11:30 PST 2008
(II) Loading extension GLX

<snip>

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

My complete /etc/X11/xorg.conf file is as follows:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Jan 22 19:53:46 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "Monitor"
    Identifier     "BenQ FP737s"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "BenQ FP737s"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

My /var/log/nvidia-installer.log file, as well as my full Xorg.0.log, is a bit big to paste here, but I can provide a link to it if that would help.

In any case, any ideas on how to fix my problem?  Thanks in advance!

---

### Post by tenmoi on 2008-06-19
I did a google search and here's the result: 
[http://www.nvnews.net/vbulletin/showthread.php?t=73278](http://www.nvnews.net/vbulletin/showthread.php?t=73278)

So I think some traces of nvidia driver (the open source version) are still lurking somewhere.

This is the guide on the nvforums

Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

Please note: unfortunately, it has become difficult to keep track of the pre-/post-installation steps required for [K]Ubuntu, and the above instructions may be incomplete. If in doubt, it is recommended that you use your distributor's NVIDIA Linux graphics driver packages, exclusively.

Hope that this'll help you.

---

### Post by martinitime1975 on 2008-06-19
tenmoi,

Thanks for your research, I am going to try this tonight.  I too have been pulling my hair out over this.  I screamed and yelled at my pc so violently that I scared my wife.  

I hope this works, but it doesn't negate the fact that installing/removing a driver package should not be this hard.  It's becoming a serious barrier to Linux adoption, and Nvidia/ATI and Ubuntu really need to  fix this on a permanent basis.  It's hard to show the Microsoft sheep and the Apple acolytes the Compiz bling if we can't even install drivers.   Embarrassing.

---

### Post by edwinw on 2008-06-19
Thanks tenmoi, with your help I've made a lot more progress and have my system working at its full resolution with a caveat.  Anyway, for others that might be having problems, the page and the information you reproduced helped me make a few other tweaks.  In particular:

I had the build tools installed (build-essential package referred to in Unix_Slayer's post), so no problem there.

There may have been a problem with my linux headers.  When I did "apt-get remove nvidia*" earlier, I ended up installing a new kernel version 2.6.24-19 along with its headers.  I noticed that I also had the original 2.6.24-16 kernel and its headers.  Looking more closely at the /var/log/nvidia-installer.log, I noticed that it had some lines referring to the 16 kernel.  So what I did was search for "linux-header" in synaptic and remove everything I could find having to the 2.6.24-16 in the name, both images (actual kernel) and header files.

pkg-config was installed on my system, but I had to install xserver-xorg-dev from synaptic.

All nvidia packages were gone from my installation, but I had to manually remove /etc/init.d/nvidia-kernel.

I had a linux-restricted-modules-common package which I had to remove in synaptic.

I then reran the Nvidia driver installer as root, I got one warning/error, but it seemed to be related to my earlier driver install.  If the above steps were done without the earlier install I guess I wouldn't have any problems.  In any case the driver seemed to compile and install okay.

On my reboot, I got a 1280x1024 screen.  Unfortunately, with desktop effects (compiz) on it was buggy, I was missing title bars and the x server was crashing.  I've turned off desktop effects and it's rock solid as I'm typing now.  I'm going to reinstall compiz and see if I can troubleshoot this.

One question I have is that if I continue running into problems, which log should I look in to diagnose the problem?  Here's the last lines of dmesg, which indicates that compiz is segfaulting, I'll probably be googling as well since this would be more a compiz related problem now.

```

[   47.819743] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   47.820150] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   47.820401] agpgart: Putting AGP V2 device at 0000:02:00.0 into 4x mode
[   57.932385] NET: Registered protocol family 10
[   57.933064] lo: Disabled Privacy Extensions
[   57.933840] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.030181] NET: Registered protocol family 17
[   67.698148] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94
[   67.782120] ieee80211_crypt: registered algorithm 'WEP'
[   68.305687] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94
[   68.328543] SoftMAC: Open Authentication completed with 00:09:5b:a8:b4:94
[   68.474599] eth1: no IPv6 routers present
[   83.582085] eth1: no IPv6 routers present
[  165.742078] compiz.real[5660]: segfault at 00001c4c eip 08055a6d esp bffb0dc0 error 4
[  167.187997] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  167.188360] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  167.188611] agpgart: Putting AGP V2 device at 0000:02:00.0 into 4x mode

```

Thanks again tenmoi for your help!

---

### Post by tenmoi on 2008-06-19
glad I could help.

If a programm is not running you could run it from a console and see what is printed there.

I guess that you have Xgl installed. I read somewhere that it may interfere with normal operations of compiz. So you had better remove it. How? I don't remember so you can do a google and find out for yourself, which I always do.

Here's a sample of my compiz started from a terminal. Mind you compiz is running fine and my card is just a meagre onboard 6100

nam@ubuntu64:~$ compiz
[COLOR=Red]Checking for Xgl: not present[/COLOR]. 
Detected PCI ID for VGA: 00:0d.0 0300: 10de:03d0 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x864) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
[COLOR=Red]Checking for Xgl: not present[/COLOR]. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by martinitime1975 on 2008-06-20
I have had it.  Tenmoi, I followed all of your posts, and I appreciate your efforts.  However, I am still stuck where I was.  An unresponsive system that has to be power cycled to use again.  Here's the symptoms:

After following all the package installs and removals, file deletions, and finally the nvidia install, I either reboot or restart gdm and the following occurs:  the screen goes black, and the system becomes unresponsive.  Mouse and keyboard are ineffective, and monitor does not detect a signal.  I have to power cycle the machine and boot into the recovery kernel to change the video driver to "vesa".  

Keep in mind that I have 2 other computers that work fine with 3d drivers (an AMD system with AGP ATI 9800 pro, and a Dell laptop with ATI x300) and both are running compiz successfully.  So it's not Ubuntu per se, but possibly a combination of both OS and Drivers.  Here's the hardware list for the troubled machine:

Ubuntu Gutsy and Hardy 64 bit (I've tried both)
AMD dual core 3800+
2 GB Dual channel RAM
Nvidia 8600 GT PCI Express card, 256 M 
Biostar NForce4amd based motherboard

I have also tried all the normal methods, checking the restricted check box, installing manually, etc.  Every method results in the same brain exploding conclusion:  a black screen and an unresponsive system.  

Let me know if you want to see any of the associated files/logs.  I really want to get this fixed. It's shameful.

---

### Post by tenmoi on 2008-06-21
I would recommend a [COLOR="Red"]completely clean[/COLOR] reinstall. I know someone is in the habit of keeping a separate /home partition and just doesn't format it on a clean install. The old configuration files are kept back and may interfere.

If you should do a reinstall, remember to [COLOR="Red"]remove --purge[/COLOR] everything nvidia*, linux-restricted-modules*, xserver-xorg-video-nv and see if things work.  

However, it could be a hardware related issue, so you should try swapping the monitor, or update your BIOS to the newest version before doing a reinstall. And this is the newest nvidia driver: [http://www.nvnews.net/vbulletin/showthread.php?t=114955](http://www.nvnews.net/vbulletin/showthread.php?t=114955)

That's all that I could help, for I'm no expert.

---

### Post by edwinw on 2008-06-22
Hey martinitime,

I'm no expert (which is obvious considering the advice I got from tenmoi) but I've learned a little bit in this whole rigamarole with getting the nvidia video to work.  Anyway, if you still have some of your logs after the manual driver install, post your /var/log/nvidia-installer.log file and perhaps also your /var/log/Xorg.0.log (after you've booted into recovery mode after the driver install doesn't work, but before you switch to the vesa driver in xorg.conf) and I'll try taking a look.  Also post the result of "uname -r".

With regard to my own situation, I spoke a little too quickly - I'm actually having stability issues even without desktop effects/compiz turned on, but I think I'll be able to solve the problem eventually.  It's kind of annoying how the video thing can be such a showstopper, I have another older ATI video based system which installed no problem from the CD.  Anyway that seems to be the issue with Linux generally, with the hardware manufacturers not cooperating enough with the Linux community.

---

### Post by Unix_Slayer on 2008-06-22
> **CLomax said:**
> Yes, this is the resolution I'm looking for, is there something I did wrong there, if so could you point me in the right direction, please?

And thank you for the protip with the capital T.

Is there anything else that needs changing? If you're wondering what my problem is exactly the link to another thread is a few posts above ^.

Cheers

What other problems are you experiencing?

---

### Post by Unix_Slayer on 2008-06-22
> **midnight0000 said:**
> here's my xorg.conf

my resolution just keeps shrinking and shrinking... i know i installed the drivers right via Slayer's steps, someone help me get my screen the way it is. i really want a normal resolution with compiz/beryl usable


Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		[COLOR="Red"]Virtual	640	480
		Modes		"640x480@60"[/COLOR]
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
EndSection

Here's your problem in red. If your still having the problem. I'm sorry but I was away on business, and couldn't respond. Anyone still having problems?

---

### Post by Unix_Slayer on 2008-06-22
> **edwinw said:**
> Hi,

This thread has been quite helpful so far, I'm so close to getting my video card working but need a little bit of help still.  I don't have the same video card, my system is an Nforce2 motherboard with integrated Geforce4 MX video, so it uses the 96 series Nvidia driver.

To make a very long story short, I have followed Unix_Slayer's instructions exactly, and the driver appeared to install.  However, like Midnight0000 I only have a low graphics/resolution mode, 800x600.  It looks like glx is not loading.  In reply to tenmoi's questions, "sudo nvidia-settings" gives:



Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "BenQ FP737s"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
[/code]



Try taking out the "1024x768" "800x600" "640x480". You didn't say what your monitors resolution goes to. You would need to remove all of them, and leave the resolution you desire/want. Actually did you try going into your system settings, under display? You might be able to change to your desired resolution. But PLEASE make a backup of your xorg.conf. It's in your /etc/X11 directory.

```
sudo cp xorg.conf xorg.conf.testing
```

---

### Post by Unix_Slayer on 2008-06-22
> **martinitime1975 said:**
> tenmoi,

Thanks for your research, I am going to try this tonight.  I too have been pulling my hair out over this.  I screamed and yelled at my pc so violently that I scared my wife.  

I hope this works, but it doesn't negate the fact that installing/removing a driver package should not be this hard.  It's becoming a serious barrier to Linux adoption, and Nvidia/ATI and Ubuntu really need to  fix this on a permanent basis.  It's hard to show the Microsoft sheep and the Apple acolytes the Compiz bling if we can't even install drivers.   Embarrassing.

It's actually all these get fast driver programs out there. I do it naturally, and don't use these quick fix programs. Yes linux is a PIMA when it comes to drivers installation, but pretty much everything is an easy fix if you know your way around it.

---

### Post by Unix_Slayer on 2008-06-22
> **martinitime1975 said:**
> I have had it.  Tenmoi, I followed all of your posts, and I appreciate your efforts.  However, I am still stuck where I was.  An unresponsive system that has to be power cycled to use again.  Here's the symptoms:

After following all the package installs and removals, file deletions, and finally the nvidia install, I either reboot or restart gdm and the following occurs:  the screen goes black, and the system becomes unresponsive.  Mouse and keyboard are ineffective, and monitor does not detect a signal.  I have to power cycle the machine and boot into the recovery kernel to change the video driver to "vesa".  

Keep in mind that I have 2 other computers that work fine with 3d drivers (an AMD system with AGP ATI 9800 pro, and a Dell laptop with ATI x300) and both are running compiz successfully.  So it's not Ubuntu per se, but possibly a combination of both OS and Drivers.  Here's the hardware list for the troubled machine:

Ubuntu Gutsy and Hardy 64 bit (I've tried both)
AMD dual core 3800+
2 GB Dual channel RAM
Nvidia 8600 GT PCI Express card, 256 M 
Biostar NForce4amd based motherboard

I have also tried all the normal methods, checking the restricted check box, installing manually, etc.  Every method results in the same brain exploding conclusion:  a black screen and an unresponsive system.  

Let me know if you want to see any of the associated files/logs.  I really want to get this fixed. It's shameful.

**I'd like to see your xorg.conf if you would.**

---

### Post by Unix_Slayer on 2008-06-23
Also.... there is a new driver out from NVidia that fixes some of your complaints that I heard.

Version: 173.14.09
Operating System: Linux x86
Release Date: June 11, 2008

Release Highlights

    * Fixed aliased font rendering corruption on X.Org server 1.5.
    * Fixed a display corruption problem driving two dual-link DFPs with Quadro FX 1700 GPUs.
    * Fixed a regression that prevented the X driver from starting on some GeForce FX, 6 and 7 mobile GPUs.
    * Fixed a locale-interaction issue in the nvidia-settings X server configuration file parser.
    * Added preliminary support for Linux 2.6.26.


If your driver is working great! And you have no problems.... Don't install this because you feel the need to have the latest, and greatest. This one fixes some problems, but may cause more problems for people who have running NVidia cards, and have no problems. Just my advice. Take it as you may see fit. I will be testing out the latest drivers this week. I will let you guys know if their is anything that is out of the ordinary.


If anyone is interested.

---

### Post by TomSwift on 2008-06-23
@ Unix_Slayer, I am interested in this thread and appreciate your work.  

I just ordered an 8800GT, and I have been reading different forums for tips on what to do if my install goes south.  I would like to be able to hit the ground running if I do have any problems with the card.

---

### Post by martinitime1975 on 2008-06-27
Hi all,

Thanks for your willingness to help.  I've been really busy at work the past week, but will get you output from all the files you requested by Monday.  I hope we can get to the bottom of this, and maybe submit something to Ubuntu for posting in the wiki.

Thanks

---

### Post by Unix_Slayer on 2008-07-09
I still haven't had a chance to install the new drivers, with the holiday that just passed. Hopefully I will get to it this week.

---

### Post by Kileli on 2008-07-12
Total noob here. when i type
```
sh NVIDIA-Linux-x86-173.14.09-pkg1.run
```
i get this error
> sh NVIDIA-Linux-x86-173.14.09-pkg1.run
Any ideas?

---

### Post by Kileli on 2008-07-12
> **Kileli said:**
> Total noob here. when i type
```
sh NVIDIA-Linux-x86-173.14.09-pkg1.run
```
i get this error

Any ideas?

Sorry i mean i get this error
> sh: Can't open NVIDIA-Linux-x86-173.14.09-pkg1.run


---

### Post by CLomax on 2008-07-13
> **Kileli said:**
> Sorry i mean i get this error

The script doesn't have the necessary permissions to be executed, this can be solved by...

```
sudo chmod +x NVIDIA-Linux-x86-173.14.09-pkg1.run
```
THEN:
[CODE]sh NVIDIA-Linux-x86-173.14.09-pkg1.run[CODE]

Protip: To make it easier, rename *NVIDIA-Linux-x86-173.14.09-pkg1.run* to *nvidia.run* or something of the like.

---

### Post by CLomax on 2008-07-13
> **Kileli said:**
> Sorry i mean i get this error

The script doesn't have the necessary permissions to be executed, this can be solved by...

```
sudo chmod +x NVIDIA-Linux-x86-173.14.09-pkg1.run

sh NVIDIA-Linux-x86-173.14.09-pkg1.run
```


Protip: To make it easier, rename *NVIDIA-Linux-x86-173.14.09-pkg1.run* to *nvidia.run* or something of the like.

---

### Post by Kileli on 2008-07-13
> **CLomax said:**
> The script doesn't have the necessary permissions to be executed, this can be solved by...

```
sudo chmod +x NVIDIA-Linux-x86-173.14.09-pkg1.run

sh NVIDIA-Linux-x86-173.14.09-pkg1.run
```


Protip: To make it easier, rename *NVIDIA-Linux-x86-173.14.09-pkg1.run* to *nvidia.run* or something of the like.


thanks i finally got installed. one other question though when i try to save the configuration it tells me i don't have access how do i fix that?

---

### Post by CLomax on 2008-07-13
> **Kileli said:**
> thanks i finally got installed. one other question though when i try to save the configuration it tells me i don't have access how do i fix that?

Im not even sure myself where the configuration is saved. If it is /etc/X11/xorg.conf I'm thinking of then you should use:

```
Sudo gedit /etc/X11/xorg.conf
```

To open the file. It should let you save after that.

---

### Post by Kileli on 2008-07-13
Thank you everyone for your posts here I have succefully installed the latest NVIDIA drivers and everything works great now i can begin my new learning curve that is ubuntu;)

---

### Post by Nardvark on 2008-07-14
Oki i hate buggin and askin for help but this last 2 weeks ive gone threw forum after forum searching for the awnser.. so far nothing has worked.. i did step by step as unix slayer has explained but for the life of me can not make this work everything i do ends up at a blackscreen.. ask me whatcha need ill try my best but i would have to say im a n00b to linux.. i wanna get away from that company called i think microshaft is there name any help would be greatly apreciated.. thanks Jeff

---

### Post by stchman on 2008-07-14
If you are using Hardy then the repositories have the 169.12 driver already there.

Enable the restricted driver.

If you are using Gutsy or earlier then you will need Envy 0.9.10 and select manual install.  The 169.12 driver option will be there.

No need to install a driver you download from a website.

---

### Post by jon_herr on 2008-07-14
> **stchman said:**
> If you are using Hardy then the repositories have the 169.12 driver already there.

Enable the restricted driver.

If you are using Gutsy or earlier then you will need Envy 0.9.10 and select manual install.  The 169.12 driver option will be there.

No need to install a driver you download from a website.

I was reading this thread in hopes to recover some of the performance I lost when I switched from Gutsy to Hardy....  I used to be able to play CS-Source in linux with performance that was comparable to windows.  Now the performance is horrible.  My display lags so much I can't begin to play.  I know it's something new to Hardy - since this is a triple booted machine Win XP, Win Vista, and Ubuntu Hardy v8.04 64 bit - and I can still play fine in XP.  

This is an AMD Athlon 64 X2, 4 Gig RAM, Dual Nvidia 7600s in an SLI configuration.  Not the hottest on the block, but not junk yet either.

Would compiling the driver manually help?  How can I verify that my SLI setup is working?   I've used nvidia-settings and can't tell if SLI is working or not.  

Again, my performance was MUCH better before Hardy.  I'm bummed.



*** UPDATE ***
I was able to enable SLI using information from this thread:
[http://ubuntuforums.org/showthread.php?t=848748](http://ubuntuforums.org/showthread.php?t=848748)

sudo nvidia-xconfig --sli=On

nvidia x-server settings reports that both cards are enabled and working now in SLI but...

My desktop is 'zippy' now, but game still is slow and un-usable.  

: (

---

### Post by Sean4000 on 2008-07-15
I have a unique issue regarding 7.10 and nvidia's 8800GT. I cannot get any install screen to come up when I have the 8800GT in. I have my 7800GT standing by and I can install 7.10 just fine with it ins but I want the power of the 8800GT. 

If I installed the newest driver after installing 7.10 with the 7800GT, would I be able to then pop in the 8800GT with no problems?

---

### Post by jon_herr on 2008-08-06
Anything new on this front?  

I have verified my performance on the same PC, same hardware using windows and linux...

Windows XP 32 bit / Counterstrike Source:  120 frames per second

Ubuntu Hardy 64 bit : 20 frames per second.
(Yes I'm using the restricted nvidia driver)

This used to be much better in 7.10...   what happened?


Jon

:confused:

---

### Post by midnight0000 on 2008-08-23
i just recently bought a new monitor and installed ubuntu over again and it magically works for me now... had nothing to do with the drivers for my card, i guess it just didnt like my really old shitty monitor

thanks for all the time and effort everyone put in for help though.  

if all of the above doesnt work, maybe its your monitor ;)

---

