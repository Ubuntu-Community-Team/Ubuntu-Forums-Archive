---
title: "Kubuntu startup resolution (Solved)"
date: 2005-11-19
forum: General Help
---

### Post by benjordan06 on 2005-11-19
hi everyone,

I am a new kubuntu user.  I have been using linux off and on for quite some time now.

I am having a problem with KDM resolution being around 640x480 and I cant find where I can change this.  It also propagates into KDE and I have to change the resolution there.

Does anyone know where I can permanently set KDM resolution?

Thanks!

---

### Post by sto6ma9ch on 2005-11-19
The resolution will depend on the type of driver you're using with your video card and what it supports. You can find out which driver's being used by checking the /etc/X11/xorg.conf file. Look for a section like this:
```
# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###

```
What kind of video card do you have?

---

### Post by benjordan06 on 2005-11-19
hey,

I am using fglrx driver with radeon 9800 pro.  I think when I installed the driver, the problem started.

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver ha
s its own code for mtrr
# ### FireGL DDX driver module specific settings ###
                                                                416,1         79%
# === Screen Management ===
    Option "DesktopSetup"               "(null)"
    Option "ScreenOverlap"              "0"
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
   Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e48
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "800x600" "1024x768" "1280x1024" "1600x1200"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
        #Virtual     1280 1024
    EndSubsection
EndSection


I am trying to set my default resolution to 1280x1024...

Thanks!

---

### Post by sto6ma9ch on 2005-11-19
Looks like you've installed the ATI driver from their website and that all of your resolutions are there.

I'd like you to check something:
[LIST]
[*]Go to System Settings -> Display
[*]Select your screen size from the drop-down menu (in this case, 1280 x 1024)
[*]Check the "Apply settings on KDE startup" box
[*]Restart your computer
[/LIST]

See if your resolution is higher.

---

### Post by benjordan06 on 2005-11-19
I have tried that.  It *does* apply the correct resolution after logging into KDE.  However, KDM is still extremely low resolution and i have to pan around my screen to find the login prompt. :(

Thanks for the effort, 
Ben

---

### Post by sto6ma9ch on 2005-11-19
From what I've Googled, KDM will get it's resolution from Xorg; there are no settings within KDM. If you have that "Apply settings on KDE startup" box checked, then it looks like Xorg is setting the initial resolution very high, and KDE is changing it to 1280 x 1024. You could always disable any resolution higher than 1280 x 1024. It's not really a fix, but it should give you the desired results.

Backup your current configuration . . .
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
. . . reconfigure Xorg . . .
```
dpkg-reconfigure xserver-xorg
```
. . . and do not select any resolution higher than 1280 x 1024.

Let us know what happens.

---

### Post by benjordan06 on 2005-11-19
hi again,

sorry for the lack of speedy replies :P... been busy with some house projects..

I configured xorg with fglrxconfig from ATI... I suppose i could use xorg to configure and then manually change the driver to fglrx.

However, I think I will just remove the other resolutions for the server to choose from.  That will work for me.  I do not need to change resolutions often.

Thanks for your help,
Ben

---

### Post by vh1 on 2005-11-20
X tries each resolution on the Modes line in order and goes with whatever works first

which, in your case, is 800x600

all you have to do is reverse the resolutions you have listed and it should work fine

---

### Post by benjordan06 on 2005-11-20
ahh,  thankyou very much for this information!

---

