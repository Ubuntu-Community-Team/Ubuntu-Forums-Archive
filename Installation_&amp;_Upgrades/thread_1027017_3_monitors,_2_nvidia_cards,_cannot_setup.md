---
title: "3 monitors, 2 nvidia cards, cannot setup"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by ainacio on 2008-12-31
I have the following setup:

2 monitors connected to one 9500 on PCI:3:0:0
1 monitor connected to the other 9500 on PCI:2:0:0

I can install 8.10 out of the box (with one monitor working on PCI:2:0:0). However, when I update the driver, and restart, the system goes into text mode as X refuses to start. 

I have tried the following:
 
1. installing 8.04.1 ::Results:: This failed. I do not have a floppy, the installer did not want to recognize my SATA DVD drive. I didn't want to spend too much time on this because I would rather install 8.10. I was going this route for a short time because I wanted to see if I could get the setup working, and copy the xorg.conf file... but I decided to try and edit it manually. 

2. editing /etc/X11/xorg.conf (I tried to specify the BusID... I also tried to specify different permutations and combinations of what other people said worked for them) ::Results:: This resulted in my system totally not responding and forcing me to go to recovery mode to change the file back.

3. using Envy Software ::Results:: I had a python run time exception

4. popping one card out  one card. ::Results:: I was able to install the new drivers. It seemed to work well; however, when I installed the 2nd card, I went right back to square one. 

5. When I was in the Text Mode, I tried running the Nvidea driver which I downloaded from their website... I could run the installer successfully, but it did not want to boot X when I restarted. I also read their driver README file and found an option for disabling the boot up of all other drives (Option "UseInt10Module" "True"), I tried this command but it did not get me anywhere. I also tried combinations of this and specifying the BusID. 

Has anyone encountered this issue? Any solutions?

---

### Post by ainacio on 2009-01-01
** Update **

Ok, so i installed the Nvidia driver again. When my system went into TTY, I edited the xorg.conf file to specify the bus of my main video card. I ran startx, and it went into into the GUI. When I restarted, it got stuck on the line:

Checking battery state...  [OK]

If I press ctrl + alt + F2, I can get into TTY and run startx.

Why is it getting stuck at Checking battery state... ?

---

### Post by ainacio on 2009-01-01
**Update**

- I reformatted the system
- Installed 8.10
- Installed required updates... restarted with everything working.
- Installed the 177 Nvidia driver

Results: Same Issue... cannot get into X normally. 

When I start the System, it hangs at 'Checking battery...     [ OK ]' 

I can get into the GUI if I go to TTY2 and start X manually with startx... as mentioned above. 

Does anybody know why the Nvidia driver is causing these issues?

---

### Post by ainacio on 2009-01-01
bump

---

### Post by ainacio on 2009-01-03
bump

---

### Post by John von Neumann on 2009-01-03
I am having *precisely* the same problem. Sorry I can't offer any help.

---

### Post by ainacio on 2009-01-04
> **John von Neumann said:**
> I am having *precisely* the same problem. Sorry I can't offer any help.

bump

---

### Post by dninja on 2009-01-04
> **ainacio said:**
> bump

Mine works ok. I installed envy ng and told it to install my nvidia drivers then used an xorg.conf that has always worked fine for me in Arch Linux.

My cards are a pair of 8600GTs so not quite the same as yours but hopefully this will help.

```
Section "Screen"
        Identifier      "Screen0"
        Device          "Videocard0"
        Monitor         "Monitor0"
        Option          "TwinView"      "0"
        Option          "metamodes"     "DFP: nvidia-auto-select +0+0"
        Option          "PixmapCacheSize"       "1000000"
        Option          "AllowSHMPixmaps"       "0"
        Option          "AddARGBGLXVisuals"     "True"
        SubSection "Display"
                Depth   24
        EndSubSection
        Defaultdepth    24
EndSection

Section "Screen"
        Identifier      "Screen2"
        Device          "Videocard1"
        Monitor         "Monitor2"
        Option          "TwinView"      "0"
        Option          "metamodes"     "CRT: nvidia-auto-select +0+0"
        Option          "PixmapCacheSize"       "1000000"
        Option          "AllowSHMPixmaps"       "0"
        Option          "AddARGBGLXVisuals"     "True"
        SubSection "Display"
                Depth   24
        EndSubSection
        Defaultdepth    24
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Videocard2"
        Monitor         "Monitor1"
        Option          "TwinView"      "0"
        Option          "metamodes"     "nvidia-auto-select +0+0"
        Option          "PixmapCacheSize"       "1000000"
        Option          "AllowSHMPixmaps"       "0"
        Option          "AddARGBGLXVisuals"     "True"
        SubSection "Display"
                Depth   24
        EndSubSection
        Defaultdepth    24
EndSection

Section "Device"
        Identifier      "Videocard0"
        Driver          "nvidia"
        Vendorname      "NVIDIA Corporation"
        Boardname       "GeForce 8600 GT"
        Busid           "PCI:5:0:0"
        Screen  0
EndSection

Section "Device"
        Identifier      "Videocard1"
        Driver          "nvidia"
        Vendorname      "NVIDIA Corporation"
        Boardname       "GeForce 8600 GT"
        Busid           "PCI:5:0:0"
        Screen  1
EndSection

Section "Device"
        Identifier      "Videocard2"
        Driver          "nvidia"
        Vendorname      "NVIDIA Corporation"
        Boardname       "GeForce 8600 GT"
        Busid           "PCI:4:0:0"
EndSection

Section "InputDevice"
        # generated from default
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "Protocol"      "auto"
        Option          "Device"        "/dev/psaux"
        Option          "Emulate3Buttons"       "no"
        Option          "ZAxisMapping"  "4 5"
EndSection

Section "InputDevice"
        # generated from default
        Identifier      "Keyboard0"
        Driver          "kbd"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection
 Section "ServerLayout"
        Identifier      "Layout0"
  screen 0 "Screen0" leftof "Screen2"
  screen 1 "Screen1" rightof "Screen2"
  screen 2 "Screen2" 1280 0
        Inputdevice     "Keyboard0"     "CoreKeyboard"
        Inputdevice     "Mouse0"        "CorePointer"
EndSection

Section "Module"
        Load            "dbe"
        Load            "extmod"
        Load            "type1"
        Load            "freetype"
        Load            "glx"
EndSection

Section "Monitor"
        # HorizSync source: edid, VertRefresh source: edid
        Identifier      "Monitor0"
        Vendorname      "Unknown"
        Modelname       "BenQ FP91G+"
        Horizsync       31.0    -       83.0
        Vertrefresh     56.0    -       76.0
        Option          "DPMS"
EndSection

Section "Monitor"
        # HorizSync source: edid, VertRefresh source: edid
        Identifier      "Monitor2"
        Vendorname      "Unknown"
        Modelname       "Maxdata (RogenTech) Bel2225S1W"
        Horizsync       30.0    -       84.0
        Vertrefresh     55.0    -       77.0
        Option          "DPMS"
EndSection

Section "Monitor"
        # HorizSync source: edid, VertRefresh source: edid
        Identifier      "Monitor1"
        Vendorname      "Unknown"
        Modelname       "QVA LM-191M"
        Horizsync       31.0    -       80.0
        Vertrefresh     60.0    -       75.0
        Option          "DPMS"
EndSection

Section "ServerFlags"
        Option          "Xinerama"      "1"
        Option          "AutoAddDevices"        "false"
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

Section "Files"
        #RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

```

This was a lot to cut and paste in, hopefully I've not missed anything.

---

### Post by dninja on 2009-01-04
> **ainacio said:**
> bump

Should have just included the file. Sorry.

---

### Post by John von Neumann on 2009-01-14
I managed to get this fixed. I added the following line to the "Device" section in xorg.conf, which contained my primary video card:

Busid "PCI:1:0:0"

To find the correct busid, run lspic. Everything works as normal now. The problem is related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241").

---

### Post by John von Neumann on 2009-01-16
Sadly, this caused more problems. When I tried to launch anything on the 2nd x-screen, I got a pop up box with no text and the pc would hang.

This seems crazy - all used to work perfectly in 8.04.

---

