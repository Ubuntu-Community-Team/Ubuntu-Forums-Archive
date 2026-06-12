---
title: "Problem with the latest ATi Radeon Mobility Driver."
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by silvestros on 2007-12-01
I use Ubutu 7.10 and my laptop is a Fujitsu-Siemens Pi1536 with:
intel Core Duo 1,6GHz
1024 MB Ram
ATI Radeon Mobility X1400
I downloaded the driver ati-driver-installer-7-11-x86.x86_64.run from the ati-webpage,
but when i try to install it and give the command:
[COLOR="Purple"]sh ati-driver-installer-7-11-x86.x86_64.run --buildpkg Ubuntu/gutsy[/COLOR]
the terminal gives me this:

[COLOR="Purple"]root@ivo-laptop:/home/ivo/Desktop# sh ati-driver-installer-7-11-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.Mt6039
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.433......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 180: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.Mt6039
[/COLOR]

On the ATI website is written that it supports Intel/AMD and also 32bit and 64bit !!
Is there anyone that knows what should i do?
Thanks!

---

### Post by Mainframe on 2007-12-01
Try this:

[http://albertomilone.com/index.html]("http://albertomilone.com/index.html")

or you can do it the hard way:

[http://ubuntero.org/cochise/weblog/718.html]("http://ubuntero.org/cochise/weblog/718.html")

---

