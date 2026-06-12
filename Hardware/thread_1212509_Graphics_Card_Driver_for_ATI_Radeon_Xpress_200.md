---
title: "Graphics Card Driver for ATI Radeon Xpress 200"
date: 2009-07-13
forum: Hardware
---

### Post by Evildemon989 on 2009-07-13
Well, I need to install a graphics driver for my ATI radeon xpress 200 card. Preferably, if someone could tell me how to force ubuntu to check for a proprietary driver for it, without waiting for it to show, that would be great. It won't show up in jaunty, it would only show in ibex. Thanks.

---

### Post by angryfirelord on 2009-07-13
The reason is that Jaunty includes Catalyst 9.4, which drops support for cards below the X2100 series. If you need 3D support, you need to run an older version of Xorg, which means reverting back to Ubuntu 8.04 or 8.10.  The radeonhd driver still has some ways to go.

---

### Post by Evildemon989 on 2009-07-17
Ok, so I'm guessing Catalyst 9.3 works with my card? Is there anyway to get 9.3 on Jaunty?

---

### Post by iamkrazee on 2009-07-17
please see this amd link : [URL="http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English"]

---

### Post by Evildemon989 on 2009-07-17
> **iamkrazee said:**
> please see this amd link : [URL="http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English"]

So, I went to that link, and I looked on the card list and it doesn't list my Radeon Xpress 200. Does it still work with my card?

And will it work with Jaunty? It says this:

> AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

---

### Post by Evildemon989 on 2009-07-20
bump

---

### Post by Evildemon989 on 2009-07-23
Bump again

---

### Post by Evildemon989 on 2009-07-23
Is there anyway to get catalyst 9.3 on jaunty?

---

### Post by Evildemon989 on 2009-07-24
So I tried to install catalyst 9.3 on jaunty from their site. DL'd the .run file, and used their installer instructions. This is what I got when I tried to run it:

```
hadrian@hadrian-desktop:~/Desktop$ sh ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.AeBCLH
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.AeBCLH
hadrian@hadrian-desktop:~/Desktop$ 
```

Anyway I can get this to work?

---

### Post by fthamura on 2009-07-31
i install driver 9.7, and make the VGA flickr.

anyone have success install this driver in jaunty

i prefer to return back to 8.04 :(

---

### Post by SnappyU on 2009-10-03
You need to run this

sh ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/jaunty <--- assuming that you are running jaunty

... I think! :o

> **Evildemon989 said:**
> So I tried to install catalyst 9.3 on jaunty from their site. DL'd the .run file, and used their installer instructions. This is what I got when I tried to run it:

```
hadrian@hadrian-desktop:~/Desktop$ sh ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.AeBCLH
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.AeBCLH
hadrian@hadrian-desktop:~/Desktop$ 
```

Anyway I can get this to work?

---

### Post by nardis_Miles1 on 2009-12-06
> **SnappyU said:**
> You need to run this

sh ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/jaunty <--- assuming that you are running jaunty

... I think! :o

I just ran this and the .deb packages were built successfully. The install required that I also install libstdc++5. I have not yet tried to restart X. Stay tuned (that is, if you are tuned in now).

So the module is built to work with xorg 7.1 not 7.4. This is a complete bust!

Art Edwards

---

### Post by vlad-i on 2009-12-06
and if i am not using jaunty can i still use the same code " sh ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/jaunty"  ? 

 thx

---

