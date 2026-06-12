---
title: "Xlib:  extension &quot;XFree86-DRI&quot; missing on display &quot;:0.0&quot;."
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by mistermax on 2006-11-04
I've had to reinistall Edgy asfter a bad upgrade and am reconfiguring everything (again)

I have the Ubuntu hacks book and i followed the instructions for 3d Acceleration, but when I run GLX gears I get-

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

here is the output of lspci -v

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASRock Incorporation Unknown device 02f1
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: ASRock Incorporation Unknown device 02fa
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: ASRock Incorporation Unknown device 02fe
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: ASRock Incorporation Unknown device 02f8
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: ASRock Incorporation Unknown device 02f9
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASRock Incorporation Unknown device 02ff
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: ASRock Incorporation Unknown device 027f
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: ASRock Incorporation Unknown device 027e
        Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: feb00000-febfffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dff00000
        Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: ASRock Incorporation Unknown device 0270
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
        Subsystem: ASRock Incorporation Unknown device 0261
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
        Subsystem: ASRock Incorporation Unknown device 0264
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at 5000 [size=64]
        I/O ports at 6000 [size=64]
        Capabilities: <access denied>

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 026d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        Memory at feabe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation Unknown device 026e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        Memory at feabfc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation Unknown device 0265
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: ASRock Incorporation Unknown device 0266
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        I/O ports at d800 [size=8]
        I/O ports at d480 [size=4]
        I/O ports at d400 [size=8]
        I/O ports at d080 [size=4]
        I/O ports at d000 [size=16]
        Memory at feabd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: ASRock Incorporation Unknown device 0888
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        Memory at feab8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
        Subsystem: ASRock Incorporation Unknown device 0269
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at feabc000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at cc00 [size=8]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

02:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300] (prog-if 00 [VGA])
        Subsystem: C.P. Technology Co. Ltd Unknown device 2166
        Flags: bus master, fast devsel, latency 0, IRQ 233
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at febe0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at e800 [size=256]
        Expansion ROM at febc0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
        Subsystem: C.P. Technology Co. Ltd Unknown device 2167
        Flags: bus master, fast devsel, latency 0
        Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

Have I missed an abovious step?
I've downloaded the fglrx driver, changed my etc/X11/xorg.conf file.

---

### Post by Eversmann on 2006-11-04
It's a common problem with the damn ati linux drivers.

First of all, disable composition at xorg. Edgy has it enable by default but ati driver doesn't support it yet.

Add this at the end of xorg.conf file:

Section "Extensions"
        Option      "Composite" "0"
EndSection

----
Reinstall linux-restricted-modules for your kernel version and install fglrx-xorg-driver if it doesn't work.

--------

If not, follow more instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

Maybe installing latest oficial drivers can help on your problem.

---

### Post by heftigrat on 2006-11-17
**Eversmann**, Thank you, thank you, thank you!!!  Those three simple lines worked.  Last time I go with ATI though.  Tired of feeling like this:  ](*,)

---

### Post by amarp on 2006-12-21
Scanning through /var/log/Xorg.o.log I've found this line:

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)

it seems that the build of fglrx driver is bad. All we can do is to wait for a new driver.

P.S. dri works perfectly in gnome session, without xgl.

---

### Post by [pl]ice on 2007-01-10
thnx for the quick fix :) works

---

### Post by nolongerlivecd on 2007-01-27
Hi, I've got the same problem.

Last week, I had problems installing the drivers. After some help on the IRC channel, I managed to fix it and get Beryl up and running. Today, after installing Wine and Counter-strke via Wine, I am getting this error again.

My Composite is disabled within Xorg.conf. Can anyone help?

---

### Post by Banekartr on 2007-02-11
Huge thanks here also.  Was having the same problem with my ATI card.  Followed the steps and we are good to go.
Thanks!

---

### Post by DrMega on 2007-02-25
This worked for me. When its time to upgrade my graphics card, it most certainly won't be another ATI card. Nowt but trouble :mad:

---

### Post by DraxNS on 2007-02-26
ahem... check your xorg.conf for
```

load "dri"

```

in **Section "Module"**

---

### Post by hollerith on 2007-03-06
Yes yes dri in the xorg.conf

I was running an app fine and now it complains about this... (it does display a startup message)

looks like a config issue

booo!

---

### Post by zeifertstc on 2007-03-07
> Section "Module"
               Load     "i2c"
               Load     "bitmap"
               Load     "ddc"
               Load     "dri"
               Load     "extmod"
               Load     "freetype"
               Load     "glx"
               Load     "int10"
               Load     "type1"
               Load     "vbe"
EndSection

I'm running Ubuntu Edgy on my laptop which is equipped with the ATi Xpress 200M video adapter.

The above is a copy of that particular portion of my xorg.conf file. I've included the three lines from the beginning post in my xorg but I still get that same error. I have been trying "fixes" from all over the net but to no avail. If anybody has an answer to this, I'd really appreciate it. I had things working in the dapper version of Kubuntu but I'm not liking this little error on Ubuntu Edgy.

---

### Post by dogatemycomputer on 2007-05-14
I had this problem with Kubuntu which took me some time to figure out. It turned out to be something really dumb.

"Xlib: extension "XFree86-DRI" missing on display ":0.0"."

You see.. Ubuntu and Kubuntu use a Restricted-Driver manager to load/unload non-FOSS drivers. Even if they are installed and specified in the xorg.conf does not mean they'll load properly. If you use GNome as your Windows Manager then you can load the Restricted Driver's Manager from the System or Preference's menu (I can't remember which).

Ironically.. If you use Kubuntu then this particular menu item is missing. In order to load the Restricted Driver Manager in Kubuntu then..

sudo /usr/bin/restricted-manager

If you check the box and reboot then it should change this message:

"Xlib: extension "XFree86-DRI" missing on display ":0.0"."

To this one:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 PRO
OpenGL version string: 2.0.6334 (8.34.8)

If you are running glxgears and getting 400-600 frames per second using either Ubuntu or Kubuntu or your video playback seems a bit slow then this may also solve your problem. This also corrected my problem getting mplayer to play multiple videos in multiple windows on multiple monitors simultaneously without a loss in quality.

Best Regards,
Dave
[email]dogatemycomputer@gmail.com[/email]

---

### Post by mpp on 2007-05-30
Nope, that does not work for me :(

I am using the ati proprietary drivers, but DRI is still not working.

```

$ fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

I am using Xinerama for my second monitor, perhaps this is causing the problem??

A snippet from my xorg:
```

Section "Module"
    Load        "i2c"
    Load        "bitmap"
    Load        "ddc"
    Load        "dri"
    Load        "extmod"
    Load        "freetype"
    Load        "glx"
    Load        "int10"
    Load        "vbe"
EndSection

```
```

Section "ServerLayout"
    Option      "Xinerama"
    Identifier  "flgrx - mpp configured"
    Screen      "Screen 0" LeftOf "Screen 1"
    Screen      "Screen 1"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
EndSection

Section "ServerFlags"
    Option  "Xinerama"
EndSection

```

```

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
    Option      "Composite" "0"
EndSection

```

Some output from the logs shows:
```

$ grep \(EE\) /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) AIGLX: Screen 0 is not DRI capable
(EE) AIGLX: Screen 1 is not DRI capable

```

I also have a further problem, that my mouse cursor does not work properly on my second screen.  It will not change when on the second screen, and will stay with whatever cursor it was when moved away from the first screen (ie, if it was a pointer, it stays a pointer and won't change to a text-selector when hovering over text, for example).

Any ideas much appreciated :-)

have fun()
mike

---

### Post by Zargoon on 2007-06-10
Ugh.  I have the same problem and NOTHING SEEMS TO WORK....... I tried that command and the ati driver is enabled but it says that it is not in use.

---

### Post by Jukka-Pekka on 2007-07-26
Stuck here as well :( I have tried most of the suggestions from around the web to correct this, so far, no luck :(

I'm running ubuntu feisty 64-bit on a HP nc8430 laptop with ATI X1600 mobility (1680x1024 LCD). This combination seems quite difficult to configure properly to have 3D acceleration, be able to use dual screens (extended and clone modes), use beryl for eye-candy etc... It also has the broadcom 4311 WLAN to make things even more difficult =)

One strange thing is, that after i have installed the proprietary ATI drivers (from ATI website), followed installation instructions, etc... My computer at first had the "restricted driver" -option ticked...But after the reboot, it only says that "restricted drivers are not needed for this computer" as if I were running the open drivers?!?

fglrxinfo still shows:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

glxinfo: no direct rendering 

lspci gives:01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]

Any further help in solving the issue in this thread would be greatly appreciated!
Jukka

---

### Post by Offoffoff on 2007-07-28
I have the same problem. I got new refurbished notebook Compaq nc4000 with ATI Technologies Inc Radeon IGP 330M/340M/350M. I cannot get direct rendering... But I take my HDD from old notebook and maybe old video card driver do not really fit to new environment. How to fix it?

---

### Post by crhylove on 2007-07-29
Yeah, I'm trying to install ANY kind of 3d wm for a buddy of mine and have run into this problem over and over.  I'm sad inside.

---

### Post by RembrandtQEinstein on 2007-07-29
I have a new Ubuntu install (3 weeks old) and recently installed OpenArena and AlienArena. They both ran OK the first time but then stopped working. Sometimes I would get the XFree98-DRI error but other times I got a DGA error. Sorry I can't remember the exact error but there are other posts about it in the Ubuntu forums. I tried several different things but could not get the above games to work again. glxinfo said that direct rendering was off. I have an ATI card by the way. I finally came across this thread: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Enable_.22restricted.22_Repository]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Enable_.22restricted.22_Repository")

It may have been linked to in this thread even.

Now everything seems to work! :)

---

### Post by dark_harmonics on 2007-08-17
This code from the ATI wiki page helped me. I think this error means that your graphics acceleration isnt properly applied to your display. This command resolved the issue for me:
```

sudo aticonfig --overlay-type=Xv
```

I already had installed the latest driver (manual install through envy) but it didn't properly set the xorg.conf. 

This changed it so that when i type the diagnostic command fglrxinfo it responds with:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6747 (8.40.4)
```

Before it was responding with a Mesa Driver ( I think its the default) and the error. 
Hope this helps somebody!

-Josh

---

### Post by minnow157 on 2007-08-23
hi try this it worked for me

#! /bin/bash
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl &
gtk-window-decorator --replace &
xmodmap - and \ “keycode 22 = BackSpace Delete \”

i couldnt find how to do this anywhere until i translated a spanish page

---

### Post by Weird Al on 2008-01-03
> **mpp said:**
> I am using Xinerama for my second monitor, perhaps this is causing the problem??

Bingo. Browsing /var/log/Xorg.0.log yields this wonderfully obtuse line:

```
(II) fglrx(0): Xinerama extension enabled, disabling direct rendering.
```

If this weren't my office computer I'd get an nvidia, which I know works. I guess there's nothing much to do but to wait for the ATI drivers to be opened up...

---

### Post by soccerdog8 on 2008-03-24
I have a similar problem, probably the same as you guys. Heres my setup:

Dell Inspiron E1505 
ATI Mobility Radeon X1400
Ubuntu 7.10 - Gutsy

The command "fglrxinfo" gives me:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

```
Which i believe is what it should be.

But the command "glxinfo | grep rendering" gives me:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```
Meaning my 3D acceleration's not working.

Relevant parts of my /etc/X11/xorg.conf:

hmm. it seems to have gotten renamed "xorg.conf.fglrx-0"  Any idea why? Anyway, here are the important parts of it:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	BusID		"PCI:1:0:0"
		###This is to try and fix the sleep mode problemx
	Option		"VBERestore"		"yes"
EndSection
```
```
### trying to get 3D acceleration to work
Section	"Extensions"
	Option		"Composite"	"Disable"
EndSection

Section "ServerFlags"
	Option		"AIGLX"		"off"
EndSection

```

Also, i heard somebody talking about what was in their "Module" section of their xorg.conf, but i don't even have one of those sections. Is this a problem?

I thought i had all my graphics problems worked out since the driver is working and compiz works so well, but when i tried to startup America's Army i got this error. Crap.

---

### Post by Langrood on 2008-05-18
thank you Eversmann. Those few lines worked for me.

---

