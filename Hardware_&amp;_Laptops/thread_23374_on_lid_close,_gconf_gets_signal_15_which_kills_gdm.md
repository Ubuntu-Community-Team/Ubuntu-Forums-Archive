---
title: "on lid close, gconf gets signal 15 which kills gdm and restarts my gnome session"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by El Rey de Todo on 2005-04-01
I'm currently on my second install of Hoary (the other was redone just because I wanted to ty again), but this time I'm having trouble with ACPI stuff.  I have seen on the forum that many people have had problems with it and simply disabled it, but since I'm using a laptop I don't consider that to be a valid option.  Either way, here's what I've discovered so far about the problem:

If anyone can help with this they'll be my hero.

- Martin

**Symptoms:**
When I close my lid and reopen it, I am logged out of gnome and bac at the gdm login screen.  Also, if I hibernate (yes, I got that working), it gets back to X, but not to my Gnome session, just the logon screen.

Also, the computer will sometimes randomly freeze, though this is not as frequent.  I'm not sure if it is related to the other problem, but I thought I'd mention it anyway.

**Symptoms I DON'T have:**
My video restarts fine.  I don't have to double-switch virtual consoles like some people do.

**Observations:**
gconf is getting signal 15 (restart?) immediatly after i shut the lid.  If I have music playing in Rythmbox, it dies within a few seconds of  the lid closing.

I have plaed with my xorg.conf file (mostly the ATI driver config) trying to see if it might be causing the problem.  I have reverted to the version I was using in my last install (where I didn't have freezing or lid-closing problems) and it still does bad stuff.

I have played with /etc/defaults/acpi-support, trying to see if any of the options in there would fix it.  I've looked up what almost all of the settings do and played with about half of them to no avail.  The file is currently in an almost-original state.

I've got log snipits from every log on my computer for one of the failed lid closing events.  This might help.  I'll attach them at the bottom.

**Hardware** 
I'm using an HP Pavilion zt3000 notebook.
The video card is an ATI Radeon 9600, 64MB non-shared RAM
I'm using the ATI fglrx drivers, latest version off apt.
Anything else needed? ask.

**Log entries** 
from /var/log/acpid:
> [Fri Apr  1 12:02:30 2005] received event "button/lid C136 00000080 00000001"
[Fri Apr  1 12:02:30 2005] notifying client 8769[1000:1000]
[Fri Apr  1 12:02:30 2005] executing action "/etc/acpi/lid.sh"
[Fri Apr  1 12:02:30 2005] BEGIN HANDLER MESSAGES
xscreensaver-command: throttled.

xscreensaver-command: activating and locking.

[Fri Apr  1 12:02:34 2005] END HANDLER MESSAGES
[Fri Apr  1 12:02:34 2005] action exited with status 0
[Fri Apr  1 12:02:34 2005] completed event "button/lid C136 00000080 00000001"
[Fri Apr  1 12:02:57 2005] received event "button/lid C136 00000080 00000002"
[Fri Apr  1 12:02:57 2005] notifying client 8769[1000:1000]
[Fri Apr  1 12:02:57 2005] client has disconnected
[Fri Apr  1 12:02:57 2005] executing action "/etc/acpi/lid.sh"
[Fri Apr  1 12:02:57 2005] BEGIN HANDLER MESSAGES
xscreensaver-command: warning: $DISPLAY is not set: defaulting to ":0.0".
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
xscreensaver-command: can't open display :0.0
[Fri Apr  1 12:02:57 2005] END HANDLER MESSAGES
[Fri Apr  1 12:02:57 2005] action exited with status 1
[Fri Apr  1 12:02:57 2005] completed event "button/lid C136 00000080 00000002"
[Fri Apr  1 12:03:28 2005] client connected from 9073[1000:1000]
[Fri Apr  1 12:03:28 2005] 1 client rule loaded
[Fri Apr  1 12:03:30 2005] received event "battery C11F 00000080 00000001"
[Fri Apr  1 12:03:30 2005] notifying client 9073[1000:1000]
[Fri Apr  1 12:03:30 2005] executing action "/etc/acpi/power.sh"
[Fri Apr  1 12:03:30 2005] BEGIN HANDLER MESSAGES
[Fri Apr  1 12:03:30 2005] END HANDLER MESSAGES
[Fri Apr  1 12:03:30 2005] action exited with status 0
[Fri Apr  1 12:03:30 2005] completed event "battery C11F 00000080 00000001"


from /var/log/daemon.log
> Apr  1 12:02:43 localhost gdm[7303]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

from /var/log/gdm/:0.log
> AUDIT: Fri Apr  1 12:02:57 2005: 8867 X: client 4 rejected from local host
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1


from /var/log/kern.log
> Apr  1 12:02:44 localhost kernel: Fire GL built-in AGP-support
Apr  1 12:02:44 localhost kernel: Based on agpgart interface v0.99 (c) Jeff Hartmann
Apr  1 12:02:44 localhost kernel: agpgart: Maximum main memory to use for agp memory: 439M
Apr  1 12:02:44 localhost kernel: agpgart: Detected an Intel 855PM Chipset, no integrated grapics found.
Apr  1 12:02:44 localhost kernel: agpgart: Detected Intel i855PM chipset
Apr  1 12:02:44 localhost kernel: agpgart: AGP aperture is 256M @ 0xb0000000
Apr  1 12:02:44 localhost kernel: Power management callback for AGP chipset installed
Apr  1 12:02:44 localhost kernel: [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Apr  1 12:02:44 localhost kernel: AGP: Found 2 AGPv2 devices
Apr  1 12:02:44 localhost kernel: AGP: Doing enable for AGPv2
Apr  1 12:02:44 localhost kernel: [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Apr  1 12:02:44 localhost kernel: [fglrx] free  AGP = 256126976
Apr  1 12:02:44 localhost kernel: [fglrx] max   AGP = 256126976
Apr  1 12:02:44 localhost kernel: [fglrx] free  LFB = 35876864
Apr  1 12:02:44 localhost kernel: [fglrx] max   LFB = 35876864
Apr  1 12:02:44 localhost kernel: [fglrx] free  Inv = 0
Apr  1 12:02:44 localhost kernel: [fglrx] max   Inv = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total Inv = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total TIM = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total FB  = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total AGP = 65536


from /var/logmessages
> Apr  1 12:02:42 localhost gconfd (martin-8662): Received signal 15, shutting down cleanly
Apr  1 12:02:43 localhost gconfd (martin-8662): Exiting
Apr  1 12:02:44 localhost kernel: Fire GL built-in AGP-support
Apr  1 12:02:44 localhost kernel: Based on agpgart interface v0.99 (c) Jeff Hartmann
Apr  1 12:02:44 localhost kernel: agpgart: Maximum main memory to use for agp memory: 439M
Apr  1 12:02:44 localhost kernel: agpgart: Detected an Intel 855PM Chipset, no integrated grapics found.
Apr  1 12:02:44 localhost kernel: agpgart: Detected Intel i855PM chipset
Apr  1 12:02:44 localhost kernel: agpgart: AGP aperture is 256M @ 0xb0000000
Apr  1 12:02:44 localhost kernel: Power management callback for AGP chipset installed
Apr  1 12:02:44 localhost kernel: [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Apr  1 12:02:44 localhost kernel: AGP: Found 2 AGPv2 devices
Apr  1 12:02:44 localhost kernel: AGP: Doing enable for AGPv2
Apr  1 12:02:44 localhost kernel: [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Apr  1 12:02:44 localhost kernel: [fglrx] free  AGP = 256126976
Apr  1 12:02:44 localhost kernel: [fglrx] max   AGP = 256126976
Apr  1 12:02:44 localhost kernel: [fglrx] free  LFB = 35876864
Apr  1 12:02:44 localhost kernel: [fglrx] max   LFB = 35876864
Apr  1 12:02:44 localhost kernel: [fglrx] free  Inv = 0
Apr  1 12:02:44 localhost kernel: [fglrx] max   Inv = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total Inv = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total TIM = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total FB  = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total AGP = 65536


from /var/log/syslog
> Apr  1 12:02:42 localhost udev[8816]: removing device node '/dev/vcs7'
Apr  1 12:02:42 localhost udev[8824]: removing device node '/dev/vcsa7'
Apr  1 12:02:42 localhost gconfd (martin-8662): Received signal 15, shutting down cleanly
Apr  1 12:02:43 localhost gconfd (martin-8662): Exiting
Apr  1 12:02:43 localhost gdm[7303]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Apr  1 12:02:44 localhost udev[8839]: creating device node '/dev/vcs12'
Apr  1 12:02:44 localhost udev[8842]: creating device node '/dev/vcsa12'
Apr  1 12:02:44 localhost udev[8850]: creating device node '/dev/vcs7'
Apr  1 12:02:44 localhost udev[8871]: removing device node '/dev/vcs7'
Apr  1 12:02:44 localhost udev[8879]: removing device node '/dev/vcsa7'
Apr  1 12:02:44 localhost udev[8893]: creating device node '/dev/vcs7'
Apr  1 12:02:44 localhost udev[8896]: creating device node '/dev/vcsa7'
Apr  1 12:02:44 localhost kernel: Fire GL built-in AGP-support
Apr  1 12:02:44 localhost kernel: Based on agpgart interface v0.99 (c) Jeff Hartmann
Apr  1 12:02:44 localhost kernel: agpgart: Maximum main memory to use for agp memory: 439M
Apr  1 12:02:44 localhost kernel: agpgart: Detected an Intel 855PM Chipset, no integrated grapics found.
Apr  1 12:02:44 localhost kernel: agpgart: Detected Intel i855PM chipset
Apr  1 12:02:44 localhost kernel: agpgart: AGP aperture is 256M @ 0xb0000000
Apr  1 12:02:44 localhost kernel: Power management callback for AGP chipset installed
Apr  1 12:02:44 localhost kernel: [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Apr  1 12:02:44 localhost kernel: AGP: Found 2 AGPv2 devices
Apr  1 12:02:44 localhost kernel: AGP: Doing enable for AGPv2
Apr  1 12:02:44 localhost kernel: [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Apr  1 12:02:44 localhost kernel: [fglrx] free  AGP = 256126976
Apr  1 12:02:44 localhost kernel: [fglrx] max   AGP = 256126976
Apr  1 12:02:44 localhost kernel: [fglrx] free  LFB = 35876864
Apr  1 12:02:44 localhost kernel: [fglrx] max   LFB = 35876864
Apr  1 12:02:44 localhost kernel: [fglrx] free  Inv = 0
Apr  1 12:02:44 localhost kernel: [fglrx] max   Inv = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total Inv = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total TIM = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total FB  = 0
Apr  1 12:02:44 localhost kernel: [fglrx] total AGP = 65536


from /var/log/user.log
> Apr  1 12:02:42 localhost gconfd (martin-8662): Received signal 15, shutting down cleanly
Apr  1 12:02:43 localhost gconfd (martin-8662): Exiting


---

### Post by alastair on 2005-04-01
No idea really. But .... a couple of things worth a look perhaps.

a) See if using the "radeon" driver makes difference. Who knows?

b) Add some "logger" messages to the shell script : /etc/acpi/lid.sh. See "man logger". i.e. Add debug messages printed after each major operation and see if any cause the problem.

---

### Post by El Rey de Todo on 2005-04-02
Ok, so the problem is FGLRX.  I'm not sure why I didn't check that already.

So how many other people are having this problem? Is it an issue with the driver itself or with the Ubuntu packaging of it?

Here's the device setup from my xorg.conf file.  Is there anything obviously wrong with it?
> 
Section "Device"
    Identifier                          "fgl0"
    Option "backingstore"		"true"
    Option "XaaNoOffscreenPixmaps"	"yes"
	Driver                              "fglrx"
#	Driver				"radeon"
#	Driver				"ati"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
#    Option "DesktopSetup"               "0x00000000" 
#    Option "MonitorLayout"              "LVDS, NONE"
    Option "DesktopSetup"               "0x00000100" 
    Option "MonitorLayout"              "AUTO, NONE"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "off"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "on"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4c66
#    Screen 0
EndSection

---

### Post by alastair on 2005-04-02
It's probably the driver. ATI have a quite poor reputation still. There is a "release notes" on their web site (linux/driver section) that mentions suspend issues (not yours in particular) but little else. The site is very bad, poorly laid out and broken in many places. Linux does not appear a priority market ...

You could check the "rage3d" forums perhaps (linux/drivers) :
[http://www.rage3d.com/board/forumdisplay.php?f=88](http://www.rage3d.com/board/forumdisplay.php?f=88)

But as for "playing" with the conf file ... perhaps worth a try, but hard to decide what to tweak.

---

### Post by El Rey de Todo on 2005-04-03
I've managed to fix the problem it seems.

One of these three seems to have fixed it (these are the new values):

Option "VideoOverlay"               "on"
Option "OpenGLOverlay"              "off"
#     Option "backingstore"           "true"

Any guesses which it might be?  I'm not sure I want to play with it anymore to figure out exactly which it was, but if anyone wants to tell me I'd sure like to know :)

Thanks for the help!

---

