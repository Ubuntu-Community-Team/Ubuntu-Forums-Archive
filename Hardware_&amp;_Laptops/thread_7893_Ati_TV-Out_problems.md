---
title: "Ati TV-Out problems"
date: 2004-12-12
forum: Hardware &amp; Laptops
---

### Post by FrankDaSilva on 2004-12-12
I dont speak English very well so i hope that you understand this ; )

I have problem with Ati TV-out.

-I have configured my card properly ( Followed Ubuntu Ati-HowTo)
-I use vlc-player.
-Tv-out works OK, i can watch my desktop from TV, EXCEPT:
**when i try to watch any video formats, in monitor they apperars OK, but in TV player screen is just black.**



Does anyone have any ideas where to start?

sorry about bad English..

FrankDaSilva

---

### Post by gfg on 2004-12-12
If you use clone mode try set your tv as the primary screen.

---

### Post by FrankDaSilva on 2004-12-12
[QUOTE=gfg]If you use clone mode try set your tv as the primary screen.[/QUOTE]
 Thanks but that didn't work.

---

### Post by SVen2000 on 2004-12-12
edit XF86Config-4

There must be an entry named Videooverlay or something ... turn it on!

This works only with ati binary driver, not with the "radeon" ubuntu comes with initially.

---

### Post by FrankDaSilva on 2004-12-13
I have installed "fglrx" drivers (followed ATI-friver HOW TO, apt-get install fglrx-driver etc..)
I think that is driver what you pointed.?

I looked XF86Config-4 and found out that those options were OK about video-overlay, i think.

Only what doesn't work is video output. Everything else appears fine in TV.

There is section from XF86Config-4 below if you understand more than me from that.


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
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000100" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "31.5       " 
    Option "VRefresh2"                  "20 - 60" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "no"     
    Option "TVStandard"                 "PAL-B"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x02008000"
[B]# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"[/B]
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
    Option "BlockSignalsOnLock"         "off"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    Option "KernelModuleParm"           "agplock=0" # AGP locked user pages: disabled
    BusID "PCI:1:0:0"    # vendor=1002, device=5960
    Screen 0
EndSection

---

### Post by SVen2000 on 2004-12-13
OpenGLOverlay, try to turn that on.
That should work.

Let me know if it does for you!

---

### Post by FrankDaSilva on 2004-12-14
YEAH! Its solved!

I disabled the Video Overlay and enabled OpenGl Overlay, and it's working.

Now i have vertical lines disturbing me while i play video, but i think that i can solve that by my own.

THANK YOU SVen2000!

---

