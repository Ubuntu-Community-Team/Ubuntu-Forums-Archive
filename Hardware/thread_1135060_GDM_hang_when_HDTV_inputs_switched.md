---
title: "GDM hang when HDTV inputs switched"
date: 2009-04-24
forum: Hardware
---

### Post by thatcooldude on 2009-04-24
Hi there!

I seem to be having an issue with the Gnome display manager (GDM) on my Ubuntu 8.10 box that's connected to a 46" Sharp Aquos HDTV.  Ubuntu boots fine, loads fine, displays in full HD beautifully.

I've noticed that when I switch inputs on the TV, wait a few minutes then switch back to the Ubuntu input, GDM is "hung".  It looks as though the video card has overheated and I'm only able to see artifacts of orange hues :D

I then SSH in from another machine (I can access a terminal window on the Ubuntu machine by pressing control + alt + 1 but it doesn't seem to work every time and the resolution is set to something incredibly low making it impossible to read the text)

And upon issuing the command: 

```
sudo /etc/init.d/gdm stop
```

I'm able to successfully kill GDM.  Then issuing the command:

```
sudo /etc/init.d/gdm start
```

Brings GDM back up and everything works again (until I switch the input!).

I think my xorg.conf file is configured incorrectly, but I've run the following command already:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

To no avail :(  Here's the current (automatically generated) xorg.conf file:

```
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
EndSection

```

I'm using an ATI Radeon 9600XT with the proprietary ATI drivers enabled.  "Visual Effects" under my Appearance Preferences are also set to "None".

Any help is greatly appreciated!  Thanks in advance!

---

### Post by thatcooldude on 2009-04-25
Bump :)

---

### Post by thatcooldude on 2009-04-26
[IMG]http://stephenpontes.com/misc/permanent/hdtv_scramble.jpg[/IMG]

That's what it looks like if I switch inputs then switch back after just about a minute.

Seems to happen regardless of whether the FGLRX proprietary drivers are enabled or disabled.

A Control+Alt+Delete works the same as the terminal command to restart GDM

My best guess is that for whatever reason my automatically configured xorg.conf (/etc/X11/xorg.conf) isn't being re-written correctly.  The only other way I know of besides the reconfigure terminal command to get a fresh xorg.conf is to use the live CD or reinstall Ubuntu :/

Bump - anyone? :D

---

### Post by thatcooldude on 2009-04-27
I'm feeling schizophrenic since I'm the only one posting, but I think I've resolved the issue. (Don't want to jinx myself though!)

I figured the issue would probably be related to my xorg.conf file since it didn't seem like there was anything specific written there.  I also set up remote desktop and was able to view my desktop correctly even when it showed up as "corrupted" on the HDTV.

I changed the xorg.conf file section to specifically set my max resolution of the HDTV (1080p or 1920x1080).  If you're experiencing the same issue I've described but aren't using an HDTV, adjust the resolution I've listed below in **bold** to your specification.

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth 24
        SubSection "Display"
                Depth     24
                Modes  **"1920x1080"**
        EndSubSection
EndSection

``` 

I'm pretty sure you can also list multiple resolutions here if you'd like, but from what I can tell Ubuntu (Ibex) seems to automatically detect the available resolutions of plugged in hardware displays.

Based on some minimal testing, the issue seems to be resolved.  I'll continue to play with this a bit more over the next week before absolutely confirming this as "fixed" on my end.  Hopefully this post will help someone else with the same issue in the future! (Please post here if it does!)

---

### Post by thatcooldude on 2009-04-27
Blast!  Came home from work today and was greeted by an all too familiar sight:

[IMG]http://stephenpontes.com/misc/permanent/hdtv_scramble2.jpg[/IMG]

Here is the current content of my xorg.conf:

```
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1920x1080"
        EndSubSection
EndSection

```

I am using the "ATI/AMD proprietary FGLRX graphics driver" (enabled through System > Hardware Drivers), but once again it doesn't seem to make a difference if it's enabled or disabled.

I'm now pretty stuck and don't know what else to try.  If anyone has any ideas, please let me know!

---

### Post by unicycler on 2009-04-27
If you adjust the the resolution from your HDTV, does Gnome rescan for output devices? You could try scaling down then back up... something to try.

---

### Post by thatcooldude on 2009-04-27
So I got the display to hang, then VNC'd in to change my resolution manually (System > Preferences > Screen Resolution) and lowered it one "step" to 1776x1000

Display came back up (just like hitting Control + Alt + Delete or issuing /etc/init.d/gdm stop and then /etc/init.d/gdm start does) at the specified resolution.  Of note, my icons aren't "Human" themed anymore after doing this.  I think I remember this happening with my method of bringing the display back as well, but hadn't mentioned it before.

Here's what the icons look like after bringing the display back:

[IMG]http://stephenpontes.com/misc/permanent/icons.png[/IMG]

Unfortunately, changing the resolution isn't a permanent fix - as soon as I switch inputs back and forth again I'm back to square one.

Thanks for the suggestion!

---

### Post by thatcooldude on 2009-05-11
Resolved:

[http://ubuntuforums.org/showthread.php?p=7261400#post7261400](http://ubuntuforums.org/showthread.php?p=7261400#post7261400)

---

