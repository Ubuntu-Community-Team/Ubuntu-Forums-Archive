---
title: "Confused by graphic tablet drivers."
date: 2010-12-31
forum: Hardware
---

### Post by HandyGandy on 2010-12-31
Recently I got a Genius MousePen 8x6.

So I grabbed the latest WizardPen driver, compiled and install.

As far as I tested it, it was OK with Gnome, but I use KDE mostly and it doesn't seem to work with KDE. 
[COLOR="Blue"]The LED on the top of pad signalling input blinks on and off under KDE.[/COLOR]

When I bought the pad I had to ask a saleperson where they were. He told me that he uses the same pad with debian with no problems. So I presume there are drivers that are more or less generic to linux ( since they work with debian), but the only place I see WizardPen is in Launchpad so I have to wonder if that was the driver that the person was using ( didn't think to ask --sigh).

Does this tablet also work with the wacom drivers?

What other drivers are there for tablets in linux?

Finally ( most important ) is there a way to get the tablet working with Ubuntu using KDE?

PS: My system is a Karmic that has been upgraded to Lucid that has been upgraded to Maverick. I installed kde onto a basic ubuntu installation ( since I wanted to play with both GNome and KDE ).

---

### Post by SnickerSnack on 2010-12-31
This may help: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

Also, there are a few tutorials here:

[http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)
[http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

One or both of those may be helpful.  They're long, but comprehensive.

---

### Post by Favux on 2010-12-31
Hi HandyGandy,

Welcome to Ubuntu forums!

First we have to figure out what tablet you have.  I think the Genius MousePen 8x6 is a WizardPen but Genius rebrands a lot so it might be a Waltop or something else.  In a terminal enter:
```
xinput --list
```
and post the output and also:
```
lsusb
```
and post the line about your tablet.

---

### Post by HandyGandy on 2010-12-31
> **Favux said:**
> Hi HandyGandy,

Welcome to Ubuntu forums!


Thank You.
> 
First we have to figure out what tablet you have.  I think the Genius MousePen 8x6 is a WizardPen but Genius rebrands a lot so it might be a Waltop or something else.  


 xinput --list
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Comfort Curve Keyboard 2000     id=9    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse               id=10   [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                   id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Microsoft Comfort Curve Keyboard 2000     id=8    [slave  keyboard (3)]
```

lsusb
Bus 002 Device 008: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet

PS: I modified my original post to make it slightly more readable, since the original was written late at night. I did add one thing--the LED which is only supposed to come on when the tablet has input constantly flashes under KDE.

PPS: I can't believe that I am the only person to use a WizardPen tablet with KDE. One Possibilty is that my KDE is in bad shape. When upgrading I was using the backports, which caused me problems because the new kde was actually a slightly older version then the backports and refused to "upgrade".

---

### Post by Favux on 2010-12-31
Alright the UC-LOGIC Tablet WP8060U tablet does use the WizardPen driver.

First did you install the WizardPen driver from DoctorMO's PPA?  That's where you should get it:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick](https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick)

Notice I used the Filter to pick the Maverick driver.

---

### Post by HandyGandy on 2010-12-31
> **Favux said:**
> Alright the UC-LOGIC Tablet WP8060U tablet does use the WizardPen driver.

First did you install the WizardPen driver from DoctorMO's PPA?  That's where you should get it:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick](https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick)

Actual I used bzr to compile source and install ala
[https://help.ubuntu.com/community/TabletSetupWizardpen]("https://help.ubuntu.com/community/TabletSetupWizardpen")

> 
Notice I used the Filter to pick the Maverick driver.  Did you do the same with the fjbtndrv?

I'm uninstalling and trying your package.

Until a few minutes ago, I did not know about fjbtndrv. Does it work for a WP8060U ( aka MousePen )?

---

### Post by Favux on 2010-12-31
I'm sorry, I confused myself.  Ignore the part about fjbtndrv.  That doesn't apply to your UC-LOGIC tablet.

---

### Post by HandyGandy on 2010-12-31
Alright I removed the compiled driver and used DoctorMO's PPA.
I basically get the same result. Works with Gnome but not KDE.


I added some tests. First I am not sure the pressure sensitivity works under Gnome, I suspect I could get it to work with some tweaks, so I am not worried about this yet, My first priority is to get it to work under KDE.

I tried it under LXDE and XFCE. It works the same as Gnome.

When I log into a KDE session the tablet stops working and the input led flashes. This is the way it is even when logging out and logging into a Gnome session. It stays this way until I disconnect and reconnect the tablet then it goes bask to working fine under Gnome.

---

### Post by Favux on 2010-12-31
Sorry, my ISP got knocked out by a storm.

Let's look at the output of:
```
xinput --list
```
in a terminal with gnome and KDE.

We also need to look at your 70-wizardpen.conf at /usr/share/X11/xorg.conf.d/.  You should have pressure in Gimp, for example, if it is working on the wizardpen driver.

---

### Post by HandyGandy on 2010-12-31
Very loud forehead-palm.

First to answer the question about xinput --list.

In both cases it produces the same list that it did the first time I posted it.

Now on to the funny part, I noticed that as I log in the input led doesn't flash. Then after a while the led starts flashing.

I don't know how much you know about the kde boot sequence, but it shows a flash screen with icons being painted in as various subsystems of kde start up. It went through this whole startup with no falshing LED. Finally rhythmbox started and the input led started flashing. So I shutdown rhythmbox, unplugged and replugged the tablet and now it sort of works.

I still don't have pressure sensitivity, but I never finished the install sequence. In particular calibrarion. I'm going to take a break now and get to that soon.

I guess I will also have to play around with rhythmbox and various wm and other mp3 playing programs, get a clue of what the problem is.

One other strange thing though, the led does not start flashing until the pen is near the tablet, so I guess whatever interference with rhythmbox happens, it happens when some signal is sent from the tablet.

---

### Post by Favux on 2010-12-31
That is strange.

Alright, your stylus is showing up in xinput.  But that doesn't tell us what driver it is on.  To tell you can either post your Xorg.0.log in /var/log or the results of this command:
```
xinput list-props "UC-LOGIC Tablet WP8060U"
```

---

### Post by HandyGandy on 2011-01-02
> **Favux said:**
> That is strange.

I googled a bit, and discovered that it seems to be a rhythmbox plugin laberled "Portable players--MTP". When you disable it, the problem goes away, so it's not so strange. Still it is a little bit.

> 
Alright, your stylus is showing up in xinput.  But that doesn't tell us what driver it is on.  To tell you can either post your Xorg.0.log in /var/log or the results of this command:
```
xinput list-props "UC-LOGIC Tablet WP8060U"
```

Output from xinput list-props:
```


Device 'UC-LOGIC Tablet WP8060U':
        Device Enabled (136):   1
        Coordinate Transformation Matrix (138): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (255):     0
        Device Accel Constant Deceleration (256):       1.000000
        Device Accel Adaptive Deceleration (257):       1.000000
        Device Accel Velocity Scaling (258):    10.000000

```

My Device 70-wizardpen.conf 
```


Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection

```

---

### Post by Favux on 2011-01-02
Nice detective work.

The list-props output is a little surprising, it doesn't tell us the driver.  I guess we have to look at Xorg.0.log.

You could try changing your 70-wizardpen.conf to the one at this link:  [http://ubuntuforums.org/showpost.php?p=10292977&postcount=13](http://ubuntuforums.org/showpost.php?p=10292977&postcount=13)

Since you are in Maverick use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```
to edit the file.

---

### Post by HandyGandy on 2011-01-02
The new 70-wizardpen.conf doesn't change anything.

---

### Post by Favux on 2011-01-02
OK, with the same assumption that you installed DoctorMo's PPA corectly try the wizardpen.conf in this post:  [http://ubuntuforums.org/showpost.php?p=10294964&postcount=28](http://ubuntuforums.org/showpost.php?p=10294964&postcount=28)
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
Still would be good to see your Xorg.0.log.

---

### Post by HandyGandy on 2011-01-03
The changes made no diference.

I'm a bit confused here. What is this supposed to accomplish? I was pretty much certain that the driver was wizardpen. At this point the pen works fairly well except that there is no presure sensitivity.

Just checking to make sure we are on the same page here.

PS:
Next post will be my Xorg.0.log

---

### Post by HandyGandy on 2011-01-03
[   582.875] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   582.875] X Protocol Version 11, Revision 0
[   582.875] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[   582.875] Current Operating System: Linux ****** 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[   582.875] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-24-generic root=UUID=c89095b5-661e-4d9b-a0c1-b1608f0434b0 ro quiet splash
[   582.875] Build Date: 16 September 2010  06:18:41PM
[   582.875] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   582.875] Current version of pixman: 0.18.4
[   582.875] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   582.875] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   582.876] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan  2 21:29:49 2011
[   582.876] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   582.877] (==) No Layout section.  Using the first Screen section.
[   582.877] (==) No screen section available. Using defaults.
[   582.877] (**) |-->Screen "Default Screen Section" (0)
[   582.877] (**) |   |-->Monitor "<default monitor>"
[   582.877] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   582.877] (==) Automatically adding devices
[   582.878] (==) Automatically enabling devices
[   582.878] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   582.878] 	Entry deleted from font path.
[   582.878] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   582.878] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   582.878] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   582.878] (II) Loader magic: 0x7d0200
[   582.878] (II) Module ABI versions:
[   582.878] 	X.Org ANSI C Emulation: 0.4
[   582.878] 	X.Org Video Driver: 8.0
[   582.878] 	X.Org XInput driver : 11.0
[   582.878] 	X.Org Server Extension : 4.0
[   582.880] (--) PCI:*(0:1:5:0) 1002:791e:1043:826d rev 0, Mem @ 0xf0000000/134217728, 0xfdbf0000/65536, 0xfda00000/1048576, I/O @ 0x0000de00/256
[   582.880] (II) Open ACPI successful (/var/run/acpid.socket)
[   582.880] (II) LoadModule: "extmod"
[   582.881] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   582.882] (II) Module extmod: vendor="X.Org Foundation"
[   582.882] 	compiled for 1.9.0, module version = 1.0.0
[   582.882] 	Module class: X.Org Server Extension
[   582.882] 	ABI class: X.Org Server Extension, version 4.0
[   582.882] (II) Loading extension MIT-SCREEN-SAVER
[   582.882] (II) Loading extension XFree86-VidModeExtension
[   582.882] (II) Loading extension XFree86-DGA
[   582.882] (II) Loading extension DPMS
[   582.882] (II) Loading extension XVideo
[   582.882] (II) Loading extension XVideo-MotionCompensation
[   582.882] (II) Loading extension X-Resource
[   582.882] (II) LoadModule: "dbe"
[   582.882] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   582.883] (II) Module dbe: vendor="X.Org Foundation"
[   582.883] 	compiled for 1.9.0, module version = 1.0.0
[   582.883] 	Module class: X.Org Server Extension
[   582.883] 	ABI class: X.Org Server Extension, version 4.0
[   582.883] (II) Loading extension DOUBLE-BUFFER
[   582.883] (II) LoadModule: "glx"
[   582.883] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   582.884] (II) Module glx: vendor="X.Org Foundation"
[   582.884] 	compiled for 1.9.0, module version = 1.0.0
[   582.884] 	ABI class: X.Org Server Extension, version 4.0
[   582.884] (==) AIGLX enabled
[   582.884] (II) Loading extension GLX
[   582.884] (II) LoadModule: "record"
[   582.885] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   582.885] (II) Module record: vendor="X.Org Foundation"
[   582.885] 	compiled for 1.9.0, module version = 1.13.0
[   582.885] 	Module class: X.Org Server Extension
[   582.885] 	ABI class: X.Org Server Extension, version 4.0
[   582.885] (II) Loading extension RECORD
[   582.885] (II) LoadModule: "dri"
[   582.886] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   582.886] (II) Module dri: vendor="X.Org Foundation"
[   582.886] 	compiled for 1.9.0, module version = 1.0.0
[   582.886] 	ABI class: X.Org Server Extension, version 4.0
[   582.886] (II) Loading extension XFree86-DRI
[   582.886] (II) LoadModule: "dri2"
[   582.887] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   582.887] (II) Module dri2: vendor="X.Org Foundation"
[   582.887] 	compiled for 1.9.0, module version = 1.2.0
[   582.887] 	ABI class: X.Org Server Extension, version 4.0
[   582.887] (II) Loading extension DRI2
[   582.887] (==) Matched ati as autoconfigured driver 0
[   582.887] (==) Matched vesa as autoconfigured driver 1
[   582.887] (==) Matched fbdev as autoconfigured driver 2
[   582.887] (==) Assigned the driver to the xf86ConfigLayout
[   582.887] (II) LoadModule: "ati"
[   582.888] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   582.888] (II) Module ati: vendor="X.Org Foundation"
[   582.888] 	compiled for 1.9.0, module version = 6.13.1
[   582.888] 	Module class: X.Org Video Driver
[   582.888] 	ABI class: X.Org Video Driver, version 8.0
[   582.888] (II) LoadModule: "radeon"
[   582.889] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   582.889] (II) Module radeon: vendor="X.Org Foundation"
[   582.889] 	compiled for 1.9.0, module version = 6.13.1
[   582.889] 	Module class: X.Org Video Driver
[   582.889] 	ABI class: X.Org Video Driver, version 8.0
[   582.890] (II) LoadModule: "vesa"
[   582.890] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   582.891] (II) Module vesa: vendor="X.Org Foundation"
[   582.891] 	compiled for 1.8.99.905, module version = 2.3.0
[   582.891] 	Module class: X.Org Video Driver
[   582.891] 	ABI class: X.Org Video Driver, version 8.0
[   582.891] (II) LoadModule: "fbdev"
[   582.891] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   582.891] (II) Module fbdev: vendor="X.Org Foundation"
[   582.891] 	compiled for 1.8.99.905, module version = 0.4.2
[   582.891] 	ABI class: X.Org Video Driver, version 8.0
[   582.891] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
[   582.907] (II) VESA: driver for VESA chipsets: vesa
[   582.907] (II) FBDEV: driver for framebuffer: fbdev
[   582.907] (--) using VT number 8

[   582.921] (II) [KMS] Kernel modesetting enabled.
[   582.921] (WW) Falling back to old probe method for vesa
[   582.921] (WW) Falling back to old probe method for fbdev
[   582.921] (II) Loading sub module "fbdevhw"
[   582.921] (II) LoadModule: "fbdevhw"
[   582.922] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   582.923] (II) Module fbdevhw: vendor="X.Org Foundation"
[   582.923] 	compiled for 1.9.0, module version = 0.0.2
[   582.923] 	ABI class: X.Org Video Driver, version 8.0
[   582.923] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   582.923] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[   582.923] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   582.923] (==) RADEON(0): Default visual is TrueColor
[   582.923] (==) RADEON(0): RGB weight 888
[   582.923] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[   582.923] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791e)
[   582.924] (II) RADEON(0): PCI card detected
[   582.924] (II) RADEON(0): KMS Color Tiling: enabled
[   582.924] drmOpenDevice: node name is /dev/dri/card0
[   582.924] drmOpenDevice: open result is 9, (OK)
[   582.924] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[   582.924] drmOpenDevice: node name is /dev/dri/card0
[   582.924] drmOpenDevice: open result is 9, (OK)
[   582.924] drmOpenByBusid: drmOpenMinor returns 9
[   582.924] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[   582.978] (II) RADEON(0): Output VGA-0 has no monitor section
[   583.160] (II) RADEON(0): Output S-video has no monitor section
[   583.569] (II) RADEON(0): Output HDMI-0 has no monitor section
[   583.572] (II) RADEON(0): Output DVI-0 has no monitor section
[   583.626] (II) RADEON(0): EDID for output VGA-0
[   583.626] (II) RADEON(0): Manufacturer: HSD  Model: 8c1  Serial#: 16843009
[   583.626] (II) RADEON(0): Year: 2007  Week: 47
[   583.626] (II) RADEON(0): EDID Version: 1.3
[   583.626] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[   583.626] (II) RADEON(0): Sync:  Separate  Composite
[   583.626] (II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
[   583.626] (II) RADEON(0): Gamma: 2.20
[   583.626] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[   583.626] (II) RADEON(0): First detailed timing is preferred mode
[   583.626] (II) RADEON(0): redX: 0.643 redY: 0.325   greenX: 0.295 greenY: 0.616
[   583.626] (II) RADEON(0): blueX: 0.143 blueY: 0.081   whiteX: 0.310 whiteY: 0.330
[   583.626] (II) RADEON(0): Supported established timings:
[   583.626] (II) RADEON(0): 720x400@70Hz
[   583.626] (II) RADEON(0): 640x480@60Hz
[   583.626] (II) RADEON(0): 640x480@67Hz
[   583.626] (II) RADEON(0): 640x480@72Hz
[   583.626] (II) RADEON(0): 640x480@75Hz
[   583.626] (II) RADEON(0): 800x600@56Hz
[   583.626] (II) RADEON(0): 800x600@60Hz
[   583.626] (II) RADEON(0): 800x600@72Hz
[   583.626] (II) RADEON(0): 800x600@75Hz
[   583.626] (II) RADEON(0): 832x624@75Hz
[   583.626] (II) RADEON(0): 1024x768@60Hz
[   583.626] (II) RADEON(0): 1024x768@70Hz
[   583.626] (II) RADEON(0): 1024x768@75Hz
[   583.626] (II) RADEON(0): 1280x1024@75Hz
[   583.626] (II) RADEON(0): Manufacturer's mask: 0
[   583.626] (II) RADEON(0): Supported standard timings:
[   583.626] (II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 66  vid: 17969
[   583.626] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 66  vid: 18017
[   583.626] (II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   583.626] (II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   583.626] (II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   583.626] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
[   583.626] (II) RADEON(0): #6: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[   583.626] (II) RADEON(0): Supported detailed timing:
[   583.626] (II) RADEON(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
[   583.626] (II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
[   583.626] (II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
[   583.626] (II) RADEON(0): Ranges: V min: 49 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 145 MHz
[   583.626] (II) RADEON(0): Monitor name: HB191
[   583.626] (II) RADEON(0): Serial No: 747PR3XY00747
[   583.626] (II) RADEON(0): EDID (in hex):
[   583.626] (II) RADEON(0): 	00ffffffffffff002264c10801010101
[   583.626] (II) RADEON(0): 	2f1101036c291a782a9bb6a4534b9d24
[   583.626] (II) RADEON(0): 	144f54bfef0031466146714f81408180
[   583.626] (II) RADEON(0): 	9500950f01019a29a0d0518422305098
[   583.626] (II) RADEON(0): 	360098ff1000001c000000fd00314b1e
[   583.626] (II) RADEON(0): 	500e000a202020202020000000fc0048
[   583.626] (II) RADEON(0): 	423139310a20202020202020000000ff
[   583.626] (II) RADEON(0): 	0037343750523358593030373437005c
[   583.626] (II) RADEON(0): EDID vendor "HSD", prod id 2241
[   583.626] (II) RADEON(0): Using EDID range info for horizontal sync
[   583.626] (II) RADEON(0): Using EDID range info for vertical refresh
[   583.626] (II) RADEON(0): Printing DDC gathered Modelines:
[   583.626] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   583.626] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   583.626] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   583.626] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   583.626] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   583.626] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   583.627] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   583.627] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   583.627] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   583.627] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   583.627] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   583.627] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   583.627] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   583.627] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   583.627] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   583.627] (II) RADEON(0): Modeline "640x480"x66.0   26.87  640 664 728 816  480 481 484 499 -hsync +vsync (32.9 kHz)
[   583.627] (II) RADEON(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   583.627] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   583.627] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   583.627] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   583.627] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   583.627] (II) RADEON(0): Printing probed modes for output VGA-0
[   583.627] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   583.627] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   583.627] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   583.627] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   583.627] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   583.627] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   583.627] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[   583.627] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   583.627] (II) RADEON(0): Modeline "1024x768"x66.0   71.64  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   583.627] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   583.627] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   583.627] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   583.627] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   583.627] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   583.627] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   583.627] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[   583.627] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   583.627] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   583.627] (II) RADEON(0): Modeline "640x480"x66.0   26.89  640 664 728 816  480 481 484 499 -hsync +vsync (32.9 kHz)
[   583.627] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   583.627] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   583.800] (II) RADEON(0): EDID for output S-video
[   584.208] (II) RADEON(0): EDID for output HDMI-0
[   584.211] (II) RADEON(0): EDID for output DVI-0
[   584.212] (II) RADEON(0): Output VGA-0 connected
[   584.212] (II) RADEON(0): Output S-video disconnected
[   584.212] (II) RADEON(0): Output HDMI-0 disconnected
[   584.212] (II) RADEON(0): Output DVI-0 disconnected
[   584.212] (II) RADEON(0): Using exact sizes for initial modes
[   584.212] (II) RADEON(0): Output VGA-0 using initial mode 1440x900
[   584.212] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   584.212] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:7ab2000
[   584.212] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[   584.212] (**) RADEON(0): Display dimensions: (410, 260) mm
[   584.212] (**) RADEON(0): DPI set to (89, 87)
[   584.212] (II) Loading sub module "fb"
[   584.212] (II) LoadModule: "fb"
[   584.212] (II) Loading /usr/lib/xorg/modules/libfb.so
[   584.212] (II) Module fb: vendor="X.Org Foundation"
[   584.212] 	compiled for 1.9.0, module version = 1.0.0
[   584.212] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   584.212] (II) Loading sub module "ramdac"
[   584.212] (II) LoadModule: "ramdac"
[   584.212] (II) Module "ramdac" already built-in
[   584.212] (II) Loading sub module "exa"
[   584.212] (II) LoadModule: "exa"
[   584.213] (II) Loading /usr/lib/xorg/modules/libexa.so
[   584.213] (II) Module exa: vendor="X.Org Foundation"
[   584.213] 	compiled for 1.9.0, module version = 2.5.0
[   584.213] 	ABI class: X.Org Video Driver, version 8.0
[   584.213] (II) UnloadModule: "vesa"
[   584.213] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   584.213] (II) UnloadModule: "fbdev"
[   584.213] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   584.213] (II) UnloadModule: "fbdevhw"
[   584.213] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[   584.213] (--) Depth 24 pixmap format is 32 bpp
[   584.213] (II) RADEON(0): [DRI2] Setup complete
[   584.213] (II) RADEON(0): [DRI2]   DRI driver: r300
[   584.213] (II) RADEON(0): Front buffer size: 5244K
[   584.213] (II) RADEON(0): VRAM usage limit set to 108356K
[   584.213] (==) RADEON(0): Backing store disabled
[   584.213] (II) RADEON(0): Direct rendering enabled
[   584.214] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[   584.214] (II) RADEON(0): Setting EXA maxPitchBytes
[   584.214] (II) EXA(0): Driver allocated offscreen pixmaps
[   584.214] (II) EXA(0): Driver registered support for the following operations:
[   584.214] (II)         Solid
[   584.214] (II)         Copy
[   584.214] (II)         Composite (RENDER acceleration)
[   584.214] (II)         UploadToScreen
[   584.214] (II)         DownloadFromScreen
[   584.214] (II) RADEON(0): Acceleration enabled
[   584.214] (==) RADEON(0): DPMS enabled
[   584.214] (==) RADEON(0): Silken mouse enabled
[   584.214] (II) RADEON(0): Set up textured video
[   584.214] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   584.216] (--) RandR disabled
[   584.216] (II) Initializing built-in extension Generic Event Extension
[   584.216] (II) Initializing built-in extension SHAPE
[   584.217] (II) Initializing built-in extension MIT-SHM
[   584.217] (II) Initializing built-in extension XInputExtension
[   584.217] (II) Initializing built-in extension XTEST
[   584.217] (II) Initializing built-in extension BIG-REQUESTS
[   584.217] (II) Initializing built-in extension SYNC
[   584.217] (II) Initializing built-in extension XKEYBOARD
[   584.217] (II) Initializing built-in extension XC-MISC
[   584.217] (II) Initializing built-in extension SECURITY
[   584.217] (II) Initializing built-in extension XINERAMA
[   584.217] (II) Initializing built-in extension XFIXES
[   584.217] (II) Initializing built-in extension RENDER
[   584.217] (II) Initializing built-in extension RANDR
[   584.217] (II) Initializing built-in extension COMPOSITE
[   584.217] (II) Initializing built-in extension DAMAGE
[   584.217] (II) Initializing built-in extension GESTURE
[   584.229] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   584.229] (II) AIGLX: enabled GLX_INTEL_swap_event
[   584.229] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   584.229] (II) AIGLX: enabled GLX_SGI_make_current_read
[   584.229] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   584.229] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[   584.229] (II) GLX: Initialized DRI2 GL provider for screen 0
[   584.230] (II) RADEON(0): Setting screen physical size to 381 x 238
[   584.252] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   584.263] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   584.264] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   584.264] (II) LoadModule: "evdev"
[   584.264] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   584.264] (II) Module evdev: vendor="X.Org Foundation"
[   584.264] 	compiled for 1.9.0, module version = 2.3.2
[   584.264] 	Module class: X.Org XInput Driver
[   584.264] 	ABI class: X.Org XInput driver, version 11.0
[   584.264] (**) Power Button: always reports core events
[   584.264] (**) Power Button: Device: "/dev/input/event1"
[   584.300] (II) Power Button: Found keys
[   584.300] (II) Power Button: Configuring as keyboard
[   584.300] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   584.300] (**) Option "xkb_rules" "evdev"
[   584.300] (**) Option "xkb_model" "pc105"
[   584.300] (**) Option "xkb_layout" "us"
[   584.302] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   584.302] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   584.302] (**) Power Button: always reports core events
[   584.302] (**) Power Button: Device: "/dev/input/event0"
[   584.340] (II) Power Button: Found keys
[   584.340] (II) Power Button: Configuring as keyboard
[   584.340] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   584.340] (**) Option "xkb_rules" "evdev"
[   584.340] (**) Option "xkb_model" "pc105"
[   584.340] (**) Option "xkb_layout" "us"
[   584.348] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/event5)
[   584.348] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev pointer catchall"
[   584.348] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall"
[   584.348] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "WizardPen class"
[   584.348] (II) LoadModule: "wizardpen"
[   584.348] (II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
[   584.349] (II) Module wizardpen: vendor="X.Org Foundation"
[   584.349] 	compiled for 1.9.0, module version = 0.7.4
[   584.349] 	Module class: X.Org XInput Driver
[   584.349] 	ABI class: X.Org XInput driver, version 11.0
[   584.349] (**) Option "Device" "/dev/input/event5"
[   584.380] (--) UC-LOGIC Tablet WP8060U: MaxX:32767 MaxY:32767 MaxZ:1023
[   584.380] (--) UC-LOGIC Tablet WP8060U: aspect ratio:1.33:1
[   584.380] (**) UC-LOGIC Tablet WP8060U is in absolute mode
[   584.380] (**) UC-LOGIC Tablet WP8060U: TopX not set, defaulting to "5%"
[   584.380] (**) UC-LOGIC Tablet WP8060U: TopY not set, defaulting to "5%"
[   584.380] (**) UC-LOGIC Tablet WP8060U: BottomX not set, defaulting to "95%"
[   584.380] (**) UC-LOGIC Tablet WP8060U: BottomY not set, defaulting to "95%"
[   584.380] (II) UC-LOGIC Tablet WP8060U: ScreenX = 1440, ScreenY = 900
[   584.380] (**) UC-LOGIC Tablet WP8060U: TopX                   = 1638
[   584.380] (**) UC-LOGIC Tablet WP8060U: TopY                   = 1638
[   584.380] (**) UC-LOGIC Tablet WP8060U: BottomX                = 31128
[   584.380] (**) UC-LOGIC Tablet WP8060U: BottomY                = 31128
[   584.380] (**) UC-LOGIC Tablet WP8060U: TopZ    (min pressure) = 0
[   584.380] (**) UC-LOGIC Tablet WP8060U: BottomZ (max pressure) = 1023
[   584.380] (**) UC-LOGIC Tablet WP8060U: always reports core events
[   584.380] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
[   584.380] (II) UC-LOGIC Tablet WP8060U Increment: 22
[   584.410] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse1)
[   584.410] (**) UC-LOGIC Tablet WP8060U: Ignoring device from InputClass "WizardPen ignore mouse dev class"
[   584.411] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event2)
[   584.411] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[   584.411] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[   584.411] (**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event2"
[   584.450] (II) Microsoft Comfort Curve Keyboard 2000: Found keys
[   584.450] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[   584.450] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
[   584.450] (**) Option "xkb_rules" "evdev"
[   584.450] (**) Option "xkb_model" "pc105"
[   584.450] (**) Option "xkb_layout" "us"
[   584.451] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event3)
[   584.452] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[   584.452] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[   584.452] (**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
[   584.490] (II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
[   584.490] (II) Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
[   584.490] (II) Microsoft Comfort Curve Keyboard 2000: Found relative axes
[   584.490] (II) Microsoft Comfort Curve Keyboard 2000: Found absolute axes
[   584.490] (II) evdev-grail: failed to open grail, no gesture support
[   584.490] (II) Microsoft Comfort Curve Keyboard 2000: Found keys
[   584.490] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as mouse
[   584.490] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[   584.490] (**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
[   584.490] (**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   584.490] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
[   584.490] (**) Option "xkb_rules" "evdev"
[   584.490] (**) Option "xkb_model" "pc105"
[   584.490] (**) Option "xkb_layout" "us"
[   584.491] (EE) Microsoft Comfort Curve Keyboard 2000: failed to initialize for relative axes.
[   584.491] (II) Microsoft Comfort Curve Keyboard 2000: initialized for absolute axes.
[   584.500] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event4)
[   584.500] (**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
[   584.500] (**) ImPS/2 Logitech Wheel Mouse: always reports core events
[   584.500] (**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event4"
[   584.540] (II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
[   584.540] (II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
[   584.540] (II) ImPS/2 Logitech Wheel Mouse: Found relative axes
[   584.540] (II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
[   584.540] (II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
[   584.540] (**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
[   584.540] (**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   584.540] (II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
[   584.540] (II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
[   584.541] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse0)
[   584.541] (II) No input driver/identifier specified (ignoring)
[   585.087] (II) RADEON(0): EDID vendor "HSD", prod id 2241
[   585.087] (II) RADEON(0): Using hsync ranges from config file
[   585.087] (II) RADEON(0): Using vrefresh ranges from config file
[   585.087] (II) RADEON(0): Printing DDC gathered Modelines:
[   585.087] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   585.088] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   585.088] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   585.088] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   585.088] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   585.088] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   585.088] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   585.088] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   585.088] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   585.088] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   585.088] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   585.088] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   585.088] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   585.088] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   585.088] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   585.088] (II) RADEON(0): Modeline "640x480"x66.0   26.87  640 664 728 816  480 481 484 499 -hsync +vsync (32.9 kHz)
[   585.088] (II) RADEON(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   585.088] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   585.088] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   585.088] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   585.088] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   585.934] (II) RADEON(0): EDID vendor "HSD", prod id 2241
[   585.934] (II) RADEON(0): Using hsync ranges from config file
[   585.934] (II) RADEON(0): Using vrefresh ranges from config file
[   585.934] (II) RADEON(0): Printing DDC gathered Modelines:
[   585.934] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   585.934] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   585.934] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   585.935] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   585.935] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   585.935] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   585.935] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   585.935] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   585.935] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   585.935] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   585.935] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   585.935] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   585.935] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   585.935] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   585.935] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   585.935] (II) RADEON(0): Modeline "640x480"x66.0   26.87  640 664 728 816  480 481 484 499 -hsync +vsync (32.9 kHz)
[   585.935] (II) RADEON(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   585.935] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   585.935] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   585.935] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   585.935] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   586.576] (II) RADEON(0): EDID vendor "HSD", prod id 2241
[   586.576] (II) RADEON(0): Using hsync ranges from config file
[   586.576] (II) RADEON(0): Using vrefresh ranges from config file
[   586.576] (II) RADEON(0): Printing DDC gathered Modelines:
[   586.576] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   586.576] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   586.576] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   586.576] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   586.576] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   586.576] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   586.576] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   586.576] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   586.576] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   586.576] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   586.576] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   586.576] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   586.576] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   586.576] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   586.576] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   586.576] (II) RADEON(0): Modeline "640x480"x66.0   26.87  640 664 728 816  480 481 484 499 -hsync +vsync (32.9 kHz)
[   586.576] (II) RADEON(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   586.576] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   586.576] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   586.576] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   586.576] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   587.216] (II) RADEON(0): EDID vendor "HSD", prod id 2241
[   587.216] (II) RADEON(0): Using hsync ranges from config file
[   587.216] (II) RADEON(0): Using vrefresh ranges from config file
[   587.216] (II) RADEON(0): Printing DDC gathered Modelines:
[   587.216] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   587.216] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   587.216] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   587.216] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   587.216] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   587.216] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   587.216] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   587.216] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   587.216] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   587.216] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   587.216] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   587.216] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   587.216] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   587.216] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   587.216] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   587.216] (II) RADEON(0): Modeline "640x480"x66.0   26.87  640 664 728 816  480 481 484 499 -hsync +vsync (32.9 kHz)
[   587.216] (II) RADEON(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   587.216] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   587.216] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   587.216] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   587.216] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   602.088] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[   604.934] (II) RADEON(0): EDID vendor "HSD", prod id 2241
[   604.934] (II) RADEON(0): Using hsync ranges from config file
[   604.934] (II) RADEON(0): Using vrefresh ranges from config file
[   604.934] (II) RADEON(0): Printing DDC gathered Modelines:
[   604.934] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   604.934] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   604.934] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   604.934] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   604.934] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   604.934] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   604.934] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   604.934] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   604.934] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   604.934] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   604.934] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   604.934] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   604.934] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   604.934] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   604.934] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   604.934] (II) RADEON(0): Modeline "640x480"x66.0   26.87  640 664 728 816  480 481 484 499 -hsync +vsync (32.9 kHz)
[   604.934] (II) RADEON(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   604.934] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   604.934] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   604.935] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   604.935] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   620.966] (II) RADEON(0): EDID vendor "HSD", prod id 2241
[   620.966] (II) RADEON(0): Using hsync ranges from config file
[   620.966] (II) RADEON(0): Using vrefresh ranges from config file
[   620.966] (II) RADEON(0): Printing DDC gathered Modelines:
[   620.966] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   620.966] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   620.966] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   620.966] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   620.966] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   620.966] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   620.966] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   620.966] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   620.966] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   620.966] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   620.966] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   620.966] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   620.966] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   620.966] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   620.966] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   620.966] (II) RADEON(0): Modeline "640x480"x66.0   26.87  640 664 728 816  480 481 484 499 -hsync +vsync (32.9 kHz)
[   620.966] (II) RADEON(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   620.966] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   620.966] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   620.966] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   620.966] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   621.770] (II) RADEON(0): EDID vendor "HSD", prod id 2241
[   621.770] (II) RADEON(0): Using hsync ranges from config file
[   621.770] (II) RADEON(0): Using vrefresh ranges from config file
[   621.770] (II) RADEON(0): Printing DDC gathered Modelines:
[   621.770] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   621.770] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   621.770] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   621.770] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   621.770] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   621.770] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   621.770] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   621.770] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   621.770] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   621.770] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   621.770] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   621.770] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   621.770] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   621.770] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   621.770] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   621.771] (II) RADEON(0): Modeline "640x480"x66.0   26.87  640 664 728 816  480 481 484 499 -hsync +vsync (32.9 kHz)
[   621.771] (II) RADEON(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   621.771] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   621.771] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   621.771] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   621.771] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   624.066] (II) RADEON(0): EDID vendor "HSD", prod id 2241
[   624.066] (II) RADEON(0): Using hsync ranges from config file
[   624.066] (II) RADEON(0): Using vrefresh ranges from config file
[   624.066] (II) RADEON(0): Printing DDC gathered Modelines:
[   624.066] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   624.067] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   624.067] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   624.067] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   624.067] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   624.067] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   624.067] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   624.067] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   624.067] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   624.067] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   624.067] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   624.067] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   624.067] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   624.067] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   624.067] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   624.067] (II) RADEON(0): Modeline "640x480"x66.0   26.87  640 664 728 816  480 481 484 499 -hsync +vsync (32.9 kHz)
[   624.067] (II) RADEON(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[   624.067] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   624.067] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   624.067] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   624.067] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   624.932] FreeType: couldn't find encoding 'iso8859-14' for '/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Georgia_Bold_Italic.ttf'

---

### Post by Favux on 2011-01-03
We're golden!  It's on the wizardpen driver now:
```
[ 584.348] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/event5)
[ 584.348] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev pointer catchall"
[ 584.348] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall"
[ 584.348] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "WizardPen class"
[ 584.348] (II) LoadModule: "wizardpen"
[ 584.348] (II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
[ 584.349] (II) Module wizardpen: vendor="X.Org Foundation"
[ 584.349] compiled for 1.9.0, module version = 0.7.4
[ 584.349] Module class: X.Org XInput Driver
[ 584.349] ABI class: X.Org XInput driver, version 11.0
[ 584.349] (**) Option "Device" "/dev/input/event5"
[ 584.380] (--) UC-LOGIC Tablet WP8060U: MaxX:32767 MaxY:32767 MaxZ:1023
[ 584.380] (--) UC-LOGIC Tablet WP8060U: aspect ratio:1.33:1
[ 584.380] (**) UC-LOGIC Tablet WP8060U is in absolute mode
[ 584.380] (**) UC-LOGIC Tablet WP8060U: TopX not set, defaulting to "5%"
[ 584.380] (**) UC-LOGIC Tablet WP8060U: TopY not set, defaulting to "5%"
[ 584.380] (**) UC-LOGIC Tablet WP8060U: BottomX not set, defaulting to "95%"
[ 584.380] (**) UC-LOGIC Tablet WP8060U: BottomY not set, defaulting to "95%"
[ 584.380] (II) UC-LOGIC Tablet WP8060U: ScreenX = 1440, ScreenY = 900
[ 584.380] (**) UC-LOGIC Tablet WP8060U: TopX = 1638
[ 584.380] (**) UC-LOGIC Tablet WP8060U: TopY = 1638
[ 584.380] (**) UC-LOGIC Tablet WP8060U: BottomX = 31128
[ 584.380] (**) UC-LOGIC Tablet WP8060U: BottomY = 31128
[ 584.380] (**) UC-LOGIC Tablet WP8060U: TopZ (min pressure) = 0
[ 584.380] (**) UC-LOGIC Tablet WP8060U: BottomZ (max pressure) = 1023
[ 584.380] (**) UC-LOGIC Tablet WP8060U: always reports core events
[ 584.380] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
[ 584.380] (II) UC-LOGIC Tablet WP8060U Increment: 22
[ 584.410] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse1)
[ 584.410] (**) UC-LOGIC Tablet WP8060U: Ignoring device from InputClass "WizardPen ignore mouse dev class"
```
This line tells us the driver has your tablet:
```
[ 584.380] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
```
So now you should have linear pressure available.  To enable it in Gimp and other applications that use pressure you'll have to configure your extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom") for an example of how to do it.

---

### Post by HandyGandy on 2011-01-05
Thank you. Everything seems to be functioning OK now.

I have other questions, but those are about software and karmic, so I'll start new threads for those.

---

