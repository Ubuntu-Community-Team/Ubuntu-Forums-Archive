---
title: "Multiple monitor on Laptop with NVidia video card."
date: 2008-11-21
forum: Hardware
---

### Post by lsim91 on 2008-11-21
I recently buy a new Dell XPS Laptop having a nvidia 8600 (or something like that), with a lot of video output (VGA, HDMI, SP DIF, ...). 

I was surprised by the cruel lack of really usable tools to manage those multiple video outputs.

The gnome multiple screen manager does not detect my external monitors, and the proprietary nvidia setting tool is usefull but not really user friendly.

So, I decide to wrote an easy to use utility !


1 - DESCRIPTION

It's a simple python script adding an icon in notification area with a right click menu allowing user to switch between several multiple screen configuration.

Example :
 - Only Laptop screen,
 - Laptop Screen and external monitor (HDMI or VGA output)
 - Only external ouput,
 - ...

Sound over HDMI is automatically enable/disable.

An "Automatic" mode, can detect plugged screen and choose the better configuration. 

This Automatic mode also detect the lid open/close and automaticaly switch to the better mode.

This detection is done at launch time or on lid open/close (I don't now if it's possible to detect screen plugging / unplugging).


2 - INSTALLATION / CONFIGURATION

This tool is base on the nv-control-dpy command that is NOT included in the nvidia-settings package, but can be build as described here : [http://ubuntuforums.org/showthread.php?p=5809670](http://ubuntuforums.org/showthread.php?p=5809670)

Files :
 - video-mode-icon.py : the python script using pygtk adding the icon in notification area
 - set-video-mode.pl  : a perl script used to parse nv-control-dpy output
 - warty-final-ubuntu-wide.png : the "wide" background (for dual screen modes)

Installation :
 - build nv-control-dpy (see [http://ubuntuforums.org/showthread.php?p=5809670](http://ubuntuforums.org/showthread.php?p=5809670)
 - copy nv-control-dpy to /usr/local/bin
 - copy set-video-mode.pl and video-mode-icon.py to /usr/local/bin
 - copy warty-final-ubuntu-wide.png to /usr/share/backgrounads
 - Use gnome session manager to start video-mode-icon.py at gnome session startup.

You can configure modes available in the notification icon menu by editing the video-mode-icon.py file and updating the "Profiles" variable.

The "wide" background file is used in "two monitor modes", to have a full screen background on each monitor. This "wide" background work for a 1440x900 internal laptop screen and a 1900x1080 FullHD TV. Build your own wide background file if your screens parameters differs.

It has been tested ONLY on my configuration, so, it probably requires minor update to work on your laptop.
Monitor names can differs, "wide" screen background size can be different, HDMI sound output name can change, etc ...
Use the command "nv-control-dpy --probe-dpys" to have the list of connected monitor name.

Have fun !

---

