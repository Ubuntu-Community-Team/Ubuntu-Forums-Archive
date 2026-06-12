---
title: "resolution reset to 640x480"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by one_ro on 2007-01-18
Hi again,

I had a problem with video card detection, which I managed to solve installing the latest ATI drivers.
The problem now is related to the resolution, which gets reset to 640x480 after each reboot.
Also, I noticed the fonts are a little peculiar.

My laptop is HP nw8440, Intel Core 2 Duo 2GHz, ATI FireGL v5200.

Could anybody give me a hint, please?
Adrian

---

### Post by j19sch on 2007-01-18
Have you checked the resolutions in /etc/X11/xorg.conf?
Do you have a "vga=791" (or some other number) as boot option in the Ubuntu entry in /boot/grub/menu.lst?

Those are the two places that have something to say about resolution.

Joep

---

### Post by one_ro on 2007-01-18
Hi, thanks for the reply.
Well, I have the necessary resolutions in xorg.conf 
```

             SubSection "Display"
                         Depth     16
                         Modes    "1680x1050" "1024x768" "800x600" "640x480
             EndSubSection
             SubSection "Display"
                         Depth     24
                         Modes    "1680x1050" "1024x768" "800x600" "640x480"
             EndSubSection
```I can manually set the resolution to 1680x1050. I just set vga=791 in the file you mentioned. It looks like this ```
# defoptions=quiet splash vga=791
```It says there not to uncomment it. After reboot, the problem persists...

Any further hint would be most welcomed.
Adrian

---

### Post by one_ro on 2007-01-18
I checked /var/log/Xorg.0.log
and I found this error:

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

Does anybody knows anything about it?

---

### Post by marcantonio on 2007-01-25
I have the exact same laptop.  Were you able to get 1680x1050?  If so, how?

Marc

---

### Post by one_ro on 2007-01-26
Hello marcantonio,

Unfortunately not. As far as I understand it is not driver problem, as both following commands return proper results:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.6234 (8.32.5)
``````
$fgl_glxgears
```The [COLOR=Red]**fgl_glxgears**[/COLOR] command correctly displays the gears rotating in 3D, so this findings leave only a problem of setting xorg.conf right.

This is my xorg.conf, in case anyone could give me a hint I would be extremely grateful; for now, I have to manually set the resolution each time I start my machine... :(
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "aticonfig-Screen[0]" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

  # path to defoma fonts
    FontPath     "/usr/share/X11/fonts/misc"
    FontPath     "/usr/share/X11/fonts/cyrillic"
    FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/Type1"
    FontPath     "/usr/share/X11/fonts/100dpi"
    FontPath     "/usr/share/X11/fonts/75dpi"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "i2c"
    Load  "bitmap"
    Load  "ddc"
    Load  "dri"
    Load  "extmod"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "type1"
    Load  "vbe"
    Load  "dbe"
    Load  "v4l"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
    Option        "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ExplorerPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option        "SendCoreEvents" "true"
    Option        "Device" "/dev/psaux"
    Option        "Protocol" "auto-dev"
    Option        "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
    Identifier  "stylus"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"# Change to 
    Option        "Type" "stylus"
    Option        "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
    Identifier  "eraser"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"# Change to 
    Option        "Type" "eraser"
    Option        "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
    Identifier  "cursor"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"# Change to 
    Option        "Type" "cursor"
    Option        "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    VendorName   "Plug 'n' Play"
    ModelName    "Plug 'n' Play"
    Gamma        1
        #DisplaySize  508 318
    #HorizSync    31.5 - 90.0
    #VertRefresh  60.0 - 60.0
    ModeLine     "1680x1050@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
    VendorName  "ATI"
    BoardName   "ATI Technologies Inc, FileGL v5200"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]"
    Device     "aticonfig-Device[0]"
    Monitor    "aticonfig-Monitor[0]"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     4
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     8
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     15
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes    "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     24
        Modes    "1680x1050@60"
    EndSubSection
EndSection

Section "DRI"
    Mode         0666
EndSection

Section "Extensions"
    Option        "Composite" "Disable"
EndSection
```

---

### Post by matejkenda on 2007-01-29
Open source driver for this video card (X1600) doesn't work (yet), so you have to use the proprietary driver fglrx.

```

$lspci | grep Radeon
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]

```

Please read the instructions on the "Unofficial ATI Linux Driver Wiki" [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide).

I have successfully set up the display in Edgy and in Feisty. I don't have to change the resolution manually at each startup.

Section of my xorg.conf:

```

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "Centermode" "off"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection


```

---

### Post by one_ro on 2007-01-29
Hello matejkenda,

Thanks for the tips. I already followed the instructions in that web page and I thought everything went well; just for the sake of it did it once more and I think I now have a problem that is not solved:
```
$ sudo module-assistant prepare
Getting source for kernel version: 2.6.17-10-generic
[.........snip............]
The following packages have unmet dependencies:
  fglrx-kernel-2.6.17-10-generic: Depends: xorg-driver-fglrx (= 8.32.5-1) but 8.33.6-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```It seems that the **fglrx-kernel** file depends on a different version of **xorg-driver-fglrx**...

The last time I went through this I tried [COLOR=Red]**apt-get -f install**[/COLOR] but it seems that didn't work. 

Could you please give me a hint on this?
Cheers,
Adrian

---

### Post by matejkenda on 2007-01-29
Hmm, I didn't have problems like this.

> 
The following packages have unmet dependencies:
  fglrx-kernel-2.6.17-10-generic: Depends: xorg-driver-fglrx (= 8.32.5-1) but 8.33.6-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


xorg ATI driver must use appropriate version of its kernel component.

Is it possible that the drivers (kernel and xorg) are available in several apt repositories that you have configured which contain different versions of the driver?

Did you perform apt-get update before installing?

---

### Post by one_ro on 2007-01-29
> Is it possible that the drivers (kernel and xorg) are available in several apt repositories that you have configured which contain different versions of the driver?Well, I played with several repos one at a time (with the *restricted* word added at the end), and all of them issued the same error: unmet dependencies.

>  Did you perform apt-get update before installing?Yes, every single time. Could you please post your sources.list, maybe my repos are gone wild?
Thanks,
Adrian

---

### Post by matejkenda on 2007-01-29
> **one_ro said:**
> Could you please post your sources.list, maybe my repos are gone wild?

Please find my zipped sources.list attached.

Try to perform ```
apt-get clean
``` to remove local cache and then ```
apt-get update
``` before trying again. This might help.

Regards,

Matej

---

### Post by one_ro on 2007-01-29
Sigh... :(
Did what you said, unfortunately with the same result.
Why-oh-why do they not match the dependencies exactly on my computer?
Hm... Do you have the same kernel?

My [COLOR=DarkOrange]**uname -r**[/COLOR] gives:
2.6.17-10-generic

I wonder if I should start another thread asking specifically for this dependency problem...

Cheers,
Adrian

---

### Post by one_ro on 2007-01-30
Hey I think I got it!
This is a new laptop I use, having migrated everything in /home from my former one.

There is something, somewhere (probably in .kde) that messes with my resolution. I've created a test user and **no problem** occurs there...

Does anybody have any slight idea as to what exactly could that file be? I could erase the whole .kde and have it recreated at the next startup, but there are some setting there that I probably don't want to lose.

Cheers,
Adrian

---

