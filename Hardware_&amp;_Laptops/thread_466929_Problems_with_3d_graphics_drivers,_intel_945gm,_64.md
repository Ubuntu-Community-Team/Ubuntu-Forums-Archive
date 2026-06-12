---
title: "Problems with 3d graphics drivers, intel 945gm, 64-bit Dapper"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by almkglor on 2007-06-07
Hello, I have a laptop built on an Intel 950GMA board with an Intel 945GM, and an Intel Core Duo.  Installed on the hdd is a 64-bit Ubuntu Dapper Drake.

My main problem is that I dearly suspect that my 3d graphics drivers.  When running Sauerbraten, for example, for *some* maps the game slows to a crawl.  For some, it works fine.  I suspect that it has more to do with the size of the map, really.

Also, I've installed Wine, but running winecfg produces:

almkglor@almkglor-laptop:~$ winecfg
wine: creating configuration directory '/home/almkglor/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
wine: wineprefixcreate failed while creating '/home/almkglor/.wine'.
almkglor@almkglor-laptop:~$ wineserver: could not save registry branch to /home/almkglor/.wine-cu4pQh/system.reg : No such file or directory
wineserver: could not save registry branch to /home/almkglor/.wine-cu4pQh/user.reg : No such file or directory

I read somewhere that this problem is mostly a problem with the drivers.

Finally, I also attempted to install Glest.  Glest produces this message:
glest
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
Exception: OpenGL extension not supported: GL_ARB_texture_env_crossbar, required for Glest

I've done a bit of research, and GL_ARB_texture_env_crossbar *should* work on an Intel 945GM.
I also saw a patch for this, here:
[https://bugs.freedesktop.org/show_bug.cgi?id=8292](https://bugs.freedesktop.org/show_bug.cgi?id=8292)
Unfortunately I can't quite figure out how to compile/install the patch.

---

### Post by almkglor on 2007-06-07
*bump*

---

### Post by ramjet_1953 on 2007-06-08
If you follow this link, it should help:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

You will notice that there are two options.

Option 1. Is probably still the best, although it is a bit more work, as it allows you to run software such as games, that change the resolution on the fly.

Option 2 is much easier, but X crashes if you try to change resolution dynamically.

Regards,
Roger :cool:

---

### Post by almkglor on 2007-06-08
I already have 915resolution installed, and am running at 1280x768.

I've also been trying to get xserver-org-video-intel, but it's not in the Dapper repository.  Don't know how to get it off Feisty and not sure if that would work.

---

### Post by almkglor on 2007-06-08
After upgrading to Edgy Eft, wine now runs.  (Yay DiabloII on Linux!!)

So here's a warning:

At least one guy has had problems running Wine with the following:
1. Ubuntu Dapper Drake 6.06LTS
2. xorg-xserver-video-i810 (no other choice with Dapper)
3. Intel 945GM Video
4. This laptop: [http://65.99.222.146/products.do?action=singleProduct&productid=98](http://65.99.222.146/products.do?action=singleProduct&productid=98)

I think this has something to do with either X or the i810 driver.  Is there some way of knowing what changed between Dapper and Edgy?

---

### Post by ramjet_1953 on 2007-06-09
I have not had any problem with my video on Dapper, Edgy, or Feisty.

I tried the new Intel driver on Feisty, but went back to the i810 driver and 915resolution because the new driver crashes X if you try to change screen resolution dynamically.

How much RAM do you have?
Also, how much shared RAM is allocated to your video in your BIOS settings?

Sometimes playing with these settings can help.

Regards,
Roger :cool:

---

### Post by almkglor on 2007-06-09
The laptop has 1Gb of memory.

I also played around with the shared ram settings in the BIOS.  The BIOS had three settings, 224Mb (Default), 128Mb, and 64Mb.  While I was in Dapper I tried all of them; none worked.  When I upgraded to Edgy I happened to have it set to 64Mb.

As soon as I rebooted into Edgy, I manage to run winecfg, with the BIOS video shared ram setting at 64Mb.  Soon got Diablo II installed and running, even at 64Mb.

I have since set the video ram to 224Mb.

Sauerbraten appears to run more smoothly now too, even on the maps that were slow on me in Dapper.

So yes, is there some way to get the difference between two distributions?  I suspect there's a difference between Dapper and Edgy here that explains why wine suddenly worked on Edgy.

---

