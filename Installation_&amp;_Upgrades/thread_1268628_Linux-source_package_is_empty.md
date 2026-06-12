---
title: "Linux-source package is empty"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by Qbeta on 2009-09-17
Well almost.  I installed it and all I got was a gzipped changelog file.  I want the ubuntu kernel tree.  What's going on here?

---

### Post by lloyd_b on 2009-09-17
> **Qbeta said:**
> Well almost.  I installed it and all I got was a gzipped changelog file.  I want the ubuntu kernel tree.  What's going on here?

"Linux-source"?  I didn't even know there was such a package.

Try getting the sources for the appropriate "linux-image..." package.  For instance, on my system it'd be "apt-get source linux-image-2.6.27-14-generic" (I'm on Intrepid rather than Jaunty, so yours will be different).

Lloyd B.

---

### Post by Qbeta on 2009-09-17
No, ```
apt-get source linux-image-2.6.27-14-generic
``` just gets you the kernel image, that isn't what I want.  Pasted here from the description for linux-source.


> Linux kernel source for version 2.6.28 with Ubuntu patches

This package provides the source code for the Linux kernel version
2.6.28.

This package is mainly meant for other packages to use, in order to build
custom flavours.

If you wish to use this package to create a custom Linux kernel, then it
is suggested that you investigate the package kernel-package, which has
been designed to ease the task of creating kernel image packages.

If you are simply trying to build third-party modules for your kernel,
you do not want this package. Install the appropriate linux-headers
package instead.


---

### Post by lloyd_b on 2009-09-18
> **Qbeta said:**
> No, ```
apt-get source linux-image-2.6.27-14-generic
``` just gets you the kernel image, that isn't what I want.  

Er, no.  "apt-get [COLOR="Red"]source[/COLOR] linux-image-2.6.27-14-generic" downloads a 66Mb tar file, plus a diff file, unpacks the tar file to create a directory (linux-2.6.27) which contains the full source tree for the initial kernel of that version, and then applies the diff file as a patch to bring that source tree up to current.

This is the proper way (afaik) to fetch the kernel source tree for a given kernel version.

If this is *not* what you want, then could you please be more specific about what you *do* want?

Lloyd B.

---

### Post by Qbeta on 2009-09-18
My mistake, I missed the "source" part.  Thanks.

---

