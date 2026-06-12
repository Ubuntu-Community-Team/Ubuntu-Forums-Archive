---
title: "xorg-driver-fglrx for ATI Radeon"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by pstov on 2005-04-28
Hi,

in Hoary 5.04, I installed the fglrx driver for ATI Radeon 9700 Pro
along the lines described in [http://ubuntulinux.org/wiki/BinaryDriverHowto](http://ubuntulinux.org/wiki/BinaryDriverHowto).
After rebooting and logging in to an X session from gdm everything was fine.
The problem started after leaving the X session, instead of getting a gdm
welcome screen I got frozen X windows. After rebooting the computer I tried
to avoid gdm using the startx command instead. The problem was similar -
for the first time everything was fine. I was also able to leave the
X session. But when relaunching startx the X windows hung again.

Any ideas are appreciated.

Pavel Stovicek

---

### Post by alastair on 2005-04-28
Unfortunately, binary drivers are sometimes trouble - especially ATI's. Your best bet would be to post some logs e.g. anything relevant from :

/var/log/syslog
/var/log/Xorg.0.log

The config file would also be useful : /etc/X11/xorg.conf

Perhaps some indication of the problem.

---

### Post by pstov on 2005-05-02
[QUOTE=alastair]Unfortunately, binary drivers are sometimes trouble - especially ATI's. Your best bet would be to post some logs e.g. anything relevant from :

/var/log/syslog
/var/log/Xorg.0.log

The config file would also be useful : /etc/X11/xorg.conf

Perhaps some indication of the problem.[/QUOTE]

Here are some excerpts from the log and config files. I am not able to deduce
much of them, hopefully someone else.

/var/log/syslog:

May  2 09:01:55 localhost kernel: allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.
May  2 09:01:55 localhost kernel: Fire GL built-in AGP-support
May  2 09:01:55 localhost kernel: Based on agpgart interface v0.99 (c) Jeff Hartmann
May  2 09:01:55 localhost kernel: agpgart: Maximum main memory to use for agp memory: 816M
May  2 09:01:55 localhost kernel: agpgart: Detected an Intel 845G Chipset, no integrated grapics found.
May  2 09:01:55 localhost kernel: agpgart: Detected Intel i845 G/GL/GV/GE/PE chipset
May  2 09:01:55 localhost kernel: agpgart: AGP aperture is 64M @ 0xf8000000
May  2 09:01:55 localhost kernel: Power management callback for AGP chipset installed
May  2 09:01:55 localhost kernel: [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
May  2 09:01:55 localhost kernel: AGP: Found 2 AGPv2 devices
May  2 09:01:55 localhost kernel: AGP: Doing enable for AGPv2
May  2 09:01:55 localhost kernel: [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
May  2 09:01:55 localhost kernel: [fglrx] free  AGP = 54800384
May  2 09:01:55 localhost kernel: [fglrx] max   AGP = 54800384
May  2 09:01:55 localhost kernel: [fglrx] free  LFB = 116387840
May  2 09:01:55 localhost kernel: [fglrx] max   LFB = 116387840
May  2 09:01:55 localhost kernel: [fglrx] free  Inv = 0
May  2 09:01:55 localhost kernel: [fglrx] max   Inv = 0
May  2 09:01:55 localhost kernel: [fglrx] total Inv = 0
May  2 09:01:55 localhost kernel: [fglrx] total TIM = 0
May  2 09:01:55 localhost kernel: [fglrx] total FB  = 0
May  2 09:01:55 localhost kernel: [fglrx] total AGP = 16384

/etc/X11/xorg.conf:

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
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
        Driver          "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver
has its own code for mtrr
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
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
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
    BusID "PCI:1:0:0"    # vendor=1002, device=4e44
    Screen 0
EndSection

/var/log/Xorg.0.log:

(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8dff000
(II) fglrx(0): [drm] mapped SAREA 0xf8dff000 to 0xb7dae000
(II) fglrx(0): [drm] framebuffer handle = 0xf0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.10-5-686
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xdf000000
(II) fglrx(0): [agp] Mode=0x1f000217 bridge: 0x8086/0x2560
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000314
(II) fglrx(0): [agp] AGP protocoll is enabled for grafics board. (cmd=0x1f000314)
(II) fglrx(0): [agp] grafics chipset has AGP v2.0
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xf9001000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x00701000
(II) fglrx(0): ----------------------------------
(II) fglrx(0): | panel native mode is 1280x1024 |
(II) fglrx(0): ----------------------------------
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer -
assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 402
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled

---

### Post by alastair on 2005-05-02
Nothing obviously wrong - except this :

allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.

But even here, it might not be the problem. See :

[http://ubuntuforums.org/showthread.php?t=29130&highlight=vmalloc](http://ubuntuforums.org/showthread.php?t=29130&highlight=vmalloc)

Perhaps try the "ati" driver?

---

### Post by pstov on 2005-05-05
[QUOTE=alastair]Nothing obviously wrong - except this :

allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.

But even here, it might not be the problem. See :

[http://ubuntuforums.org/showthread.php?t=29130&highlight=vmalloc](http://ubuntuforums.org/showthread.php?t=29130&highlight=vmalloc)

Perhaps try the "ati" driver?[/QUOTE]

I tried to do some experiments with the settings but I didn't discover much.
I was using the "ati" driver prior to fglrx and I never experienced a problem.
I checked it once more and there was no vmalloc message for it. Going back
to fglrx, the vmalloc message can be removed with the option vmalloc=256m
when booting from grub but the problem with hanging X windows persists.
In fact, the situation for me is not critical at all. Even if I wish to use fglrx I have
to avoid gdm and I must reboot the computer after leaving an X session.
Thanks a lot for the hints anyway.

---

