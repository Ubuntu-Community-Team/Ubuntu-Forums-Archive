---
title: "Sreen resolution too small"
date: 2010-02-06
forum: Hardware
---

### Post by gooliwoop on 2010-02-06
I've just installed ubuntu 9.10 on a Toshiba Portege P4010 laptop and can't increase the resolution higher than 800 X 600. This leaves a small viewing area with about 1" of unusable black border on the 12" screen. I've looked at some of the previous threads that describe similar problems but can't understand the jargon/language being used to describethe solution. Does anyone know a simple remedy that they can explain in plain Englist? Unfortunately, now that I've dumped MS Windows I am no longer able to interrogate my machine to find out what sort of on-board graphics card I have.

---

### Post by pi/roman on 2010-02-06
graphics hardware for portege 4010

    •     12.1” TFT Poly-silicon color LCD; internal display supports up to
          16M colors at 1024 x 768 (XGA)
    •     Trident CyberALADDiN-T graphics controller; 16MB external
          UMA video memory
    •     3D Graphics Accelerator, 4x AGP bus support; 2D Graphics
          Accelerator, BitBLT hardware, Hardware cursor, Direct Draw
          support
    •     External Color Support:
          800 x 600, 640 x 480; 60/75/85Hz Non-Interlaced @ 16M
          1024 x 768; 85Hz Non-Interlaced @ 64K
          1280 x 1024, 1024 x 768; 60/75Hz Non-Interlaced @ 16M
          1280 x 1024; 60/75/85Hz Non-Interlaced @ 64K
          1600 x 1200; 60Hz Non-Interlaced @ 64K

So your lcd should be able to support 1024x768, while plugging into an external monitor you could get up to 1600x1200.
Do you have an xorg.conf? ```
cat /etc/X11/xorg.conf
``` should list it if you do.

---

### Post by gooliwoop on 2010-02-06
It would seem that I havn't got xorg.conf because when I type Cat/ettc/x11/xorg.conf into Applications/Accessories/Terminal I get the response "No such file or directory"
P.S. what's with the beans

---

### Post by pi/roman on 2010-02-06
> **gooliwoop said:**
> what's with the beans
Not really sure myself but some have called them a miracle fruit.
Are you sure you typed the command exactly with the X in /X11/ being the only capital letter or just copy and paste it?
cat /etc/X11/xorg.conf

---

### Post by gooliwoop on 2010-02-07
I did copy and paste first time but have now tried using both small and capital X in X11 and still get the response "No such file or directory"

---

### Post by pi/roman on 2010-02-07
Here is how to create an xorg.conf called xorg.conf.new in your home folder: ```
sudo X :1 -configure
```Then copy it into your /etc/X11 folder and rename it to xorg.conf by typing: ```
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf
```now try : ```
cat /etc/X11/xorg.conf
```

---

### Post by gooliwoop on 2010-02-07
OK. I did all that and got this:

justin@justin-laptop:~$ sudo X :1 -configure
[sudo] password for justin: 

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux justin-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=eeb941c5-c83d-40c0-862e-cef388ab4fc4 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Feb  7 18:49:24 2010
List of video drivers:
    s3virge
    savage
    voodoo
    nv
    siliconmotion
    ati
    trident
    sis
    i740
    tseng
    openchrome
    s3
    vmware
    r128
    ztv
    ark
    apm
    intel
    v4l
    chips
    neomagic
    sisusb
    i128
    rendition
    mga
    mach64
    geode
    tdfx
    cirrus
    radeon
    fbdev
    vesa
(++) Using config file: "/home/justin/xorg.conf.new"
f000:36ab: 01 ILLEGAL EXTENDED X86 OPCODE!


Xorg detected your mouse at device /dev/input/mice.
Please check your config if the mouse is still not
operational, as by default Xorg tries to autodetect
the protocol.

Your xorg.conf file is /home/justin/xorg.conf.new

To test the server, run 'X -config /home/justin/xorg.conf.new'

 ddxSigGiveUp: Closing log
justin@justin-laptop:~$ sudo cp ~/xorg.conf.new /etc/X11/xorg.conf
justin@justin-laptop:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri"
    Load  "glx"
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "dri2"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "SetMClk"                # <freq>
        #Option     "MUXThreshold"           # <i>
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "NoMMIO"                 # [<bool>]
        #Option     "NoPciBurst"             # [<bool>]
        #Option     "MMIOonly"               # [<bool>]
        #Option     "CyberShadow"            # [<bool>]
        #Option     "CyberStretch"           # [<bool>]
        #Option     "XvHsync"                # <i>
        #Option     "XvVsync"                # <i>
        #Option     "XvBskew"                # <i>
        #Option     "XvRskew"                # <i>
        #Option     "FpDelay"                # <i>
        #Option     "Display1400"            # [<bool>]
        #Option     "Display"                # [<str>]
        #Option     "GammaBrightness"        # [<str>]
        #Option     "TVChipset"              # [<str>]
        #Option     "TVSignal"               # <i>
    Identifier  "Card0"
    Driver      "trident"
    VendorName  "Trident Microsystems"
    BoardName   "CyberBlade XPAi1"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

justin@justin-laptop:~$

---

### Post by pi/roman on 2010-02-07
I don't know if you tried rebooting yet but this may fix your problem now.  But if not then you could try placing virtual display options in your screen settings.
for instance use edit it by pressing alt/f2 and typing "sudo gedit /etc/X11/xorg.conf" and go to your screen section and add the following lines that are in red in each subsection:

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"[COLOR=Red]
virtual 1024 768[/COLOR]
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"[COLOR=Red]
virtual 1024 768[/COLOR]
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
[COLOR=Red]virtual 1024 768[/COLOR]
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"[COLOR=Red]
virtual 1024 768[/COLOR]
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"[COLOR=Red]
virtual 1024 768[/COLOR]
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"[COLOR=Red]
virtual 1024 768[/COLOR]
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Then reboot and if your screen is still not displaying properly then you can add modelines to the configuration.

---

### Post by efflandt on 2010-02-07
This may help you find and test modelines: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I am not familiar with how modelines plug into xorg.conf because 9.10 does not even have xorg.conf by default.  But I wrote a bash script using xrandr commands to enable a proper mode for VGA HDTV and turn off my laptop screen, with a launcher on my desktop to double-click run it when connected to that external display.

---

### Post by Carlos C on 2010-02-08
Try to add this to your xorg.conf under Section "Monitor":

HorizSync 28-96
VertRefresh 50-75

---

### Post by gooliwoop on 2010-02-21
That worked. many thanks.

---

