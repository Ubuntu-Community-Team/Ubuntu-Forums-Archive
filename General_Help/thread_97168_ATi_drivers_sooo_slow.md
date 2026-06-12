---
title: "ATi drivers sooo slow?"
date: 2005-11-30
forum: General Help
---

### Post by SirKillalot on 2005-11-30
Hi,
I am a prowd owner of an ATi Radeon 9700 Pro graphic adapter... Now my problem is that my system, an AMD 2400+ 768 MB DDR machine, runs fine with the fglrx drivers, they work, but it is so terribly slow! Modern games like UT2k4 or CounterStrike over cedega only run with a lack of fps. I heard from other users that they also think that the ATi drivers suck.

I mean, NVIDIA has it's own driver development team for linux drivers, ATi doesn't. Afaik ATi even has a team for MAC.. but not for linux! I am very angry about this, people pay lot of money to get a high-end card, and then the whole dream ends because of the drivers? That is just poor!

Now, share your experiences with ATI Cards on linux, compare it with other OSs,  and tell the whole world how you managed to get your system work faster ;).

Regards

---

### Post by dodongo on 2005-11-30
I have a Radeon 9000.   I won't lie -- I'm disappointed by the performance that I get from the cruddy drivers they throw our way.  I've sworn by ATI for the last five or six years; my next graphics card will be Nvidia.  That said, it's important to note that A) the system isn't unusable by any stretch of the imagination; it [i]runs[/] just fine; and B) this isn't the fault of any distro or party involved in the evolution of Linux.  It's ATI's choice not to develop better stuff for Xorg.  I, for one, will remember that.

---

### Post by charlesbrooking on 2005-12-02
[QUOTE=SirKillalot]Now, share your experiences with ATI Cards on linux, compare it with other OSs,  and tell the whole world how you managed to get your system work faster ;).[/QUOTE]

I have the Radeon Mobility 9700 in my laptop, and it runs UT2004 pretty well, although I've never bothered checking FPS and we might have different personal preferences.

You could try putting something like this in your /etc/X11/xorg.conf file (these are values I ripped from a file on a guy named Felix Marthaler's [blog]("http://blog.en.marfix.net/archives/10-my-new-laptop-dell-inspiron-9200-working-on-ubuntu-linux.html")).

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"    # vendor=1002, device=4e50
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
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x06419064"
    Option "GammaCorrectionII"          "0x06419064"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00008000"
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
    Option "UseFastTLS"                 "1"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    Screen 0
EndSection
```

To be honest, I have no idea what those options mean, but you could try them out and see how they go. :)

---

### Post by karolbe on 2005-12-03
> **dodongo]I have a Radeon 9000.   I won't lie -- I'm disappointed by the performance that I get from the cruddy drivers they throw our way.  I've sworn by ATI for the last five or six years said:**
> runs[/] just fine; and B) this isn't the fault of any distro or party involved in the evolution of Linux.  It's ATI's choice not to develop better stuff for Xorg.  I, for one, will remember that.

Firstly, make sure, that you have enabled 3D suport in the fglrx driver (use
fglrxinfo command) then complain :)

Karol

---

### Post by dodongo on 2005-12-03
[QUOTE=karolbe]Firstly, make sure, that you have enabled 3D suport in the fglrx driver (use
fglrxinfo command) then complain :)

Karol[/QUOTE]

Oh, I've had the FGLRX drivers enabled for some time, and they're just not good.  I'm complaining about the quality of the drivers from ATI.  I realize (though I think some people miss) the fact that it's no fault of anyone at Xorg or Ubuntu that the drivers aren't up to snuff.  That responsibility lies solely with ATI.

---

