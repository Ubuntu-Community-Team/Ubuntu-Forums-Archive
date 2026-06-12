---
title: "Looking for Ubuntu CreatBot software package"
date: 2015-06-24
forum: Hardware
---

### Post by Xiguus on 2015-06-24
Hi All,
I've just gotten a CreatBot 3D printer (DX02). I'm told there's a debian/ubuntu management package for it, but I can't find it, at least not under that name, so I'm stuck with the Windows interface (nuff sed...). Manufacturer's site is in Chinese, so no help for me there. Does anyone know where this package is stashed?
Thanks in anticipation,
Xiguus.

---

### Post by dino99 on 2015-06-25
Well, is it not so hard to find the specs: [http://www.the3dprinter.com.au/products/creatbot-dx-3d-printer](http://www.the3dprinter.com.au/products/creatbot-dx-3d-printer)
with all the details and needed packages installation (cura-engine) available into the archive.
[https://launchpad.net/ubuntu/+source/cura-engine](https://launchpad.net/ubuntu/+source/cura-engine)

That should work out of the box :p

---

### Post by Xiguus on 2015-06-25
Hi dino99,   Thanks for this.   the3dprinter.com page links to the creatbot download page, which doesn't have a linux package.   AFAICS the required components are (i) drivers for the hardware, and (ii) a nice user interface. I've found the drivers in the repositories and installed arduino, arduino-core and arduino-mk.  There doesn't seem to be a nice user interface, but not to worry...   Looks like I could have dug a bit deeper before calling for the cavalry, but then again, I didn't really have a sense of how complex, or simple, this was likely to be.  I'll run with what I have and let you know how it goes...  Thanks again,  BR Xiguus.

---

### Post by Xiguus on 2015-06-26
Hi All,
 just to wrap this up, the ultimaker website has a complete cura in a deb package [http://software.ultimaker.com/current/cura_15.04-debian_amd64.deb](http://software.ultimaker.com/current/cura_15.04-debian_amd64.deb), so now we're there.;)
Cheers,
Xiguus

---

