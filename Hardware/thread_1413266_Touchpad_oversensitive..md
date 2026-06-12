---
title: "Touchpad oversensitive."
date: 2010-02-22
forum: Hardware
---

### Post by theDaveTheRave on 2010-02-22
Hello all.

I've recently noticed since an update to Jaunty (no i've not yet gone to karmic!), that my laptop touchpad is extremely sensitive.

This is particularly annoying when watching DVD's, as the touchpad causes VLC to jump in and out of fullscreen mode, and it is all but impossible to select the buttons I want to "press".

My current solution is to plug in an external mouse (well trackball is actually my preference..... but.... ;).

so my system is as follows.

Acer Aspire 3680 (about 4 years old now).

here is the output of an lshw, I don't know what bit is for the touchpad, so if you are able to tell me I should then be able to search directly for it

```


~$ lshw
WARNING: you should run this program as super-user.
dartagnon                 
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 502MiB
     *-cpu
          product: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1050MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts pni monitor tm2 xtpr pdcm
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8038 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 14
                serial: 00:16:36:c8:51:d3
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 3
                bus info: pci@0000:0a:03.0
                logical name: wmaster0
                version: 01
                serial: 00:19:7d:40:b8:c0
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.135 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:0a:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:0a:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:96:46:b3:c4:3b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```

I am unable to find any setting in either my gnome or my lxde/openbox system preferences to change the sensitivity of my touhpad.

I hope there is a simple <apt-get> I can perform to get a little applet to help me out, but what is it called???

As always thanks in advance.

David

edit.....

so I have just realised this may be a "VLC" problem. I'm sat here currently using my usb 'mouse' and I just used the touchpad, and there seems to be no problem.

SO now I think that somehow VLC may be what is causing the problem... does that souns possible.

what else can I do to test?

thank again all.

David

---

### Post by pi/roman on 2010-02-22
I would not recommend installing extra applets to control the touchpad. It is better to learn how to adjust the settings yourself, then you can install an applet as a helper, but otherwise 3rd party programs just cause confusion because they interfere with your regular settings.
First look for current settings on the touchpad in xorg.conf
```
cat /etc/X11/xorg.conf
```also look for current hal settings:
```
sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 |  xargs -0 -t cat
```and also list your synclient options:
```
synclient -l
```and also list your touchpad's xinput settings:
```
xinput list --short | grep -i 'touchpad' | grep -o '"[^"]*"' | xargs xinput list-props
```also check to see if you have a "touchpad" on your mouse preferences.

---

### Post by viper250 on 2010-02-22
you can usually adjust the mouse sroperties and the touch pad is considered as a mouse as far as the os is concerned.
even ms windows loads a mouse driver for a touchpad but some touchpads came with a special driver that allowed special adjustments.

---

### Post by theDaveTheRave on 2010-02-22
hello again, sorry for the slow response....

I forgot to mention that I am using both gnome and lxde, I have started using lxde by default, and I can't find anywhere how to get to the mouse/touchpad settings??

However, here are the details as suggested by pi/roman....

```
:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"gb"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection
[COLOR="Purple"]# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection[/COLOR]

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2720 932
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

davem@Dartagnon:~$

```

The bit that I have [COLOR="Purple"]highlighed[/COLOR] would seem to suggest that I'm not using any setting for my input device? is this as it should be? I will try 'uncommenting' the lines to see what happens later on.....

so next up....

```

~$ sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 |  xargs -0 -t cat
[sudo] password for davem: 
cat /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
    </match>
  </device>
</deviceinfo>

```

what exactly does all that mean?? :confused:

and now for the synclient....

```

~$ synclient -l
Can't access shared memory area. SHMConfig disabled?

```

so the error message would seem to be indicative? I tried it with sudo also, and same message was returned.

so in case anyone else is having this problem I did a quick search for SHMConfig, and I found this [page]("/www.samlesher.com/code/enable-shmconfig-for-synaptics-touchpad-on-ubuntu-intrepid-ibex-810") on the web, which on a first read may have the solution to my problems... but I need to check that later....

for now though here is the final output...

```

~$ xinput list --short | grep -i 'touchpad' | grep -o '"[^"]*"' | xargs xinput list-props
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (129):		1
	Synaptics Edges (275):		1632, 5312, 1575, 4281
	Synaptics Finger (276):		24, 29, 255
	Synaptics Tap Time (277):		180
	Synaptics Tap Move (278):		221
	Synaptics Tap Durations (279):		180, 180, 100
	Synaptics Tap FastTap (280):		0
	Synaptics Middle Button Timeout (281):		75
	Synaptics Two-Finger Pressure (282):		280
	Synaptics Scrolling Distance (283):		100, 100
	Synaptics Edge Scrolling (284):		1, 0, 0
	Synaptics Two-Finger Scrolling (285):		1, 0
	Synaptics Edge Motion Pressure (286):		29, 159
	Synaptics Edge Motion Speed (287):		1, 401
	Synaptics Edge Motion Always (288):		0
	Synaptics Button Scrolling (289):		1, 1
	Synaptics Button Scrolling Repeat (290):		1, 1
	Synaptics Button Scrolling Time (291):		100
	Synaptics Off (292):		0
	Synaptics Guestmouse Off (293):		0
	Synaptics Locked Drags (294):		0
	Synaptics Locked Drags Timeout (295):		5000
	Synaptics Tap Action (296):		2, 3, 0, 0, 1, 2, 3
	Synaptics Click Action (297):		1, 1, 1
	Synaptics Circular Scrolling (298):		0
	Synaptics Circular Scrolling Trigger (299):		0
	Synaptics Circular Pad (300):		0
	Synaptics Palm Detection (301):		0
	Synaptics Palm Dimensions (302):		10, 199
	Synaptics Pressure Motion (303):		29, 159
	Synaptics Grab Event Device (304):		1

```

so reading that seems to suggest something is going on! but what precisely? where can I get the details of what each of the settings means?

I'm guessing from reading it that there is some form of '2 finger gesture' stuff going on. I must admit I had a feeling that this may be the case, however how do I confirm that my touchpad will even be able to recognise these gestures??

Thanks so for for your assistance, I've learnt some new things from the output of the above that I didn't even know existed.

I wish I could have found these before posting as it may have negated the requirement to do so a little bit.

As mentioned earlier, I am going to try a few things to see what happens, but not until tomorrow (Tuesday 23rd).

David

---

### Post by pi/roman on 2010-02-22
> Synaptics Tap Action (296):        2, 3, 0, 0, 1, 2, 3This could be what is causing the touchpad to seem too sensitve.  In short it means that pressing in the top right corner is a mouse button 2 click, pressing in the bottom right corner is a mouse button 3 click, tapping with 1 finger is a mouse button 1 click, tapping with 2 fingers is a mouse button 2 click, and tapping with 3 fingers is a mouse button 3 click.  You can set these all to zero with the following:
```
xinput set-int-prop  'SynPS/2 Synaptics TouchPad' 'Synaptics Tap Action' 8 0 0 0 0 0 0 0
```The following output means that shmconfig is disabled.
> ~$ synclient -l
Can't access shared memory area. SHMConfig disabled?
So in order to enable Shmconfig through hal and disable the top-right and bottom right open up your hal configuration and copy in the following lines in red.
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```> <?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>[COLOR=Red]
    <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    <merge key="input.x11_options.rbcornerbutton" type="string">0</merge>
    <merge key="input.x11_options.rtcornerbutton" type="string">0</merge>[/COLOR]
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
    </match>
  </device>
</deviceinfo>Then reboot and you should be able to check your synclient settings:
```
synclient -l
```

---

### Post by theDaveTheRave on 2010-02-23
hi again...

pi/roman, things now seem a little more clear....

So clear in fact I am going to mark this thread as 'solved' as I think I should now be able to solve my issues as you have given me the knowledge to understand what I need to do...



so now I can do a both of these commands,....

if anyone else is having this issue I would recomend either having 2 separate terminals open or Copy /pasting the output to a separate file so as you can view the output side by side...

.... and things now make rather more sense...
so taking a portion of the output from this command..

```

~$ xinput list --short | grep -i 'touchpad' | grep -o '"[^"]*"' | xargs xinput list-props
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (129):		1
	[COLOR="Red"]Synaptics Edges (275):		1632, 5312, 1575, 4281[/COLOR]
	[COLOR="SeaGreen"]Synaptics Finger (276):		24, 29, 255[/COLOR]
	[COLOR="Purple"]Synaptics Tap Time (277):		180[/COLOR]
	[COLOR="Orange"]Synaptics Tap Move (278):		221[/COLOR]
	[COLOR="Navy"]Synaptics Tap Durations (279):		180, 180, 100[/COLOR]
	[COLOR="Yellow"]Synaptics Tap FastTap (280):		0[/COLOR]

```

I have been able to run the output of the synclient command

```
 
~$ synclient -l
Parameter settings:
    [COLOR="Red"]LeftEdge                = 1632
    RightEdge               = 5312
    TopEdge                 = 1575
    BottomEdge              = 4281[/COLOR]
    [COLOR="SeaGreen"]FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255[/COLOR]
    [COLOR="Purple"]MaxTapTime              = 180[/COLOR]
    [COLOR="Orange"]MaxTapMove              = 221[/COLOR]
    [COLOR="Navy"]MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100[/COLOR]
   [COLOR="Yellow"] FastTaps                = 0[/COLOR]

```

here I have summised that the parameter settings are in accordance with the order of the device properties... I have hence highlighted each propety and the relevant setting in a color coordinated manner, for everyone else to have a better understanding of the settings...

other setting include the <two finger pressure>, <edge motion speed> and lots more!!

All this leads me to believe that my touchpad is now pressure sensitive, and can be controlled by 1, 2 or 3 fingers, and with 'gestures' (ie <circular scrolling> is available. But how do I find what the 'gestures' are??

Also this is slightly related... it regards my mouse. The output of the <xinput list> for my attached mouse is as follows...

```
"Logitech USB-PS/2 Trackball"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

It would seem that I have 32 buttons... but I must be blind as I can only see 3 buttons (with the middle button being a 'wheel button') does this mean that I have <multi button> functionality on my mouse also?

so I've done a quick bit of 'binary math'

3 true button
1 wheel
1 ball

total = 5

or somewhere between 
00001

and

11111

in binary, or equivalent to 32 ! but how do I find the combinations 

So I used the command
```

~$ xinput list --short | grep -i 'touchpad' | grep -o '"[^"]*"' | xargs xinput list-props
```

and changed the 'touchpad' for 'trackball', and got the following...

```

~$ xinput list --short | grep -i 'trackball' | grep -o '"[^"]*"' | xargs xinput list-props
Device 'Logitech USB-PS/2 Trackball':
	Device Enabled (129):		1
	Evdev Axis Inversion (266):		0, 0
	Evdev Reopen Attempts (263):		10
	Evdev Axis Calibration (264):		
	Evdev Axes Swap (265):		0
	Evdev Middle Button Emulation (267):		2
	Evdev Middle Button Timeout (268):		50
	Evdev Wheel Emulation (269):		0
	Evdev Wheel Emulation Axes (270):		0, 0, 4, 5
	Evdev Wheel Emulation Inertia (271):		10
	Evdev Wheel Emulation Timeout (272):		200
	Evdev Wheel Emulation Button (273):		4
	Evdev Drag Lock Buttons (274):		0

```

---

### Post by pi/roman on 2010-02-23
A couple more things for you as you configure your touchpad, you can use synaptics manual by typing in terminal:
```
man synaptics
```will give definitions of the different options available.  These should be entered into your hal configuration as you did with these two commands:[COLOR=Red]
    [/COLOR]> [COLOR=Red]<merge key="input.x11_options.rbcornerbutton" type="string">0</merge>
    <merge key="input.x11_options.rtcornerbutton" type="string">0</merge>[/COLOR]and not into xorg.conf as the manual suggests because if both configurations are enabled they will conflict with each other and cause interference.

---

### Post by mr.frisky on 2012-09-12
Hi all,

Another potential solution is to ensure the SDL_MOUSE_RELATIVE environment var is set to 0.

This inhibits weird behaviour in libSDL (used for loads of cross-platform games).

```
export SDL_MOUSE_RELATIVE=0
```

Try setting the var in a terminal, then running your game from that terminal: If it line works, you can add the following line to .bashrc

Cheers,
Tim

---

### Post by overdrank on 2012-09-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

