---
title: "ATI Radeon HD 3000 series Setup"
date: 2009-07-03
forum: Hardware
---

### Post by grizlo42 on 2009-07-03
Here is what I did to get my ATI Radeon HD working.

[LIST]
[*]downloaded the ATI Catalyst driver from: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)
[*]chmod +x ati-driver-installer-*.run
[*]fresh install of ubuntu (9.04)
[*]install updates
[*]at this point, i mounted my /home directory which i kept through the install where i kept the driver, but any way of copying the driver installer works.
[*]sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms ia32-libs <== ia32-libs only for 64 bit install
[*]cp to directory containing the driver
[*]sh ati-driver-installer-9-6-x86.x86_64.run --buildpkg Ubuntu/jaunty
[*]sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
[*]sudo apt-get install displayconfig-gtk <== This may not be necessary, but its what i did, and mine is working well so, I put it anyway
[*]sudo gedit /etc/X11/xorg.conf
[*]add this to the driver device section
[/LIST]
```

Section "Device"
	.........[B]
	Identifier	"SOME IDENTIFIER"
	Driver		"fglrx"[/B]
        .........
EndSection

```
[LIST]
[*]sudo aticonfig --initial -f
[*]sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
[*]sudo shutdown -r
[/LIST]

glxgears should be running fine. compiz should be working, and compiz plus opengl programs work :).  Don't enable the restricted module at this point. Hope this helps.

---

