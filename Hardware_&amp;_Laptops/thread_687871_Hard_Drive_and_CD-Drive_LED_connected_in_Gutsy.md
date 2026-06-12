---
title: "Hard Drive and CD-Drive LED connected in Gutsy?"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by BandD on 2008-02-04
I've searched through the forums and bug tracker, but there doesn't seem to be a lot of information about this issue and my issue seems to be a little different.  

I started using Gutsy about 3 months ago.  I had to replace my Hard Drive in December, but this issue existed on that drive as well as my new drive.  

The Hard Drive LED is constantly on from the Ubuntu Splash Screen (after GRUB) until, and here's the kicker, I open my CD Drive and close it again (either with a CD loaded or not).  Then my HD LED goes back to 'normal' (ie usually off, and flickers on and off when there is disk activity.)  On occasion, however, espcially if I've been listen to music through Rythmbox from files off my HARD DRIVE, the system will hang for about 10 seconds and then the HD LED is always on again, until I open the CD drive and close it again.  

Both drives were PATA in a Sony Vaio FS620 notebook.  Neither drives were/are being constantly accessed, that I am certain of because 1) there is no disk noise and 2) when I open and close the CD everything is hunky-dory.  

So something is connecting the LED behaviour from the CD drive to the Hard Drive, but I have no idea what.  Very curious.

---

### Post by BandD on 2008-02-05
After some poking around, I'm pretty sure that this issue is related to error outputs in .xsession-errors in my home folder, mostly because when the time the problem occurs lines up with the time this file is last modified.  But I might be totally off.  Here is the info in there, note the errors in the 'Tracker' section lower down especially:


> (process:5352): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5356): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/BandD-laptop:/tmp/.ICE-unix/5349
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
** Message: Not starting remote desktop server


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
Initializing gnome-mount extension
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
sh: jackd: not found
sh: jackd: not found
sh: jackd: not found

The "sh: jackd: not found" is sometimes listed hundreds of times in a row.  In this case it is listed probably about 50 times, but I didn't see the need to include all of them.

Anyway, I'm in over my head here.  But I thought there might be a correlation.

---

