---
title: "Ubuntu Fails w/ ATI Radeon graphics card!  Should I switch DISTRO?"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by jmbenson89 on 2008-01-23
Ubuntu fails to recognize ATI Radeon HD 2600 Pro graphics card (512 MB, 800 mHz PCIe card).  I checked the incompatibility list and I've seen others with the same issue, but no resolution.  When I install the restricted fglrx drivers for it and reboot, the screen goes black and freezes, and I must reboot and reconfigure the xorg file manually.

I was wondering if anyone found a solution to get these ATI cards to work.  I really want to use 3D desktop effects (compiz-fusion, games, etc.).  Is there a solution on Ubuntu or is there another distro where it does work?

Thanks.

---

### Post by Yellow Pasque on 2008-01-23
A lot of people report success with Method 2 of this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by jmbenson89 on 2008-01-23
Method 2 didn't work.  On this step:

"sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy"

It failed with:

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 195: dpkg-architecture: not found
Error: unsupported architecture:
Removing temporary directory: fglrx-install.d22789

Are those instructions for older ATI cards or do they work on the new DirectX10 ones too?

---

### Post by Yellow Pasque on 2008-01-23
They should work with the newer cards.

I would suggest continuing with that guide, but just doing the express install (i.e. leave out the --buildpkg... part)

---

