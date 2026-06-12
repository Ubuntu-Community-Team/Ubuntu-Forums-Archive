---
title: "Getting boxes - locale screwed up somehow"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by LoungeLizard on 2009-04-10
I'm researching this issue related to this locale issue and have read hundreds of suggestions and am getting nowhere.  A little history... I've recently executed an update on synaptic on my Hardy machine and suddenly after a required reboot, all I'm getting is a bunch of boxes and I can't log in anymore in the GUI - all I get is a bunch of boxes.  So I alt over to a terminal screen and try 'apt-get update' and nothing is out of date.  But I'm noticing that there were a number of instances of perl errors not being able to set locale and trying to use a default "C"...  hence my research that led me to reading about the perl errors...

So, I try 'sudo dpkg-reconfigure locales'
and again I see the perl locale not getting set and a response of ```
locale: Cannot set LC_ALL to default locale: No such file or directory...
Generating locales...
en_AU.UTF-8... up-to-date
en_BW.UTF-8... up-to-date
en_CA.UTF-8... up-to-date
en_DK.UTF-8... up-to-date
en_GB.UTF-8... up-to-date
en_HK.UTF-8... up-to-date
en_IE.UTF-8... up-to-date
en_IN.UTF-8... up-to-date
en_NG.UTF-8... Cannot open locale definition file en_NG: no such file or directory. Failed.
en_NZ.UTF-8... up-to-date
en_PH.UTF-8... up-to-date
en_SG.UTF-8... up-to-date
en_US.UTF-8... up-to-date
en_ZA.UTF-8... up-to-date
en_ZW.UTF-8... up-to-date 
```etc...

I look in my /etc/environment and see my LANG is set to "en" and everything seems to be in place.  Just for grins, I 'export LC_ALL=en_US.UTF-8' and re-run the generate locales - same messages and still have an error in the en_NG...

So I try to run the following: ```

sudo locale-gen
sudo dpkg-reconfigure locales
sudo apt-get install --reinstall language-pack-en

```Still getting errors and am pulling my hair out.  I've spent hours on this and still no resolution.  Can someone please help???  I have no idea where to go from here and it seems that nothing is helping.

da Lizard

---

### Post by LoungeLizard on 2009-04-10
oh yeah - I should add this ```

$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
LANG="en_US.UTF-8"
LANGUAGE="en"

$ locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LANGUAGE=en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"[FONT=monospace]
[/FONT]LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8[FONT=Verdana]
[/FONT]
```[FONT=Verdana]

still trying to figure something out.  BTW - I'm running all these commands in a ALT window since my X session is already running on another TTY display and I can't type anything in there.  So any GUI-based commands are useless at this point...

and finally...  after trying 'sudo aptitude install locales' for the 10th time...  I get the locales to generate and have resolved at least a PORTION of the problem:  I no longer am getting a slew of PERL errors about not being able to set LC_ALL to default and the 'locale' command completes correctly.

Wierd, it just magically worked this time and not the last previous times...

Now, I still have the problem of xfonts-scalable (1.0.0-6) not configuring correctly: [/FONT]```
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts. See update-fonts-dir for more information.
Options:
  -h, --help display this usage message and exitdpkg: error processing xfonts-scalable (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
xfonts-scalable
E: Sub-process /usr/bin/dpkg returned an error code (1)
```da Lizard

---

### Post by LoungeLizard on 2009-04-10
one other thing...  on a whim, I tried restarting X (ctrl-alt-backspace) to see if the locale generation resolved the square boxes - It DID NOT.  I can get in though, typing my UID and PWD in the login dialog (even though I can't read anything) and I get to gnome - but nothing is readable and nothing is usable; everything is all boxes.  SHEESH...  this is terrible...  At least my cron jobs are still working but I can only monitor my box using command-line and is NOT good at all.  

Please help...  what should I try now to fix the xfonts-scalable?  I tried ```
$ sudo apt-get install --reinstall language-pack-en
$ sudo apt-get install -f
``` all resulting in the same xfonts-scalable having a "usage error" and bombing out

da Lizard

---

### Post by LoungeLizard on 2009-04-10
another update...

I just ran ```
$sudo apt-get install --reinstall xfonts-utils
``` based on  what I read in [https://bugs.launchpad.net/ubuntu/+source/xfonts-scalable/+bug/107687](https://bugs.launchpad.net/ubuntu/+source/xfonts-scalable/+bug/107687) and it seemed to resolve the issue where xfonts-scalable was bombing out.  I can now run ```
$ sudo apt-get install --reinstall language-pack-en 
``` successfully without errors!

BUT...  when I pop over to my X session and restart X, I STILL HAVE BOXES... and am still completely unusable.

I am SO FRUSTRATED!!!


da Lizard

---

### Post by LoungeLizard on 2009-04-10
so...  I get to thinking...  this all started because I executed a synaptic update and something was wanting to be upgraded.  SO...  I think, what the hey - the PERL issue caused the upgrade to abort possibly right in the middle of an update of something.  And I type ```
$ sudo apt-get update
$ sudo apt-get upgrade
``` and we're off to a massive download and install of a ton of stuff.  At any prompt, I choose whatever is the default for answers.  After all's said and done...  I WAY WORSE than I was to begin with...  Now I get a message on a blue screen "Failed to start C server..." and the screen goes black with only a blinking cursor at the top.  I have no TTY screens either.  So, what now...  I wait a few minutes and watch the cursor and look at my machine - no hard drive activity, nothing seems to be happening...  I decide to force a reboot with the reset button on the computer.

It boots - and I choose to verbosely let it boot and notice a failure during boot of "kernel variables" and something about an unknown key.  It continues to boot, eventually getting to a black screen where X is trying to load.  Then an ASCII graphic message comes up saying "Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"  then I get a login prompt telling me I'm at TTY2.  While I'm typing all this, another message comes up: "configuration error - unknown item 'FAIL_DELAY' (notify administrator)

GAWD - WILL IT NEVER END!!!  now I totally hosed!!!  HELP!!!  

da Lizard is going to bed now...  I've had enough disasters for today...

---

### Post by LoungeLizard on 2009-04-10
Sure would be nice if someone could give me a little help...  What do I do to restore my X server?  It is completely hosed now.  I tried to do a 'dpkg-reconfigure xserver-xorg' but got an error message and it failed.  I am still quite concerned about the failed key during the initial bootup so this morning I spent some time poring over my syslog from last night and I'll post it here (attached zipped textfile).  What's most revealing is the entries associated with GDM starting around line 326:```

Apr 10 01:11:05 localhost gdm[4666]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 10 01:11:05 localhost gdm[4666]: PAM [dlerror: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 10 01:11:05 localhost gdm[4666]: PAM adding faulty module: /lib/security/pam_smbpass.so
``` and repeated a number of times in the logfile.  Now how did that happen??? How did the PAM SO file get deleted - was this accomplished during the upgrade?

And here is the gdm log file generated last night:```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux LazFileServer 2.6.15-53-386 #1 PREEMPT Sun Jan 25 23:29:51 UTC 2009 i686
Build Date: 16 March 2006
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 10 01:39:18 2009
(==) Using config file: "/etc/X11/xorg.conf"
(**) RADEON(0): RADEONPreInit
(**) RADEON(0): RADEONScreenInit d0000000 0
(**) RADEON(0): Map: 0xd0000000, 0x02000000
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81ff540)
(**) RADEON(0): Read: 0x0000003c 0x000301f7 0x00000000
(**) RADEON(0): Read: rd=60, fd=503, pd=3
(**) RADEON(0): RADEONSaveMode returns 0x81ff540
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x02000000
(**) RADEON(0):   agp_size         : 0x081ff418
(**) RADEON(0):   agp_base         : 0x081ff418
(**) RADEON(0):   MC_FB_LOCATION   : 0xd1ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1280x768       80.14  1280 1344 1480 1680   768  769  772  795 (24,32)
1280x768       80.14  1280 1344 1480 1680   768  769  772  795 (24,32)
(**) RADEON(0): Pitch = 10485920 bytes (virtualX = 1280, displayWidth = 1280)
(**) RADEON(0): dc=8014, of=16028, fd=356, pd=2
(**) RADEON(0): RADEONInit returns 0x81ffef0
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ffef0)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xd1ffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000003c 0x00010164 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=60, fd=356, pd=1
(**) RADEON(0): GRPH_BUFFER_CNTL from 20205c5c to 20125c5c
(**) RADEON(0): RADEONSaveScreen(0)
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(**) RADEON(0): Initializing backing store
(**) RADEON(0): DRI Finishing init !
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): GRPH_BUFFER_CNTL from 20205c5c to 20125c5c
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 160
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): Initializing DPMS
(**) RADEON(0): Initializing Cursor
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(**) RADEON(0): RADEONScreenInit finished
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Invalid argument
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

Fatal server error:
could not open default font 'fixed'
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff540)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xffff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x003fffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000003c 0x000301f7 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=60, fd=503, pd=3
(**) RADEON(0): Ok, leaving now...
```So I looked at my xorg.config file and found a few WACOM device entries - I don't have any WACOM devices on this machine, so I commented out those lines and did a complete reboot  - since restarting X won't work and trying to force X to run causes a black screen and a loss of my TTY screens (can't switch to another TTY and only get a black screen with a flashing cursor in upper left corner).  Still have no X and I'm still getting the PAM error - AND - I'm noticing that I'm completely missing the entire /etc/X11/Xserver directory <-- it is simply not there at all but the error log indicates there should be a sercurity policy file in there: "error opening security policy file /etc/X11/xserver/SecurityPolicy".  I am displaying below my xorg.conf as well as attaching the Xorg.0.log file (zipped up).

Please help!  --humbly,  da Lizard
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

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
# EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
# EndSection

# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
# EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Driver        "ati"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "KDS"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Monitor        "KDS"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice     "stylus" "SendCoreEvents"
#    InputDevice     "cursor" "SendCoreEvents"
#    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection
```

---

### Post by LoungeLizard on 2009-04-13
** BUMP **

So - where do I go from here???  Anyone???

---

