---
title: "Feisty GNU/Linux on the Fujitsu Stylistic 3400 tablet PC"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by bcw on 2007-05-27
Install the generic Feisty software.  This machine will not boot from a USB drive without some help.  I have the Fujitsu floppy disk drive - see my post **['HowTo install from unbootable CD']("http://ubuntuforums.org/showthread.php?t=244918")**.  There are other schemes to use if you don't have the floppy drive.  I used Xubuntu to accommodate the modest hardware resources.

The system reports install is complete and I choose to reboot.  The screen icons clear, but nothing further happens.  Wait several minutes for the buffers to flush, then power off and restart.

**Display & Stylus**

The touchscreen is handled by the 'fpit' driver, which is not installed by default.  This driver is in the 'universe' repository, which is commented out in '/etc/apt/sources.list' by default.  You must remove the comment character ('#') from the beginning of the line and then update the sources:
```
sudo aptitude update
```

The touchscreen is implemented as a serial device, and must be defined via 'setserial'.  I have seen other posts suggesting boot-up scripts to configure this, but that isn't necessary (although it works, too):
```
sudo aptitude install xserver-xorg-input-fpit setserial
```

Save (or add) these lines to '/etc/serial.conf':
```
/dev/ttyS1 uart 16450 port 0xfd68 irq 5 low_latency baud_base 115200 spd_normal skip_test
```

I have seen other configurations that use '/dev/ttyS3'.  I can't explain the discrepancy.

Edit the Xorg server configuration file:
```
sudo nano -w /etc/X11/xorg.conf
```

The default install includes Sections for Synaptic Touchpads and Wacom tablets, neither of which are used by the ST3400/3500.  Remove all such entries (unless you have them as external peripherals).  Don't forget the lines in the "ServerLayout" Section near the end of the file.

Add this entry to enable the stylus as an input device.  Note I switched the Touchscreen to be the CorePointer device, and not the mouse, and the ST3400 & ST3500 require the 'Passive' option:
```
Section "InputDevice"
        Identifier      "Touchscreen"
        Driver          "fpit"
        Option          "Device"                "/dev/ttyS1"
        Option          "BaudRate"              "9600"
[B]        Option          "Passive"
        Option          "CorePointer"[/B]
#        Option         "Rotate"                "CW" <= works, but screen does not rotate via xrandr
        Option          "MaximumXPosition"      "4070"
        Option          "MaximumYPosition"      "4020"
        Option          "MinimumXPosition"      "0"
        Option          "MinimumYPosition"      "0" 
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
**        Option          "SendCoreEvents"        "true"**
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
```

The 10.4" screen has these dimensions (in millimetres): 211 x 158.  The X server has no idea what size monitor the ST3400 has - to inform it, add the 'DisplaySize' parameter so it can scale fonts, icons, etc. correctly BEFORE you futz with font sizes, etc.  I haven't a clue why this isn't a standard question asked during installation - it saves a great deal of messing about:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-40
        VertRefresh     43-60
**        DisplaySize     211 158**
EndSection
```

Change the "ServerLayout" Section to look like this (be careful about matching Identifiers (the names in "") so they all match up:

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
**        InputDevice     "Touchscreen"**
EndSection
```

**Tablet input**

Search in the Ubuntu forums for a thread titled **'[xstroke 0.6]("http://ubuntuforums.org/showthread.php?t=69476&highlight=xstroke+0.6")'**.  A member '23meg' (thanks, mate) prepared an Ubuntu .deb file you can download and install:
```
dpkg -i xstroke_0.6.cvs20040921-2_i386.deb
```

Run this to provide full-screen handwriting recognition:
```
xstroke &
```

An icon of a green pencil will appear somewhere in your panel - select it and letters 'abc' are superimposed on it to indicate your strokes will be read as text, select again to remove the 'abc' text and your stylus becomes a mere mouse pointer again.

**XVkbd**

After un-commenting the 'Uinverse' lines in '/etc/apt/sources.list' add this:
```
sudo aptitude install xvkbd
```

I use the 'fitaly' keyboard layout.  Edit '/etc/X11/app-defaults/XVkbd' and add this line:
```
#include "XVkbd-fitaly"
```

AAAAGH!
Xubuntu uses gksu.  Fine, but when using any administrative tool, gksu pops up to get my password.  Unfortunately, gksu also greys out all other programs, rendering XVkbd input impossible.  It just won't work.

Fix:
```
sudo nano -w /usr/share/gconf/schemas/gksu.schemas
```

8 lines down, in the section with the key ".../disable-grab", change the <default>false</default> entry to <default>true</default>.  Save the file.  Then run this command to integrate the change:
```
sudo gconf-schemas --register /usr/share/gconf/schemas/gksu.schemas
```

Reboot.

**On-screen keyboard for log-in**

Xubuntu uses GDM by default, but I use KDM for my log-in manager.  I have tried getting the GOK keyboard to appear with GDM, but I have not succeeded.  If someone reading this has, please post a detailed HowTo.

Using KDM:
Adapted from [http://www.handhelds.org/hypermail/tc1000-linux/1/0196.html](http://www.handhelds.org/hypermail/tc1000-linux/1/0196.html)
To provide a login keyboard for the stylus:
In /etc/kde3/kdm/Xsetup, insert this near the beginning (after the first lines):
```
   /usr/bin/xvkbd -geometry +260-0 -no-keypad & 
```

and to remove it after login:
In /etc/kde3/kdm/Xstartup, insert this near the beginning (after the first lines):
```
   kill `ps -u root | grep xvkbd | cut -b 1-5`
```

**Hotpads**

Just Works (tm).
These appear to work through the hardware and need no configuration.  I don't know how to read events from them for programming.

**PCMCIA**

This works if the packages are installed.  See the [GRUMBLE ON] section below for the details.

**USB**

Just Works (tm).

**Power Management**

This system uses APM by default.  To switch to ACPI, edit the 'menu.lst' file to add parameters to the kernel at start-up:
```
sudo nano -w /boot/grub/menu.lst
```

Find the lines that starts like these:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=
```

And add these parameters to that line (substitute your own swap partition for '/dev/hda6').  The 'vga=788' tells the Ctrl+Fn consoles to use the entire display:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=**apm=no acpi=force resume=/dev/hda6 vga=788**
```

Then update the grub options:
```
update-grub
```

Edit '/etc/default/acpi-support' and make these changes (the first is needed, the others may not be):
```
#ACPI_SLEEP_MODE=mem
ACPI_SLEEP_MODE=standby
...
SAVE_VIDEO_PCI_STATE=true
...
DOUBLE_CONSOLE_SWITCH=true
```

I have not been able to get suspend working with the 'mem' parameter.  If someone can, please post the settings.  With this set up, both suspend and hibernate work for me from the Xubuntu shutdown menu.

[GRUMBLE ON]
**Wireless networking and drivers**

This applied with Dapper Drake, and may be relevant now for some network drivers, so I'm leaving it in.  If it doesn't trouble you, just bypass it.

This laptop has an ethernet card built-in, but no physical port - this is only provided by the various expansion docks one might add.  Thus, I use a 3Com AirConnect PCMCIA wifi card for networking.

This card is found and configured automatically during the live session.  Just Works (TM).  But curiously, the packages and settings are not carried over during the install...?!  Grrr...

Here is how I solved this problem.

During a live session (either the initial one, or another after the install is complete and found wanting), have a look at the modules loaded (lsmod), the network settings (ifconfig), and the wireless settings (iwconfig) if appropriate.  From this, get an idea of the modules you might need that were not installed.  'aptitude search' and 'aptitude show <packagename>' can also help here.

From the live session, with networking working, mount a device with persistent storage - an existing hard disk partition, a USB key, a network share, a floppy.  You might want to 'cd' onto the mounted device before continuing.

...and while you're at it, uncomment the 'universe' repository in '/etc/apt/sources.list' and run:
```
sudo aptitude update
```

...to make these sources available, then:
```
sudo aptitude -d download xserver-xorg-input-fpit setserial
```

Download the packages you need.  For instance, I did this:
```
sudo aptitude -d download pcmciautils pcmcia-cs wireless-tools
```

Copy them all off to the persistent storage you mounted (if you aren't saving them there in the first place) so they will be available when you reboot into the installed system.

After rebooting to the installed system, mount the persistent storage you used, cd to it, and install the packages (the versions may have changes since I wrote this, so use the actual names you downloaded):
```
dpkg -i pcmcia-cs_3.2.8-5.2ubuntu7_i386.deb setserial_2.17-43_i386.deb etc..
```

You can do this during the initial Live session, before installing or before leaving the install to avoid my fate.
[/GRUMBLE OFF]

---

### Post by aldebarn42 on 2007-05-27
very useful information thank you!
after a little searching i found a way to get an on screen keyboard using gdm (using xvkbd not gok)

edit /usr/X11/gdm/Init/Default as root
just before the last (exit 0) insert the following:
/usr/bin/X11/xvkbd &

it also appears you cant used a 'theme' on your gdm to make this work 
so run: sudo gdmsetup
and in the 'local' tab set the style to 'plain with face browser'

that did the trick for me, hope it works for you!

---

### Post by TabletGuy on 2007-05-29
Gidday

Great post.

I find onboard to be a better on screen keyboard - doesn't crash and its easy to configure the key layout.

An easy way to configure gksudo not to grab the screen is to use gconf-editor:
in terminal type:
gconf-editor

then 

Apps > gksudo

Then check:

Disable-grab

Problem solved.

---

### Post by bcw on 2007-05-31
I was browsing and found this page:
[TC1000 INSTALL]("http://www.rainbowbreeze.it/images/rainbow_sync/works/installations/tc1000_linux/tc1000_install.txt")

There are instructions (I have not tried this - YMMV) for XVkbd with GDM:

> xvkdb under gdm
([http://linux-tablet-pc.dhs.org/howto.html](http://linux-tablet-pc.dhs.org/howto.html))
([http://homepage3.nifty.com/tsato/xvkbd/](http://homepage3.nifty.com/tsato/xvkbd/))
 apt-get install xvkbd
 edit file /etc/X11/gdm/Init/Default and add the following line before the "exit 0" line
 sleep 15 && /usr/bin/xvkbd -geometry -10-10 & 
 (increment the sleep timeout if xkvbd appeas before the gmd login screen)


As well as some other items of interest.

---

### Post by keithacole on 2007-06-15
ive got xubuntu on my 3500, followed the instructions from here, and i canNOT get fpit working properly.


when i touch the screen, it is only recognizing the touch as being in the upper left hand corner of the screen, rendering touch screen useless.

any suggestions. i have been searching but nothing.

---

### Post by bcw on 2007-06-15
> **keithacole said:**
> when i touch the screen, it is only recognizing the touch as being in the upper left hand corner of the screen, rendering touch screen useless.

any suggestions. i have been searching but nothing.

Please provide some information.

1) When did the digitiser last work correctly?  Did it work in Windows, and when did you last have it working?

2) Please post your xorg.conf file.

Thanks,
Bret

---

### Post by keithacole on 2007-06-15
it was working fine with winxp sp2, and win2k.. last time it was working was with winxpsp2. then i went with damnsmallinux on here.. and then decided to go with xubuntu since im running ubuntu on my desktop

here is the xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
        Identifier      "Touchscreen"
        Driver          "fpit"
        Option          "Device"                "/dev/ttyS1"
        Option          "BaudRate"              "9600"
        Option          "Passive"
#        Option          "CorePointer"
#        Option         "Rotate"                "CW" 
        Option          "MaximumXPosition"      "4096"
        Option          "MaximumYPosition"      "4096"
        Option          "MinimumXPosition"      "0"
        Option          "MinimumYPosition"      "0" 
	Option		"AlwaysCore"		"on"
	Option		"SendCoreEvents"
	Option		"SwapXY"
	Option		"SwapX"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:20:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-40
	VertRefresh	43-60
        DisplaySize     211 158
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice     "Touchscreen"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by bcw on 2007-06-15
> **keithacole said:**
> it was working fine with winxp sp2, and win2k.

Good.  That removes concerns about broken hardware.
> here is the xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
...
Section "InputDevice"
        Identifier      "Touchscreen"
        Driver          "fpit"
        Option          "Device"                "/dev/ttyS1"
        Option          "BaudRate"              "9600"
        Option          "Passive"
#        Option          "CorePointer"
#        Option         "Rotate"                "CW" 
        Option          "MaximumXPosition"      "4096"
        Option          "MaximumYPosition"      "4096"
        Option          "MinimumXPosition"      "0"
        Option          "MinimumYPosition"      "0" 
	Option		"AlwaysCore"		"on"
	Option		"SendCoreEvents"
	Option		"SwapXY"
	Option		"SwapX"
EndSection

...

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:20:0"
EndSection


```

You have a line commented out in your Touchscreen definition:
```
#        Option          "CorePointer"
```
Remove the comment and see the effect.  Note that my original post does not comment out that line.

Separately, you are using the 'vesa' driver.  My 3400 is using the trident driver.  I don't know what difference that might make.  Is there a particular reason for that choice?

If the change I mention above doesn't solve the problem, please post your '/etc/serial.conf' file.

Cheers,
Bret

---

### Post by keithacole on 2007-06-15
uncommenting that line had no effect, how would i go about changing to the driver your using?

---

### Post by bcw on 2007-06-15
> **keithacole said:**
> uncommenting that line had no effect, how would i go about changing to the driver your using?

Edit the file to change that entry to 'trident' and restart X windows.

The fact that you've asked this question leads me to ask in turn, how did you uncomment the line, and did you then restart your machine to see the effect (just checking)?

I also asked that you post the contents of your '/etc/serial.conf' file if this didn't work.  Could you please do that?

Cheers,
Bret

---

### Post by keithacole on 2007-06-16
changing the entry to 'trident' stops x from running alltogether, i had to restart and use nano to change it back to vesa,

anywho here is my /etc/serial.conf

```
/dev/ttyS1 uart 16450 port 0xfd68 irq 5 low_latency baud_base 115200 spd_normal skip_test
```

---

### Post by bcw on 2007-06-17
Your serial.conf file is identical to mine.  I will admit I don't know.  I have seen behaviour such as you mentioned while configuring my own ST3400, but don't remember specifically what fixed it.  I believe it's somewhere between the serial configuration and the xorg.conf file, though.

Please try my xorg.conf file without change.  If it works, you can make changes from this baseline, but for diagnosis, it would be interesting to see if it fixes the issue.  I particularly wonder about the 'Swap' option lines, but it's quick to find out.

Here is my video card (lspci -vv  <= that's two 'v's for 'very verbose'):
> 00:14.0 VGA compatible controller: Trident Microsystems Cyber 9525 (rev 49) (prog-if 00 [VGA])
        Subsystem: Fujitsu Limited. Lifebook C6155
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 255
        Region 0: Memory at fe800000 (32-bit, non-prefetchable) [size=4M]
        Region 1: Memory at fed00000 (32-bit, non-prefetchable) [size=128K]
        Region 2: Memory at fe400000 (32-bit, non-prefetchable) [size=4M]
        [virtual] Expansion ROM at 20000000 [disabled] [size=64K]
        Capabilities: [80] AGP version 1.0
                Status: RQ=33 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
        Capabilities: [90] Power Management version 1
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

Is yours the same, or do you have a different graphics chip?

Here is my xorg.conf.  This is working on my system as I write this message:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Touchscreen"
        Driver		"fpit"
        Option		"Device"		"/dev/ttyS1"
        Option		"BaudRate"		"9600"
	Option		"Passive"
	Option		"CorePointer"
#	Option		"SendCoreEvents"	"true"
#	Option		"AlwaysCore"		"on"
#        Option		"Rotate"		"CW" <= works, but screen does not rotate
        Option		"MaximumXPosition"	"4070"
        Option		"MaximumYPosition"	"4020"
        Option		"MinimumXPosition"	"0"
        Option		"MinimumYPosition"	"0" 
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
#	Option		"CorePointer"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Trident Microsystems Cyber 9525"
	Driver		"trident"
	BusID		"PCI:0:20:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-40
	VertRefresh	43-60
	DisplaySize	211 158
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems Cyber 9525"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Touchscreen"
#	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Please let me know about the video card and the results of using this file.

Cheers,
Bret

---

### Post by keithacole on 2007-06-17
when i started getting the touchscreen to work i started with your "input device" section describing the touchscreen, so i know that configuration doesnt work, the swap options came into play from me looking at other xorg.conf from other stylistic owners, but i cant seem to find anyone with the touchscreen working on the ST3500

here is my lspc -vv

> 00:14.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M (rev 64) (prog-if 00 [VGA])
        Subsystem: Fujitsu Limited. Unknown device 1103
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: I/O ports at 2000 [size=256]
        Region 2: Memory at fc102000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: [5c] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-



---

### Post by bcw on 2007-06-17
From your reply, I can't tell if you used my xorg.conf, or just cut part of it out to combine with other inputs.

Your xorg.conf file with the 'vesa' entry did work for my machine.

However, I notice in your output that you have an ATI video card - did you notice that?
```
00:14.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M (rev 64) (prog-if 00 [VGA])
 
```

Whereas mine has the Trident chipset.

Try both your and my xorg.conf file, but substitute 'ati' for the 'vesa' driver.  But other than that, please try the entire file - after all, if we knew what was going on, we wouldn't be having this conversation at all.

If the behaviour is different for any combination, please say here what the differences are.

If those combinations don't work, copy your '/etc/serial.conf' file off to another name so it's not found at startup, and post the output of these commands:
```
setserial -G /dev/ttySn   <= where 'n' is 0 - 4
```

Since your video hardware is different, your serial ports might be too.

Make sure '/etc/serial.conf' is not found before doing this, or we'll get bad data.

Cheers,
Bret

---

### Post by orengolan on 2007-06-26
Does anyone know how to make the touchscreen work with Fujitsu P1510?
I can't find the folder /usr/X11R6/lib/modules/input" on my tablet...

[http://ubuntuforums.org/showthread.php?t=328035](http://ubuntuforums.org/showthread.php?t=328035)

---

### Post by bcw on 2007-06-26
> **orengolan said:**
> Does anyone know how to make the touchscreen work with Fujitsu P1510?

Apparently quite a few people do.  I searched on the web for "linux Fujitsu P1510" (linux + your text) and immediately found several sites, some including links to other sites, and directions, files, etc.  Have you tried these?

When their instructions work or fail, you can post the details, so others here will know where to look, or what specific problems there are getting Ubuntu to work as these other people have with their chosen Linux distros.

Please let us know how you get on.

Cheers,
Bret

---

### Post by brh-z2 on 2007-08-11
bcw,

Do you still have the 3400 running xubuntu? I've got one that I just installed xubuntu (feisty) on and cannot get the suspend to ram to work correctly. It does suspend, but when I resume I get a black screen. Definite HD activity. Would it be possible for you to post your BIOS settings, menu.lst & acpi-support files. Also any other files that you think would be relivent. I've made the changes that you suggested in your first post and have not had any success. Any help would be greatly apreacited.

---

### Post by keithacole on 2007-08-12
i had it running less touch screen, but it was dropped by my 10 year old and the harddrive is now crap, tells me apt is corrupt and i cant start x, cant reconfigure or do anything, i tried another reinstall, but same thing. so i gotta hit ebay up for another harddrive

---

### Post by bcw on 2007-08-12
> **brh-z2 said:**
> bcw,

Do you still have the 3400 running xubuntu? I've got one that I just installed xubuntu (feisty) on and cannot get the suspend to ram to work correctly. It does suspend, but when I resume I get a black screen.

It's at home, and I won't have Internet for a week or so.

In the meantime, you didn't post your own ACPI settings, which would save time.  Did you overlook this (just checking)?
> Edit '/etc/default/acpi-support' and make these changes (the first is needed, the others may not be):
 
Code:
#ACPI_SLEEP_MODE=mem
ACPI_SLEEP_MODE=standby
...
SAVE_VIDEO_PCI_STATE=true
...
DOUBLE_CONSOLE_SWITCH=true

I have not been able to get suspend working with the 'mem' parameter. If someone can, please post the settings. With this set up, both suspend and hibernate work for me from the Xubuntu shutdown menu.
 

---

### Post by keithacole on 2007-08-12
sorry, but my tablet wont boot until i get a new harddrive for it, when it boots every attempt at a command comes back unknown

---

### Post by everdred on 2007-08-30
> **orengolan said:**
> Does anyone know how to make the touchscreen work with Fujitsu P1510?
I can't find the folder /usr/X11R6/lib/modules/input" on my tablet...

[http://ubuntuforums.org/showthread.php?t=328035](http://ubuntuforums.org/showthread.php?t=328035)

FYI, aldebarn42 and orengolan, the correct path to the file seems to be /etc/gdm/Init/Default

I had to find this through trial and error...

---

### Post by stylistic on 2007-10-10
> **keithacole said:**
> changing the entry to 'trident' stops x from running alltogether, i had to restart and use nano to change it back to vesa,

anywho here is my /etc/serial.conf

```
/dev/ttyS1 uart 16450 port 0xfd68 irq 5 low_latency baud_base 115200 spd_normal skip_test
```

I had the same problem. The simple solution was to add a line break after this line. Now everything works fine.

---

### Post by yosef on 2007-12-26
I was given a stylistic 3500 without memory or hdd or anything.  I cannibalized the mem out of an lt-p600 but the hdd cable is missing, does anyone know where I can find one?  Tried ebay, no luck.  The truth is I have a notebook to cfcard adapter, so I would like to try replacing the harddrive with a cfcard but I still need the cable to connect it unless someone has any other ideas?

---

### Post by bcw on 2007-12-26
I will suggest you join this group:

[http://groups.yahoo.com/group/stylistic/](http://groups.yahoo.com/group/stylistic/)

Someone there might know.

Cheers,
Bret

---

### Post by Mathew Priest on 2008-01-20
Real quick note... I got xubuntu Dapper working on my Stylistic 3400 and it is awesome.  Faster than the original OS and it is easy on the standard 6GB HD.  Everything I need for a lightweight tablet.  The only change I would make would be to adjust the xorg.conf file with the settings:

Option "MaximumXPosition" "4096"
Option "MaximumYPosition" "4096"

Some other settings in the threads recommend +/- 4070x4020 but the registration was a little off.  Everything is great so far!  I'm turning it into an audio system front end, but I'm looking for the slickest UI.  Haven't found one yet though.

-Mat

---

### Post by themischiev on 2008-06-26
Stylistic 3400 Harddrive Image For Download?

Please Someone Have An Image Of The Fujitsu Stylistic 3400 Hard Drive With Ubuntu Installed That I Could Download And Copy To My Stylistic 3400 Hard Drive?

---

### Post by stylistic on 2008-07-04
There are some driver problems on Hardy Heron. See

[http://ubuntuforums.org/showthread.php?t=763380](http://ubuntuforums.org/showthread.php?t=763380)

to solve them.

---

### Post by wnbrandt on 2008-07-07
If I may inquire, what are the advantages to switching from a windows based os? I use the pad mostly to browes web pages (Provides control access) but the machine is getting slow. Would there be a significant speed increase with this switch?

Thanks

Bill

---

### Post by bcw on 2008-07-07
> **wnbrandt said:**
> If I may inquire, what are the advantages to switching from a windows based os? I use the pad mostly to browes web pages (Provides control access) but the machine is getting slow. Would there be a significant speed increase with this switch?

Even if you may not inquire, there are advantages, and they might be advantages to you specifically.

Windows XP Tablet is not available for these machines, but there are handwriting recognition input solutions available for (X,K,U)buntu that run on these machines:

XStroke is like Graffiti(tm) on Palms.  OneStroke appears to use plain printed letters, and Cellwriter appears even better.  (I haven't used any  but XStroke as I do have a full copy of Tablet XP on my main Tablet and I've worked out a way to use the handwriting recognition in Linux on it).

XVkbd, On-board, and GOK provide on-screen keyboards for input, and they're quite configurable - I use a variation of the 'fitaly' layout provided with XVkbd for speed.

Malware exposure is greatly reduced running Linux.  The only reason I won't say there isn't any is that I'm not an expert on security.  The buildup of 'cruft' in Windows machines, including adware, contributes to the slowdown many people experience.  You can run a free anti-virus program (clamav) to avoid downloading malware that might attack other Windows machines on your home network.

You can get support for just about all the media types.  You can even do this when local laws don't allow using them by paying $40 to this company, which sells licenses for them: [https://shop.fluendo.com/]("https://shop.fluendo.com/")

If you want to try anything beyond what you mention above, there is a large body of software available for no money you can try and discard, and an easy mechanism to install it or remove it.  There's also a strong community of people (like here) to help work out ideas or problems.

"Free Software" isn't about money - if I mention that you're free, it doesn't mean I can have you for no money, it means you are free - you can't be locked up.  That's the idea about Free Software, and it's about helping others (no pressure - if you get into it and answer questions some day, that's fine).

Cheers,
Bret

---

