---
title: "ATI 8.42.3 supports DRI &amp; AIGLX! :D But won't work!"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by bmhm on 2007-10-28
Hi,

new ATI drivers  8.42.3 finally support AIGLX!

I always used:
```
sudo bash ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/feisty
```
but it won't work anymore :((

All I get is this:
```


==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/feisty
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.42.3-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 8.42.3-1
 debian/rules build
echo "Using architecture: amd64"

** -- snip --- **

cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.d10473
```

Suggestions? It always worked fine for me before.. I want DRI!! :(( 

Release notes & driver available at: [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

Regards!

---

### Post by bmhm on 2007-11-01
bump

anyone?

---

