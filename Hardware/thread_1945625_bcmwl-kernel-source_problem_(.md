---
title: "bcmwl-kernel-source problem :("
date: 2012-03-23
forum: Hardware
---

### Post by Fyllling on 2012-03-23
Hi, I had some problems with my broadcom STA wireless driver.

So I did a installation of jockey-gtk to get the 'Hardware Drivers'.

But I couldn't activate my wireless driver due to an error:
InstallArchieves() failed

So after som googleing, I found out that it could be related to the bcmwl-kernel-source, so I tried a reinstall, but I just got a error. And then I tried this fix:
[http://ubuntuforums.org/showpost.php?p=9107408&postcount=11](http://ubuntuforums.org/showpost.php?p=9107408&postcount=11)

But after the reboot where I typed upgrade, I got this :(
```

apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.2.6
Building for architecture i686
Building initial module for 3.2.6

Error! Bad return status for module build on kernel: 3.2.6 (i686)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I am currently running BT5 r2, and I wasn't too sure where to put this, and I apologies if I missplaced it.

Sorry for my english, I haven't been using it for some years now :(
Can anyone help me?



Best regards 
Fyllling

---

### Post by Darent on 2012-03-24
Don't know exactly the problem, but it seems similar to mine. It happened to me after upgrade to the latest kernel 3.2.0-20. The dkms fails to build the module for the new kernel. Try to boot with an older one, mine's working with kernel 3.0.0-16, the latest from the repositories (natty).

It may be a problem with the bcmwl-kernel-source package, or a problem with the linux package. Please post it here if you find another solution.

Sorry for my english too :)

---

