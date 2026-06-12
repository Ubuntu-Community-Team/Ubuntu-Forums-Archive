---
title: "HP L2000, fglrx and suspend/hibernate"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by HankB on 2006-06-04
This is an HP Special Edition L2000 laptop with AMD 64 (Turion) and I have just upgraded to dapper from breezy. This laptop uses the ATI chip set that includes the "Radeon XPRESS 200M" video adapter.

I have also tested out the latest fglrx drivers ( 8.25.18 ). And while I really like the acceleration, they cause suspend to ram and suspend to disk to not work. For the former, the system never resumes and with the latter, it never shuts off. Both of these work with the stock 'ati' driver.

There is an alternate suspend to ram that uses a less drastic ACPI power state. As near as I can tell, that would be invoked by writing 'standby' to /sys/power/state, but this seems to be rejected:

```

root@baobab:/etc/acpi# echo standby > /sys/power/state
bash: echo: write error: No such device
root@baobab:/etc/acpi# cat /sys/power/state
mem disk
root@baobab:/etc/acpi#

```

Any suggestions on how to get this laptop to suspend while using the fglrx would be most welcome!

---

### Post by vespo on 2006-06-06
Hi,
I am afraid to tell you that proprietary ATI driver are NOT suspendable. See also "Known issues" at this link:
[http://www2.ati.com/drivers/linux/linux_8.25.18.html](http://www2.ati.com/drivers/linux/linux_8.25.18.html)

For the moment it is either 3d or suspend, you choose. I have opted for suspend right now, but my baby daughter really liked tux sliding down the hill catching fishes (ppracer game, unusable without ATI DRI).

PS: this is my very first post to ubuntu forums.

---

### Post by tommohawk on 2006-06-06
HankB - I am really curious as to how you have achieved the 3D accel on your laptop.

I have an HP DV8025ea which uses the AMD Turion64 processor and the ATI chipset including the Xpress 200M card.

I had full OpenGL accel working (ATI not MESA!) using Kernel 2.15.23 and the ATI 8.24.8 drivers.  I managed to achieve this using the linux-restricted-modules package and the xorg-drivers-fglrx package thanks to a guide on this forum.

However, a recent upgrade to the 8.25.18 drivers has left my 3D broken and nothing I can do seems to fix it.

I have read elsewhere that there are issues with the 8.25.18 drivers and the Xpress 200M card.

So..... I was wondering exactly what you did to make it work?  Do you have 3D under ATI or MESA because if it is MESA then it is non-accelerated which is what I need!

I have been running Dapper since BETA for a while now and this is the first time it has broke beyond my knowledge level.

PS - Ubuntu Team - Keep up the good work!

---

### Post by HankB on 2006-06-06
[QUOTE=tommohawk]HankB - I am really curious as to how you have achieved the 3D accel on your laptop.
[/QUOTE]

I'm afraid I don't even know if I have 3D accel working. I just know that the 2D stuff is not as dog slow as with the ATI drivers. If you can tell me how to check, I will check and let you know, but I bet the answer is not. From the log all I have is:

```
hbarta@baobab:~$ grep -i accel /var/log/Xorg.0.log
(==) fglrx(0): NoAccel = NO
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
```


vespo,
Pretty good for a first post. Thanks for the info! Too bad when I entered the specific topic number for that issue in their KB it came up as not found. :(

I'm also disaapointed to see that the drivers do not list support for  this card.

---

### Post by HankB on 2006-06-06
Well... I just had kind of a Doh! moment. :roll: 

When I first switched to the fglrx driver I had absolutely no acceleration and found it was because it was turned off in the xorg.conf with
```
     Option      "NoAccel"
```
in the device section for the video driver.

I just changed this to "Accel" for the "ati" driver and found that video performance is not as dog slow. :rolleyes: 

I'm guessing that this remains from an older install (breezy) and was there to deal with some problem in the driver. I now get decent video performance and hibernation no longer works. But hibernation is not a big issue with me. I'm happy to suspend when I'm operating off the power grid.

So... for the most part my problem (slow video and suspend) have been solved.

Thanks for the help.

---

### Post by tommohawk on 2006-06-06
[QUOTE=HankB]I'm afraid I don't even know if I have 3D accel working. I just know that the 2D stuff is not as dog slow as with the ATI drivers. If you can tell me how to check, I will check and let you know, but I bet the answer is not. From the log all I have is:

[/QUOTE]

You need to enter fglrxinfo in a console, if it comes up with MESA then you have no accel, if it says ATI or Radeon then you have accel - simple!

You could also try fgl_glxgears and see your framerate - if it is quite good (100+ at least) then you probably have accel - if it is around 20 like mine then you have no accel.

---

### Post by HankB on 2006-06-06
[QUOTE=tommohawk]You need to enter fglrxinfo in a console, if it comes up with MESA then you have no accel, if it says ATI or Radeon then you have accel - simple!
[/quote]
Like this?
```
hbarta@baobab:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

> 
You could also try fgl_glxgears and see your framerate - if it is quite good (100+ at least) then you probably have accel - if it is around 20 like mine then you have no accel.

But not like this: :(
```
hbarta@baobab:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Floating point exception
hbarta@baobab:~$
```

I have enabled acceleration for the 'ati' driver and it seems tp meet my needs. (I can suspend to RAM) Until they get suspend or hibernate working with the fglrx drivers, I'll stick with that.

thanks,
hank

---

### Post by vespo on 2006-06-14
[QUOTE=vespo]Hi,
I am afraid to tell you that proprietary ATI driver are NOT suspendable. See also "Known issues" at this link:
[http://www2.ati.com/drivers/linux/linux_8.25.18.html](http://www2.ati.com/drivers/linux/linux_8.25.18.html)

For the moment it is either 3d or suspend, you choose. I have opted for suspend right now, but my baby daughter really liked tux sliding down the hill catching fishes (ppracer game, unusable without ATI DRI).

PS: this is my very first post to ubuntu forums.[/QUOTE]

I stand very much corrected. Sorry guys. Very bad first post.

The info I gave you earlier "ati driver are not suspendable" came from my previous experience with fglrx on the same Toshiba Satellite p30 but with other distros (Fedora, SuSE). For those I got to the conclusion above after much feedling and after I found out that ATI recognises the issue.

Yesterday I wanted to install fglrx for my ati 9600 128Mb, knowing that I would loose suspend to RAM and DISK. By the way, the stock ubuntu install of opensource ati r300 and dri was already giving a quite respectable 1000 fps for glxgears. I also knew that the maximum to be expected from 128Mb video card memory was about 2000 fps.

I installed xorg-driver-fglrx with synaptic (from restricted repo I think). Run

```
sudo aticonfig -f --initial
``` 

This edited the xorg.conf but since I knew it fails very often to do the most trivial but most important thing which is to tell xorg.conf to load fglrx instead of the stock you had before, I checked the new xorg.conf and manually edited it by using:

```
sudo nano /etc/X11/xorg.conf
```

looked for the line

```
device "ati"
```

changed to

```
device "fglrx"
```

the above line is usually towards the end of /etc/X11/xorg.conf.
Rebooted and fglrx is working as expected:
1. glxgears about 2000 fps
2. fgl_glxgears about 400 fps
3. correct output for glxinfo
4. brighter display colours and general feel of increased redraw speed for applications. 
Fair enough.

Then I wanted to give suspend a try anyway, closed and saved all unsaved data since I was ready to a hard reset as usual when the laptop failed to resume from suspend with fglrx (both 2ram and 2disk).

MAGIC OF UBUNTU it resumes promptly and without a glitch from both suspend to RAM AND DISK and TUX glides down the ice of planet penguin (ppracer) at 150 frames per second at 800x600 for the joy of my baby daughter.

Actually, I have a minor issue with ACPI (unrelated to ATI): ACPI mistakes the event of AC unplug for the LID closure. I'll look into it later.

Guys, I am more and more impressed with Ubuntu (I'm using it only since a couple of weeks). See also my other post on how the agere winmodem worked almost out-of-the-box.
[http://www.ubuntuforums.org/showthread.php?t=195016&highlight=vespo](http://www.ubuntuforums.org/showthread.php?t=195016&highlight=vespo)

cheers

---

### Post by HankB on 2006-06-14
[QUOTE=vespo]
Then I wanted to give suspend a try anyway, closed and saved all unsaved data since I was ready to a hard reset as usual when the laptop failed to resume from suspend with fglrx (both 2ram and 2disk).

MAGIC OF UBUNTU it resumes promptly and without a glitch from both suspend to RAM AND DISK and TUX glides down the ice of planet penguin (ppracer) at 150 frames per second at 800x600 for the joy of my baby daughter.
[/QUOTE]

So... did you need to do anything to make this work? Are you using any boot options?

I did try both suspend to RAM and suspend to disk with fglrx drivers and neither worked for me. With the ati driver, suspend to RAM works. If I disable acceleration, suspend to disk works also, but then the display is really really slow.

Can you post your xorg.conf so I can compare options?

thanks,
hank

---

### Post by vespo on 2006-06-15
I do not use any boot options apart from vga=791 and I am using a 686 kernel (smp).

Here you go with xorg.conf ...pretty stock though

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/X11/fonts/100dpi"
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
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "it"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
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

Section "DRI"
	Mode         0666
EndSection

```

You may want to have a look at /etc/default/acpi-support also

```

# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true

```

---

