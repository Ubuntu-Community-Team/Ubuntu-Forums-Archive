---
title: "update manager won't update"
date: 2008-11-01
forum: General Help
---

### Post by rapattack1 on 2008-11-01
Hi Update manager popped up and tried to update but I was told to use 'dpkg --configure -a' which i did and got this:
root@studio:~# dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0001' near line 1:
 field name `tostart/pulseaudio-module-xsmp.desktop' must be followed by colon
root@studio:~# 

I am not sure what this means and how to get rid of the error.

---

### Post by ajgreeny on 2008-11-01
Open up that file in gedit as root with ```
gksudo gedit /var/lib/dpkg/updates/0001 
```and look for that line which the error says should have a colon and edit it with the asked for colon.  Save the file and try again to use the ```
sudo dpkg --configure -a
``` then update.

---

### Post by rapattack1 on 2008-11-01
Now it says this when I try the 2nd command you mentioned above:
poppinlockin@studio:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0001' near line 14:
 missing package name
poppinlockin@studio:~$

I hope I saved it correctly?

---

### Post by ajgreeny on 2008-11-01
Is this following an update from 8.04 to 8.10?  If so it may be worth backing up your home and starting again with a clean install of 8.10.

How large is the /var/lib/dpkg/updates/0001?  It may be worth copying it here, or attaching it as a txt file, to see if anyone can help further.  I have a fully updated 8.04 here and have no files in my /var/lib/dpkg/updates/ folder, so I assume you are doing a distro update.

---

### Post by rapattack1 on 2008-11-01
Nope I didn't do an update like what you say. It is Ubuntustudio on the drive that I am saying this is happening to.

I will get on that drive and look that file again.

Here it is:
tostart/pulseaudio-module-xsmp.desktop: 30119bce815d64f09565c1deb5e4fe4d
Description: X11 module for PulseAudio sound server
 PulseAudio, previously known as Polypaudio, is a sound server for POSIX and
 WIN32 systems. It is a drop in replacement for the ESD sound server with
 much better latency, mixing/re-sampling quality and overall architecture.
 .
 This module enables PulseAudio to publish itself as the default sound
 server to the X11 root window automatically upon startup. The is also a
 module to playback a sound file in place of the X11 bell beep.
 .
 The modules are called module-x11-publish and module-x11-bell.
Homepage: [http://www.pulseaudio.org](http://www.pulseaudio.org)
Original-Maintainer: CJ van den Berg <cj@vdbonline.com>

Package: finger
Status: install ok installed
Priority: standard
Section: net
Installed-Size: 76
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: bsd-finger
Version: 0.17-11
Replaces: netstd
Depends: libc6 (>= 2.5-5)
Description: user information lookup program
 finger displays information about the system users.
Original-Maintainer: Anibal Monsalve Salazar <anibal@debian.org>

Package: libwxgtk2.8-0
Status: install ok installed
Priority: optional
Section: libs
I

---

