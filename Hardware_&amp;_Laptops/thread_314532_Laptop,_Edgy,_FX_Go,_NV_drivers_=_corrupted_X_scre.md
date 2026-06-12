---
title: "Laptop, Edgy, FX Go, NV drivers = corrupted X screen"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by notasquirrel on 2006-12-07
Hello all,

First off I've been scouring the net for a week and haven't found info on this yet, including here, Google, the nvidia linux forums.  So, I think that means it's something I'm doing wrong, but I'm pretty sure I've installed the nvidia drivers correctly so I think it's xorg configuration.

Also please be loosely interpret the names of commands and config files I typed...  I double checked them all thoroughly from guides when actually using them but I'm in Windows right now without linux or the guides open.  :-k   

And, brace yourself for a big ol' chunk of post because I'm going for the "provide all the details" methodology...  I labeled sections at least!   8-[ 


**My Laptop Info:**  (Brand is Alienware Area-51m)
- P4, 3.4ghz proc.
- Geforce FX Go5700
- 1680x1050 resolution screen
- some other stuff I'll cut for not being related to graphics

**Symptoms:**

When GDM starts up, the laptop screen is corrupted as if it's mistakenly showing some uninitialized frame buffer with some leftover graphics data in it, kind of like if X initialized and wrote to one buffer but turned on a different one.

This happens after installing any nvidia drivers (from nvidia, not the 'nv' module).  I did run nvidia-xconfig, and tried some stuff in xorg.conf, keeping clean backups to go back to when things didn't work.

The corrupted display happens only on the laptop screen when there is nothing plugged in to the extra VGA plug.  The following situations produce different results:

---  **Starting GDM first and then plugging a monitor in the extra VGA plug:**
The laptop screen pops into graphics mode and is corrupted.
GDM plays the Ubuntu start-up sound.  X and GDM remain running and I believe I can even type username / password and log in.  Stopping X from a root console or SSH turns off the corrupted graphics, back to what you'd expect without X running.  The extra monitor stays blank, and no corrupted graphics ever appear on it. (no signal.)

---  **Plugging in a monitor, and THEN starting GDM:**
The blinking cursor on root console 7 turns to a plain black screen.  The Ubuntu startup sound plays normally.  The monitor I have plugged in now shows a perfectly normal Ubuntu login screen.  After logging in I try some screensavers, and they display very nice, very fast, I'd say perfectly.

I can then go to nvidia's driver config applet that got installed with the drivers, poke through it and do stuff.  It sees the flat panel I plugged in as what it is with the correct brand name and resolution.  It also sees a second display screen, but the resolution list for it is empty and shows up as a thin horizontal line I can tell would normally hold a list of resolutions.  If I try and enable this screen, it chooses 640x480 but that resolution still doesn't show in the list to choose from.

Nothing I do in the gnome nvidia drivers applet helps the laptop screen, even after saving a new xorg.conf, copying it into place, and restarting gdm.  At least one of the new xorg.conf files I got it to make had definitions for two display devices and two screens, but with no detected resolutions for the laptop screen.  Adding resolutions, checking them vs. the detected refresh rates, saving and restarting gdm did not help.


**Extra info that seems relevant:**

Full computer reboots do not help.

I am nearly clueless as far as how to REALLY configure xorg.conf, though I did get my resolutions set up right with the 'nv' driver.

I have not changed anything significant as far as the default ubuntu installation before trying nvidia drivers.

I *did* however install the ubuntu security and package updates that asked me to.

I used the Alternative Install Image this time, but the same thing happened with the Desktop install image last time.

I have not put any module options into "modules.conf" yet as the nvidia guide suggests.  I can't seem to figure out exactly how to accomplish this in Ubuntu's mothodology.  :confused: 

I have theoretically disabled the kernel's loading of the 'nv' module on boot, like the guides say to do, but for some reason it seems I can just switch the xorg.conf file back to using it and things work without me having to re-enable the module and reboot.  (This makes me suspect it's not disabling correctly?)

In the xorg log file, for a gdm startup without the extra monitor plugged in, I get some NVIDIA: lines that say it tried 1024x768 and found no such resolution, tried 800x600 and found no such resolution, and then tried 640x480.  I'm still parsing through those trying to figure out what they all are - going to finish posting this then reboot into ubuntu so I can post them.


**What works perfectly:**
- Windows XP w/ nvidia drivers, and all functions of them incl. openGL, directX
- Ubuntu 6.10 Edgy with open source 'nv' module and laptop screen
- Mouse, keyboard, synaptics touchpad, plug-in usb items 
- networking, internet, wireless even with WPA, sound
- strangely enough, nvidia drivers, but only when I'm using an external monitor not the laptop's LCD screen.



I hope I didn't scare everyone off four paragraphs in...  This is a weird one, and I've reached the end of my ability to attack it without help.  (So, Thanks if anyone knows what's up!)

I will be back after reboot with X logs and conf files...

---

### Post by TKBuisan on 2006-12-07
I have an Averatec Laptop and I have the same problem(s). I get around the issue by booting into recovery mode, typing exit and I then get a good Login Screen.
TKBuisan

---

### Post by notasquirrel on 2006-12-07
That was so fast it caught me before my reboot...

sounds like a good time to try it!

---

### Post by TKBuisan on 2006-12-07
Not a fix... just a workaround.
TKBuisan

---

### Post by notasquirrel on 2006-12-07
No dice...

I did these steps:

Booted to recovery mode
Restored my pre-nvidia-drivers xorg.conf
ran nvidia-xconfig --no-composite to nvidia-ize the xorg.conf
typed 'exit'


GDM started up and got the exact same corrupted screen as before.  I restored the old pre-nvidia xorg.conf and I'm in gnome now.  I notice that the openGL screensavers do not run at all anymore, while they used to at least run slowly.

Here's the xorg.conf that nvidia-xconfig made for me.  I stripped out the InputDevice sections to save some wear and tear on your scroll wheels:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV36 [GeForce FX Go5700]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV36 [GeForce FX Go5700]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1280x854" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1280x854" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1280x854" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1280x854" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x854" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x854" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```


Here are the lines and context of xorg.0.log involving nvidia.
DFP-0 is the device for the laptop flat panel.  Note the resolutions all being denied except for 640x480, and also I believe that 640x480 was never checked but would have been denied if it had been;  I think it passed because it "has to".  I think X is finding the configured resolutions and applying them to DFP-0 and the correct screen, but something is telling the nvidia drivers those resolutions won't work?

The alternative is that the nvidia driver is detecting those resolutions as capabilities and X is telling the nvidia driver they won't work because of a misconfig?
```

my@machine:~# cat /var/log/Xorg.0.log.old |grep -B 3 -A 3 -i nvidia

(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV36 [GeForce FX Go5700]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"

--

(II) Bus 6 prefetchable memory range:
        [0] -1  0       0x54000000 - 0x55ffffff (0x2000000) MX[B]
(--) PCI: (0:12:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 2, Mem @ 0xdf000000/24
(--) PCI:*(1:0:0) nVidia Corporation NV36 [GeForce FX Go5700] rev 161, Mem @ 0xdc000000/24, 0xc0000000/28, BIOS @ 0xddee0000/17
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]

--

(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9629
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1

--

(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9629
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"

--

        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9629  Wed Nov  1 19:31:54 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so

--

        [29] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [30] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce FX Go5700 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.36.20.33.14
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX Go5700 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 300.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): No valid modes for "1280x854"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(--) NVIDIA(0): DPI set to (50, 60); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:

--

        [30] -1 0       0x00000c00 - 0x00000c1f (0x20) IX[B]
        [31] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [32] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) NVIDIA(0): Setting mode "640x480"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM

--

(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };


```



Here is xorg detecting PCI devices.  I think the "unknown" is probably a Conexant video capture device the laptop has installed.  (it works in windows - no hardware problems.  None that aren't "the hardware sucks" anyway...)
```

(--) PCI: (0:12:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 2, Mem @ 0xdf000000/24
(--) PCI:*(1:0:0) nVidia Corporation NV36 [GeForce FX Go5700] rev 161, Mem @ 0xdc000000/24, 0xc0000000/28, BIOS @ 0xddee0000/17

```


The nvidia and GLX modules are both loading. GLX first then nvidia:
```

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9629
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX

#  ...  other modules loading in between #

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9629
	Module class: X.Org Video Driver

```


BTW I was being good and posting from the xorg.0.log.old, from the nvidia startup and not from the current session I'm in...

Is it worth posting the whole xorg.0.log?

Thanks again guys!  I'm trying to use ubuntu as a content creation platform, i.e. Maya, Blender, video editors and the like.  So, without acceleration, well that's it.  :(

---

### Post by notasquirrel on 2006-12-07
Oh yeah, should probably mention what kernel is installed:

:~# uname -r
2.6.17-10-generic

---

### Post by TKBuisan on 2006-12-07
I could not get the nvidia drivers to work. I use the nv drivers. 
TKBuisan

---

### Post by chris_n00b on 2006-12-08
> **TKBuisan said:**
> I could not get the nvidia drivers to work. I use the nv drivers. 
TKBuisan

Where do you get the 'nv' drivers from instead? I know you can get the nvidia ones from through automatix2...

---

### Post by notasquirrel on 2006-12-08
The 'nv' drivers are the open-source ones that Ubuntu includes with a default installation.  You can verify by looking at /etc/X11/xorg.conf:

```

Section "Device"
     Identifier     "Name of your Video Card, Probably"
     Driver         "nv"
     ...   ...
     ...   ...
EndSection

```


I could be wrong about this (pretty easily, I'm not exactly a guru) but I think the 'nv' drivers are a kernel module and are nearly always installed with the Ubuntu install CD unless they've been removed.  If you're using them, the Driver line in your display device declaration above will say "nv".  Otherwise it could say something like "VGA" or "Vesa".  You are using the nVidia supplied drivers if it says "nvidia" instead of any of those.

---

### Post by notasquirrel on 2006-12-20
The folks at the Nvidia Linux forum helped me through this and I now have a working system.  It doesn't seem to have been EDIDs related, or at least disabling EDIDs does not help.

[COLOR="Navy"][--> Here is the thread <--]("http://www.nvnews.net/vbulletin/showthread.php?p=1104113")[/COLOR] at the nvidia linux forums where it got solved.

After starting GDM with the line "startx -- -logverbose 6", we noticed the modes that would have worked in the mode pool were being disabled due to the vertical refresh for unknown reasons.  I had xorg.conf set to 60Hz max, and it was testing for 61.1Hz and not validating.  Changing the xorg.conf line to 62Hz didn't solve it, the modes still got invalidated.

At one point in the process I upgraded to driver 9631 which did not solve the problem by itself but may have contributed.  It might work to use the official release 9629 with the option I mention below in the correct section.

The solution was to add this line to the **Device section:**

**Option   "ModeValidation"  "NoVertRefreshCheck"**

I'd previously had that option in the Screen section which did not work, although the options DID show as having been parsed in Xorg.0.log.

With driver 9631 and that line above I have fast acceleration and working GDM on my laptop screen.

---

### Post by notasquirrel on 2007-01-02
Another person I talked to on the NVNews forum just verified that this fix also worked for him on his AlienWare Area-51m laptop.  Thought it would be nice to mention here for posterity.

His config was very similar to mine, that being Ubuntu Edgy 6.10, an AlienWare Area-51m laptop, and an nVidia FX-Go card.  He had the same symptoms I mentioned above, and adding the option to disable vertical refresh checks fixed it.

---

### Post by jswhite on 2007-03-12
Notasquirrel: You're my new hero. That Alienware Area51-M laptop you were talking about? Well, I have it. And for nearly two years now, I've been fighting with it trying to get the nVidia drivers to work properly. With MEPIS, I was usually able to fiddle around with xorg.conf so that it was usuable, but the freaky screen still showed up on shutdown and at certain resolutions when I was working.

Since switching to Ubuntu officially, I hadn't been able to get it to work AT ALL. No changes to xorg.conf made even the slightest dent. Then I found this thread, added that line, and restarted X. *POOF* Everything works.

It's about damned time. You rock.

---

