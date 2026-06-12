---
title: "ATI Drivers - include files have improper version"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by marioallstar on 2005-08-11
I've found some interesting games to play on my Ubuntu machine, but unfortunately can not use any OpenGL application without extremely slow speeds. So I decided to install the ATI drivers.

I went to ATI's website and download the installer file, killed Xorg, and ran it. It proceeds for a while then tells me there have been installation errors. Here is a copy of /usr/share/fglrx/fglrx-install.log:

> [Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
Error:
kernel includes at /lib/modules/2.6.10-5-386/build/include do not match current kernel.
they are versioned as "2.6.10"
instead of "2.6.10-5-386".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux
[Error] Kernel Module : Failed to compile kernel module - please consult readme.
Running "uname -a" returns "Linux luigi 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux"

Does anyone know why files in /lib/modules/**_2.6.10-5-386_**/build/include would have a version of 2.6.10? How could I solve this? Thank you very much in advance.

Edit: Oddly enough /usr/src/linux is linked to /usr/src/linux/linux-source-2.6.10

Here are the contents of /usr/src
> linux (the symbolic link)
linux-headers-2.6.10-5
linux-headers-2.6.10-5-386
linux-patches
linux-source-2.6.10
linux-source-2.6.10.tar
modules
rpm

---

### Post by amohanty on 2005-08-11
Why not try the fglrx drivers in the repos. They work great for me.

AM

---

### Post by marioallstar on 2005-08-11
I have heard before that they are not ideal and often don't work. Maybe I just misread some things. I'll give it a try. Thank you.

---

### Post by marioallstar on 2005-08-11
The repository will not let me install fglrx-6-8-0 because it lacks a version number.
> fglrx-6-8-0:

Package fglrx-6-8-0 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
Also, it says it is an XFree86 package, not an Xorg one.

---

### Post by amohanty on 2005-08-11
What you want to install is
xorg-driver-fglrx

If you cannot see it, enable universe repos.

AM

---

### Post by marioallstar on 2005-08-11
That package was already installed, so I reinstalled it. After restarting Xorg (with Ctrl + Alt + Backspace) I opened a terminal window and typed in fglrxinfo and it returned this:
> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
Doesn't a vendor of "Mesa" mean it wasn't successful?

Edit: I seem to have got it to use the ATI drivers. I will test some 3D applications and check back with the status. Thank you so much for your help so far.

Edit 2: Everything is great. Thank you so much for your help and patience.

---

### Post by amohanty on 2005-08-11
>  Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1) 

This just fine.
To enable 3D accel.

in your xorg.conf replace ati with fglrx and in you /etc/modules add fglrx at the end and reboot.

AM

---

### Post by marioallstar on 2005-08-12
Everything is working just fine, except for the fact that I can't change resolutions when X is open. This is bad because the games have different resolutions than my normal desktop. When I try to run gnome-display-properties, it says this:
> The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.
According to what I have read, there is no XRandR setting in Xorg.conf, does anyone know how I could get this working?

---

### Post by Lux Perpetua on 2005-08-12
The first post here: [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557) addresses that problem. Also make sure you have edited your xorg.conf according to section 5 here: [http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#configure](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#configure)

---

### Post by marioallstar on 2005-08-12
Yeah I actually found it that out and was about to come here and post it. :) Basically, comment out (or delete) this:

> Load "extmod"

In the "module" section and put this in instead:

> SubSection "extmod"
	Option "omit xfree86-dga"
EndSubSection
I know the posts you link to have this, I just thought I would put it here in case anyone stumbles across this post first.

Despite some minor difficulties, this was a relatively easy proccess, actually. Thanks to everyone who posted here for helping out.

---

### Post by marioallstar on 2005-08-12
Edit: Nevermind.

---

