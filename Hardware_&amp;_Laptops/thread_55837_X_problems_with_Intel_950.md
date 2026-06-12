---
title: "X problems with Intel 950"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by leaded on 2005-08-10
I just got a Dell Dimension 5100C, and I'm beginning to think it's too new for Linux.  ](*,)  According to Dell, it has the new Intel 950 graphics controller. I haven't kept up with Linux lately since I've been using my Mac, but about 6 months ago I had used Fedora for a year, and was using an Nvidia card. I've heard stuff about Nvidia and ATI, regarding drivers, but never Intel.

I'd love to use Ubuntu for my desktop (this is a 2nd machine for me at work, next to my Mac mini) but I can't get X to start. It also won't work with the mobo ethernet so I can't copy over the log files to post or config, but I'll try and include relevant information by hand.

Just as a notice- my boss bought the same machine and wants to use FC4. In Fedora I was able to get X to start, but it won't properly display on our new widescreens. But, Fedora was using a Generic VESA driver I think. I'm not using a widescreen monitor, and if I could get a Generic driver to work for me and Ubuntu I would totally use it.

While typing up all of the information below, it looks like the 950 has no driver. Is there a generic driver or is there something I can download?

Ok, here's some stuff from /etc/X11/xorg.conf. Please keep in mind, this isn't everything; just what I thought was relevant.
```

Section "Module"
    Load  "bitmap"
    Load  "dbe"
    Load  "ddc"
    Load  "dri"
    Load  "extmod"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "record"
    Load  "type1"
    Load  "vbe"
End Section

Section "Device"
    Identifier  "Intel Corporation Intel Default Card"
    Driver      "i810"
    BusID       "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier  "DELL 1702FP"
    Option      "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Intel Default Card"
    Monitor       "DELL 1702FP"
    DefaultDepth  24
    SubSection    "Display"
                  Depth  1
                  Modes  "1280x1024" "1152x864" "1024x768" "800x600" etc...
    EndSubSection
    (... Repeats the SubSection "Display" identically for depths of 4, 8, 15, 16, and 24 ...)
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
    Screen      "Default Screen"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
EndSection

Section "DRI"
    Mode  0666
EndSection

```

The following is from /var/log/Xorg.0.log. Once again, this is just what I thought would be relevant for discussion.
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.warthogs.hdb.com)
...
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
...
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL 1702FP"
(**) |   |-->Device "Intel Corporation Intel Default Card"
(**) |-->Input Device "Generic Keyboard"
...
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Modules ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.7
        X.Org XInput driver: 0.4
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
...
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping /usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No symbols found
Skipping /usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No symbols found
Skipping /usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No symbols found
...
(II) I810: Driver for Intel Integreated Graphics Chipsets: i810, i810-dc100, 
       i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, 915GM
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) No devices detected.

Fatal server error:
no screens found

```

Thanks in advance!!

---

### Post by mo_x on 2005-08-10
You could also try using the vesa driver. Replace the line:
    Driver      "i810"
with:
    Driver      "vesa"
in your xorg.conf file.
i810 seems the right driver to me but I don't know if you chip is supported yet or if it does have some issues. You will have to do some more research on that.

---

### Post by leaded on 2005-08-12
[QUOTE=mo_x]You could also try using the vesa driver. Replace the line:
    Driver      "i810"
with:
    Driver      "vesa"
in your xorg.conf file.[/QUOTE]
 Thanks! That did it, for now. We might put in some Nvidia cards, which I've had luck with before. Off-topic, Dell says this computer has a PCIe 1x slot and a PCI 16x slot. The motherboard looks to me like a regular PCI slot and a really short (maybe 2.5 to 3 inches) slot. Which is which? Also, is the standard-length PCIe slot backwards compatible with regular PCI?

---

