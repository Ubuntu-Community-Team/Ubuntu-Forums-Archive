---
title: "Broadcom 4328 cant install bcmwl-kernel-source on Kernel 2.6.38"
date: 2011-02-22
forum: Hardware
---

### Post by TuxIsAwesome on 2011-02-22
I'm having some massive issues with Kernel 2.6.38, I cant seem to get bcmwl-kernel-source installed without it giving me issues, here's the output

My Wireless card by the way is a Broadcom 4328


Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.60.48.36+bdcom
Kernel:  2.6.32-29-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-29-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building for 2.6.32-29-generic and 2.6.38-4-generic
Building for architecture x86_64
Building initial module for 2.6.32-29-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-29-generic/updates/dkms/

depmod....

DKMS: install Completed.
Building initial module for 2.6.38-4-generic

Error! Bad return status for module build on kernel: 2.6.38-4-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source

Is there any way to fix this, I really want to use kernel 2.6.38. It occurs on every version of 2.6.38, (-1, -2, -3, and -4) Additionally none of my other kernels have wireless at all either. Why is this happening.

---

