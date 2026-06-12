---
title: "ATI Mobility Radeon 9000, where to get driver?"
date: 2009-12-11
forum: Hardware
---

### Post by gypsumwolf on 2009-12-11
I am trying to get 3D to work properly on a Toshiba Satellite A85-107.

Here is the complete system specs: [pdf]("http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A85-S107.pdf").

Its a ATI Mobility Radeon 9000. In the sysinfo program it tells me that it is a ATI Mobility 9200 IGP.

I have tried to run celestia which does not run well, stellarium does not even try to run, but 3d screen savers run, some of them just fine others are choppy and some don't look like they fully loaded correctly.

---

### Post by lewisforlife on 2009-12-11
I have the same card.  I have had pretty good luck with the open source ATI driver in Ubuntu 9.04 (no such luck in 9.10).  There are some games that I have issues with but most work great.  ATI quit linux support for this chipset a long time ago, so I have heard that it is not possible to install the offical ATI driver unless you are running pre-ubuntu 6.04.

---

### Post by RedSingularity on 2009-12-11
Have you looked in System>Admin>Hardware drivers?  Your driver may be listed in there.

---

### Post by jocko on 2009-12-11
> **RedSingularity said:**
> Have you looked in System>Admin>Hardware drivers?  Your driver may be listed in there.
No it won't. Amd/ati does not support cards older than the radeon HD cards...

---

### Post by gypsumwolf on 2009-12-11
> **jocko said:**
> No it won't. Amd/ati does not support cards older than the radeon HD cards...

Its definitely not there.

I don't know what I am talking about but maybe there could be a wrapper for windows graphics cards (like the wrapper for windows network card drivers ndiswrapper.)?

Or is there a driver for debian 5? and if so can I use it for ubuntu 9.10?

---

### Post by jocko on 2009-12-12
> **gypsumwolf said:**
> Its definitely not there.

I don't know what I am talking about but maybe there could be a wrapper for windows graphics cards (like the wrapper for windows network card drivers ndiswrapper.)?

Or is there a driver for debian 5? and if so can I use it for ubuntu 9.10?
The last proprietary driver that supported your card was released by ati in august 2006. Since debian 5.0 (just like ubuntu 9.10) is a modern distro it's kernel and xserver is too new to run the older proprietary driver. 
So you are stuck with the open source driver (named "radeon"), which supports your card really well and is installed and used by default in ubuntu. In fact I think the current version of the open source driver probably performs *a lot* better than the old proprietary driver ever did.
But you may need to change some of the default settings to get it performing better.
One thing to try is this:
First back up your current xorg.conf (if you have one):
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Don't worry if it tells you the file does not exist, as it only exists if you have created it.
Then make a new xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
copy+paste this into the file that opens:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
EndSection

Section "Device"
        Identifier    "Card0"
        Driver        "radeon"
        Option        "EnableDepthMoves"     "True"
        Option        "EnablePageFlip"       "True"
        Option        "DMAForXv"             "True"
        Option        "AccelDFS"             "True"
        Option        "ColorTiling"          "True"
        Option        "RenderAccel"          "True"
        Option        "VGAAccess"            "True"
        Option        "AccelMethod"          "EXA"
        Option        "DRI"                  "True"
        Option        "MigrationHeuristics"  "greedy"
        Option        "TripleBuffer"         "True"
        Option        "EXAOptimizeMigration" "true"
        Option        "EXANoComposite"       "No"
        Option        "BackingStore"         "true"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    Option     "Accel"    "True"
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Extensions"
    Option "RENDER" "Enable"
    Option "Composite" "True"
    Option "XVideo" "Enable"
    Option "XINERAMA" "False"
EndSection

Section "DRI"
    Mode        0666
EndSection
```
Restart the xserver to load the new settings:
```
sudo service gdm restart
```

If this make things worse, simply removing the xorg.conf will get you back to where you started (you may want to write this down on a piece of paper just in case things gets really bad so you have to boot into recovery mode. But I don't think that's very likely.):
```
sudo rm /etc/X11/xorg.conf
```
Or if you already had a xorg.conf and want to revert to using the old one:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by mirkob on 2010-08-07
I have an old Thinkpad T40 with the Radeon Mobility 9000.
I installed Ubuntu 10.4 and everything was working fine until suddenly when I booted it said
[B]Ubuntu is running in low-graphics mode

Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself.[/B]


I tried this
[http://ubuntuforums.org/showthread.php?t=1506463](http://ubuntuforums.org/showthread.php?t=1506463)
But after installing the 6.33 kernel it would not boot at all.

Then I backed my work and re-installed from scratch and tried the previous poster recomended.
The system boots fine but then only the top of the screen can be open with the mouse. The mouse has no effect on the desktop.

If I remove xorg.conf, then the mouse works fine but the I'm afraid that the "low graphic mode" bug will come back.
Help
Thx

---

