---
title: "Unable to start Xorg"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by James- on 2008-12-31
I have a Dell latitude E6500 with a Nvidia Quadro 160M inside
I decided to install the drivers for it

downloaded (180.18 ) from: 
[ftp://download.nvidia.com/XFree86/Linux-x86/180.18/NVIDIA-Linux-x86-180.18-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/180.18/NVIDIA-Linux-x86-180.18-pkg1.run)

got this error when I restarted gdm:
> 
(WW) No matching Device section for instance(BusID PCI:1:0:0) found
(EE) No devices detected



lspci:
> 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)

01:00.0 VGA compatible controller: nVidia Corporation Device 06eb (rev a1)

03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection


xorg.conf(without the inputs..to save room)
> 
Section "Device"
        Identifier      "nVidia Corporation Quadro 160M"

        # Enabling the nvidia drivers means that all acceleration processing is done internally
        # NVidia provide's its own GLX module
        # NVidia does not use the X server's DRI stack. 
        #       Instead, it uses a proprietary method to route call directly to the hardware and provide drect rendering
        # Though the only possible driver is nvidia, it is also possible to override NVidia's methods:
        #       by force-enabling AIGLX in "ServerLayout", loading dri, and enabling DRI in "Device"
        #       by enabling XGL (which is a bad idea anyway)
        Driver          "nvidia"
        # lspci | grep -i nv            <- To find device
        Busid           "PCI:1:00.0"

        # Adds support for 32-bit rendering on ARGB colorspace windows and pixmaps
        # ARGB = alpha, red, green, blue
        # AKA you should enable this on the new NVidia driver
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"                "True"

        # Experimental : enable hardware acceleration of the X render extension
        # Enabled by default in newer drivers however
        Option          "RenderAccel"           "True"

        # Enable RGB overlay. (Not available with X composite)
        # Also slow with virtual desktops larger than 2046x2047
        # Requires depth of 24 or higher
        # Requires an NVidia quadro
        Option          "Overlay"               "True"

        # Improves performance by using OS to notify X to update direct-rendered visuals instead of running through the hardware.
        # Enabled by default in newer drivers
        Option          "DamageEvents"          "True"

        # Disable clipping OpenGL rendering to the root window
        Option          "DisableGLXRootClipping"        "True"

        # An X server option to disable accel. writes into offscreen video memory
        # Might be needed if using AIGLX instead of proprietary NVidia interface
        # Probably ignored if using the NVidia method
        #Option         "XaaNoOffscreenPixmaps"

        # Might cause crashes in older NVidia drivers.
        # Forces the driver to allow GLX when composite on the X server is enabled.
        # Not necessary on modern X servers; might decrease stability
        #Option         "AllowGLXWithComposite"         "True"

        # An X server option to allow occluded window pixel data to be remembered
        # Caution in enabling. It might be faster to redraw the information than to fetch it
        # BackingStore is implemented in a very hackish but memory-efficient way. Therefore, it tends to be slow
        Option          "BackingStore"                  "True"

        # Use below in conjuction with v-sync (see nvidia-settings)
        # v-sync will however cap framerate to a max of 60 fps on most monitors

	Option		"UseDisplayDevice"		"DFP-0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        # Power saving mode
        Option          "DPMS"
        # at start X will automatically probe EDID information of the monitor.
        # This can be overridden, but not recommended.
        Horizsync       28-96
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation Quadro 160M"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen          "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
	Inputdevice	"Synaptics Touchpad"

EndSection

Section "Module"
        # To understand these comments, understand that there are three methods of running acceleration:
        #       XGL, AIGLX, NVidia

        # The GLX module provides the hardware OpenGL extensions to the X server
        # Through AIGLX, this loads the open source GLX
        # Through NVidia, this loads NVidia's GLX modules (closed source)
        Load            "glx"
        Load            "dbe"
        Load            "extmod"
        # The freetype module completely replaces the "type1" module
        Load            "freetype"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "int10"
        Load            "vbe"
        # DRI = Direct Rendering Infrastructure
        # DRI is an X server extensions that allows "3d" acceleration calls to bypass the X server.
        #       This leads the term "Direct Rendering" as the calls are routed directly to the hardware
        #       This also leads to dramatic speed improvements/increases
        # DRI is AIGLX's response to XGL. However, DRI provides the benefit that the entire screen is compositing as well.
        # Loading this module is harmless unless it is enabled in the "Device" section.
        # NVidia will not use this module as it's direct rendering calls are processed internally
        Load            "dri"
        # Load the mesa software acceleration libraries
        #Load           "GLcore"

EndSection

# Specific only to the DRI module.
Section "DRI"
        # Allows all users to access DRI
        Mode 0666
EndSection


---

### Post by lemming465 on 2009-01-01
There are two nvidia drivers, the legacy one for the older cards and the new one for the newer cards.  I think you downloaded the older one.  Try [this one]("http://us.download.nvidia.com/XFree86/Linux-x86/177.82/NVIDIA-Linux-x86-177.82-pkg1.run") instead and see if you get a better result.

---

