---
title: "Driver for DynaPro touchscreen"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by rcoconnell on 2007-03-12
I'm trying to get the touchscreen working on a Ramline 510 running Xubuntu (Edgy), and have run into a few problems.  I believe the screen istelf is a DynaPro SC3.  I've downloaded the xserver-xorg-input-dynapro from [http://packages.ubuntulinux.org/edgy/x11](http://packages.ubuntulinux.org/edgy/x11) , and installed it.  I know that at this point I need to add the appropriate stuff to xorg.conf, but I'm not sure what that is -- the man file for the driver doesn't seem to be finished.

I'm a bit confused about where to find the device itself.  In Win98 it appears on COM3, which I think means it should appear on /dev/ttyS2 .  If I run 'cat /dev/ttyS2' and doodle on the screen, though, I don't get any response.  The touchscreen itself is fine since, as I mentioned, it works in Win98.  In fact, I can get some info from the device manager there:

The memory addresses are 03E8-03EF, IRQ 10
It's communicating at 9600 bps
8 data bits
no parity
1 stop bit
Xon/Xoff flow control

Not that I know what exactly that means.

It seems like the general outline should follow [http://ubuntuforums.org/showthread.php?t=158666](http://ubuntuforums.org/showthread.php?t=158666) , but I'm not sure how the options in xorg would be different, and am a bit spooked that I don't get anything from 'cat /dev/ttyS2'

-ross

---

### Post by rcoconnell on 2007-03-13
Some progress -- the dynapro driver is sort of working.  I had to run 

stty -F /dev/ttyS2 speed 9600

from the command line, but then the touchscreen started to respond.  The y-axis is inverted, so that's the next order of business. Suggestions?

-ross

---

### Post by rcoconnell on 2007-03-16
Under 'Section "Module"', I added
Load "dynapro"

Below the other input devices, I added

Section "InputDevice"
Identifier "TouchScreen"
Driver "dynapro"
Option "Type" "Finger"
Option "Device" "/dev/ttyS2"
Option "BaudRate" "9600"
Option "MinX" "1000"
Option "MaxX" "0"
Option "MinY" "900"
Option "MaxY" "0"
Option "SendCoreEvents" "True"
EndSection

and then under 'Section "ServerLayout"', I added

InputDevice "TouchScreen" "SendCoreEvents"

I didn't use a calibration program, as the above settings worked well enough for me. Note that the MinX and MinY are greater than the MaxX and MaxY -- before I set those, the x and y axes were both inverted.

-ross

---

### Post by GlitchZ28 on 2007-03-19
Ross,

Good timing.  I just got my RamLine 510 in the mail on Friday.  Great information on the touchscreen.  I have gotten the TS working as well using the dynapro driver. For informational / googleing purposes here are my Ram Line 510 observations:

Processor - Mobile P3 500
Video - ATI Rage 3D Pro (Use ati X.org driver, no options)
LCD - 800x600 native
Sound - ESS Allegro (Use maestro3 ALSA driver)
Host USB - UHCI - Seems to be reconize devices, haven't tried much

PCMCIA - ??? - PCMCIA modules load and yenta driver finds the hardware, but all my cards timeout. If anyone has information on this (or has it working) let me know.

You can get into the System BIOS by holding down F2 on boot.

To install:
Remove HD from RamLine 510
Intall HD in another box or laptop
Basic Ubuntu Install
Install root on hda1 (or at least GRUB)
Boot Ubuntu on the "install box"
Use fdisk to mark hda1 as bootable
Add the universal repositiory to apt
Install the xserver-xorg-input-dynapro package
Edit /etc/X11/xorg.conf
Change driver to ati for card
Follow above instructions to configure the touchscreen.
Install HD back into RamLine510

Boot and Enjoy!
--Justin

---

### Post by francisco_athens on 2007-03-19
I installed Ubuntu in a similar way as Justin. I'm using Xubuntu though, and am quite pleased with performance ( seems to only use 64 of the 128m of RAM most of the time :D  ).  I tried the above instruction for the screen but the pointer seems to be a bit off (up and to the left about 32px) and the tracking as atrocious anyways, so I just use a trackball instead.   It's not what I'd consider a tablet that one can just hold, but works great hanging on a wall :D

Currently I can watch xvid encoded movies fullscreen in VLC  if they are not too high res <640x480 and play snes emulation games.

I use a wifi usb stick on a usb hub that also has kb and trackball attached.

I would really love a deb of the DRI enabled Mach64 driver, I can't get it to compile for some reason in Edgy. (instructions [HERE]("http://www.ubuntuforums.org/showthread.php?t=7200"). Not sure how much of an improvement it would be tho.

EDIT: I got Mach64 with DRI enabled following the instructions [HERE]("http://www.ubuntuforums.org/showthread.php?t=7200&page=7") (see the Ally_S post and attachment).  There was a file that needed to be changed for it to work with the "generic" linux kernel image (as opposed to the "386" version)....  Now I can play Chromium and egoboo, although FPS games seem a little too slow for comfort.

  
Francisco

---

### Post by rcoconnell on 2007-03-27
To stray from the topic of my original post...  are your sound cards working?  Mine never installed correctly, instead I had to run alsamixer to get it to respond.  Once that was done, VLC would work.  I did some tinkering, though, and managed to wipe it out completely.  I started a thread on it with more info, [http://ubuntuforums.org/showthread.php?t=394546](http://ubuntuforums.org/showthread.php?t=394546)

-ross

---

### Post by francisco_athens on 2007-05-20
Just thought I would chime in that the "onboard" onscreen keyboard works well with the ramline.  there are soem nice instructions for getting the onboard application to show up in the login window [HERE]("http://ubuntuforums.org/archive/index.php/t-304045.html")

onboard-settings will allow you to tweak this application...

additionally you can tweak how it shows up in the login screen with

sudo onboard

if you want to change the font size you can edit the XML file, which is usefull if onboard is made small.  15 is a good size... 

enjoy!

---

### Post by Skyefiera on 2007-07-25
I'm running KBuntu on my Ramline 510, but when I do stty -F /dev/ttyS2, I get

stty: /dev/ttyS2: Input/Output error.

It works fine on ttyS0, but of course, the touch screen isn't attached to it! Any idea what is going on?

---

### Post by francisco_athens on 2007-08-02
Check the BIOS configuration (F2 at boot) to see that the  "COM3" (which is ttyS2) is enabled. sometimes it gets reset.. You may also have to disable com 2 and 4 

references:
[http://www.mp3car.com/vbulletin/general-hardware-discussion/89967-ramline-touchscreen-problem.html](http://www.mp3car.com/vbulletin/general-hardware-discussion/89967-ramline-touchscreen-problem.html)
[http://www.wireless-products.dk/Xplore/RamlinePlll510.htm](http://www.wireless-products.dk/Xplore/RamlinePlll510.htm)

---

