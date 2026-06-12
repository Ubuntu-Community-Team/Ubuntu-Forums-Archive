---
title: "ATI Radeon Xpress 200"
date: 2009-08-04
forum: Hardware
---

### Post by zepl on 2009-08-04
I'm trying to install the driver from the ATI website, I've tried the open source driver, and the flgrx one. Neither resolves my issue in blender
*"I asked this over at blenderartists, I'm having a problem selecting things with the right mouse button in blender. I guess I can't post attachments here, but I was told it might be a video card error. I have an ATI Radeon Xpress 200, I looked on their website and found the Catalyst driver, I tried downloading it, and following instructions, i wasn't able to open the file. I looked at the filename and it said "x86_64", even tho I selected the 32bit. I think thats why I can't install it?"*
So, what should my next step be?

---

### Post by Yellow Pasque on 2009-08-04
You have to be running Ubuntu 8.10 or earlier for the proprietary drivers to work for your GPU.

Download Catalyst 9-3 (later ones won't work for your GPU): [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

Then follow this guide :
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

> I looked at the filename and it said "x86_64"
It says x86 and x86_64. ATI uses the same file to install either one.

---

### Post by pastalavista on 2009-08-04
If you're using Jaunty, check out [this site]("http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/"). I have the same graphics as you and I've been trying to fix it for a good while and that fix is the only one to work. Problem is you can never upgrade your grapics again. But since it works right now, I don't need an upgrade. Upgrading to Jaunty was what broke it in the first place.

---

### Post by zepl on 2009-08-05
I haven't looked into the second site, seems more of a last resort thing.
Anyways, I was following these Instructions, [URL="http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_Open_Source_Edge_Drivers"]"Installing Open Source Edge Drivers"
[/URL]

It actually solved ym problem in blender, but it changed my resulution to 800/600, so I added the last part into the */etc/X11/xorg.conf*, loged out and then my screen went blank. I tried booting into recovery mode, and using try to auto solve graphics problems. Didn't work. My systems dual booted, so I'm on XP right now, would it be smart to edit the same file to the original?

---

