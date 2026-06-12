---
title: "Problem with S3 graphics on Winbook N3"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by sirancestor on 2007-03-26
I would appreciate any help with changing screen resolution on Winbook N3 with S3 graphics card. (S3 Graphics Twister or something)

VGA chip integrated in VIA PN133 (VT8603) share memory 32MB, AGP 4X, support for 15/16/24bbp True Color, 3D accelerator.

Native screen resolution for this notebook is 1400*1050 and generic drivers loaded with default installation of Ubuntu 6.10 are set to 1024*768. 

I cannot change resolution and I presume that the drivers that were loaded are not the ones that support this video card properly.

Please help.

---

### Post by s0cket on 2007-03-26
You need to look in your /etc/X11/xorg.conf and make sure everything looks right.  It's pretty straight forward on how to change which video driver Xorg is using.

Another thing to consider.  If you have DRI (driect rendering) support enabled in your xorg.conf you'll not be able to get a 32 meg card to dispay 24 bit color at 1400x1050, not enough video memory with DRI enabled.

Backup your xorg.conf and play around with it a little.

---

### Post by sirancestor on 2007-03-27
Thanks for your help. I did manage to make it work using this post:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Thanks

---

