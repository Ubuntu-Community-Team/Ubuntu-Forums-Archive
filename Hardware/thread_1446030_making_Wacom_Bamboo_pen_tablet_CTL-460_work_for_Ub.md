---
title: "making Wacom Bamboo pen tablet CTL-460 work for Ubuntu 8.04 Hardy"
date: 2010-04-03
forum: Hardware
---

### Post by statmech on 2010-04-03
Sat, 03 Apr 2010, 11:27:03 EDT

Summary for ubuntu forum (and also for my documentation):

There are many web documents on how to download and install the
linux drivers for wacom tablet devices, starting with

[INDENT]  [The linux Wacom project]("http://linuxwacom.sourceforge.net/index.php/main")
   [/INDENT]

but there was no document dedicated to show how to make the Wacom
Bamboo pen tablet CTL-460 work for Ubuntu 8.04 Hardy.

This document is intended for newbies (like me) who are new to
Wacom devices, in particular the Bamboo pen tablet CTL-460, and
want to make this device work under Ubuntu 8.04 Hardy.

I first downloaded the linux wacom driver linuxwacom-0.8.4-4.tar.bz2,
then followed the instructions in

   [INDENT][13.9 - Building wacom driver On Ubuntu 9.04 64-bit system]("http://linuxwacom.sourceforge.net/index.php/howto/ubuntu")
   [/INDENT]

That was the only howto section for Ubuntu.

Clearly this method did not work ... since it was intended for
Ubuntu 9.04 64-bit system.

A web search led to the following web sites:

   [INDENT][Wacom (ubuntu documentation)]("https://help.ubuntu.com/community/Wacom")
   [/INDENT]

   [INDENT][Ubuntu 8.04 (Hardy Heron) (ubuntu documentation) ]("https://help.ubuntu.com/community/Wacom#Ubuntu%208.04%20(Hardy%20Heron)")
[/INDENT]

   [INDENT][HOWTO: Wacom in 8.04 Hardy, April 24th, 2008 (ubuntu forum)]("http://ubuntuforums.org/showthread.php?t=765915")
   [/INDENT]

I next followed the instructions in the above web site for the
following linux wacom driver versions

   [INDENT]linuxwacom-0.8.4-4[/INDENT]

   [INDENT]linuxwacom-0.8.0-3[/INDENT]

None worked... even though the device properties obtained using the command lsusb in Step 2 gave

[INDENT]   vql@io: tcsh 22> lsusb | grep -i wacom
   Bus 004 Device 002: ID 056a:00d4 Wacom Co., Ltd 
   vql@io: tcsh 23>
[/INDENT]
i.e., the Wacom pen tablet CTL-460 is a "056a" device, and the web
site said that 

   [INDENT]Most models beginning with "056a" should work[/INDENT]

The procedure did not work for the Wacom pen tablet CTL-460.

I looked into the file wacom.udev described in Step 16 in

[INDENT][HOWTO: Wacom in 8.04 Hardy, April 24th, 2008 (ubuntu forum)]("http://ubuntuforums.org/showthread.php?t=765915")
   [/INDENT]

but did not find any wacom device corresponding to the USB device
CTL-460 with ID 056a:00d4:

[INDENT]   Bus 004 Device 002: ID 056a:00d4 Wacom Co., Ltd [/INDENT]

It turned out that the Wacom Bamboo pen tablet CTL-460 was not
yet supported by the stable release of the linuxwacom drivers,
such as version 0.8.4-4.  

  [INDENT] See [post 498]("http://art.ubuntuforums.org/showpost.php?p=8184594&postcount=498") in [p.50]("http://art.ubuntuforums.org/showthread.php?t=765915&page=50") of [HOWTO: Wacom in 8.04 Hardy, April 24th, 2008 (ubuntu forum)]("http://ubuntuforums.org/showthread.php?t=765915")
   [/INDENT]

The inclusion of these newer devices was being incorporated in the 
development versions of linuxwacom.

Another search revealed the following web document:

[INDENT]   [Wacom Bamboo Pen and Touch Series Development (ubuntu forum)]("http://ubuntuforums.org/showpost.php?p=8283168&postcount=1")
[/INDENT]

where they were talking about development linuxwacom version 0.8.5-10
or even 0.8.5-11.  

The development versions of linuxwacom can be obtained from the
sourceforge of linuxwacom under [linuxwacom-dev]("http://sourceforge.net/projects/linuxwacom/files/linuxwacom-dev/").  Only the newer
version [0.8.5-12]("http://sourceforge.net/projects/linuxwacom/files/linuxwacom-dev/0.8.5-12/linuxwacom-0.8.5-12.tar.bz2/download") was available; so I downloaded this version.
But following the above document did not work for the Wacom pen
tablet CTL-460.

[INDENT]UPDATE: I had to reinstall ubuntu 8.04.4 due to a root partition problem when I unplugged the laptop before a complete shutdown!  After that, yum broke down (it is needed in the linuxwacom version 0.8.5-12); it no longer worked for the newer linux kernel 2.4.6-28.  I decided to go with the latest linuxwacom version 0.8.8-8 as of Sep 2010.  Following the same steps described here; it worked (yum was not needed). [/INDENT]

See also

[INDENT] [post 384  Re: New Wacom Bamboo not working]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384")
   [/INDENT]

So I went back to follow the steps in 

[INDENT][HOWTO: Wacom in 8.04 Hardy, April 24th, 2008 (ubuntu forum)]("http://ubuntuforums.org/showthread.php?t=765915")
   [/INDENT]

with the following modification to Step 16.  After downloading the file wacom.udev, edit it to add the
following line for the Wacom Bamboo pen tablet CTL-460:

[INDENT]   ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00d4", SYMLINK+="input/tablet-wacom-bamboo-pen"[/INDENT]

Back up the file

   [INDENT]/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules[/INDENT]

and then copy to overwrite the above file with the modified wacom.udev.

After the above, follow through to Step 19 to reboot; it should work.

To adjust the properties of the pen, run the command wacomcpl:

   [INDENT]vql@io: tcsh 29> wacomcpl
   wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
   vql@io: tcsh 30>[/INDENT]

to bring up a GUI window.  On the left subwindow, click at "stylus"
(pen) to select this device.  On the right, appear the buttons
"Feel", "Tool Buttons", "Tracking", "Screen Mapping".  Click the
button "Feel" allows you to adjust the Tip Sensitivity (soft to
firm, default 4), the Click Force (low to high, default 11), the
Smoothness (low to high, default 4), the Suppress Point (low to high,
default 2).

There are 2 positioning modes: Absolute and relative (like a mouse).
For use as a mouse, it is better to use the relative positioning;
for use to write, it is better to use the absolute positioning.
To select the positioning mode, run wacomcpl to bring up the Wacom
Control Panel, then click "Tool Buttons", and under "Positioning
Mode", select "Absolute" or "Relative".

Check out also the web document

   [INDENT]Linux Wacom Project HOWTO
   [5.1 - Adding the InputDevices]("http://linuxwacom.sourceforge.net/index.php/howto/inputdev")[/INDENT]

After an upgrade of the linux kernel, the pen tablet stopped 
working; for example, I had ffmpeg and the wacom pen tablet work
for 2.6.24-26; for linux kernel 2.6.24-{27,28}, ffmpeg misbehaved,
and the wacom tablet did not work.  (I may have compiled ffmpeg
under 2.6.24-26.)

To reinstall the wacom pen tablet for a specific linux kernel, 
you will need to redo the installation of the linux wacom driver
from Step 7 (reconfigure and recompile), skip Steps 8-12, redo
Steps 13-19.


For Ubuntu 10.04 Lucid LTS, see

    [INDENT][Get Wacom Bamboo Pen Working in Ubuntu Lucid]("http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/")[/INDENT]

On the other hand, there are reasons to stay with ubuntu 8.04, and not upgrade to ubuntu 10.04, since there are programs working under ubuntu 8.04, but not under ubuntu 10.04, e.g., 

[INDENT][Ekee: LaTeX equation editor]("http://rlehy.free.fr/")[/INDENT]

If it is working, don't fix it; wait till you have a new laptop to install a newer OS, such as ubuntu 10.04, which by that time may have all the bugs cleared out, and to find an alternative to programs such as Ekee (if you need them).  I am glad that I decided to reinstall ubuntu 8.04.4 and not ubuntu 10.04, so programs that have been working for me continue to work for me.

---

