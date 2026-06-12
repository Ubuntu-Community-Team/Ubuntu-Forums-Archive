---
title: "AMD/ATI driver updates..."
date: 2012-02-29
forum: Hardware
---

### Post by ragtag on 2012-02-29
What's the update policy on proprietary ATI drivers in Ubuntu. The current version in 11.10 is a few notches behind the latest one. Are these left untouched, until next release (i.e. 12.04).

I've been wanting to get working OpenCL to take advantage of the new Cycles renderer in Blender, but don't really want to go through the hassle of installing the latest drivers manually...and having to recompile kernel modules with every kernel update.

Yes, yes....I know I'm being lazy. :)

---

### Post by Mark Phelps on 2012-03-01
Sorry, haven't used the restricted AMD drivers in a while, but from what I recall, if you install them using the Additional Hardware option, when you do an update that changes the kernel version, the drivers are automatically removed and reinstalled.  When you install them manually from a download from AMD, I believe you have to do that yourself.

And, from what I recall, the driver version does not change once the distro version is released.

---

### Post by Yellow Pasque on 2012-03-01
The policy used to be no updates once the Ubuntu version was released. That's changed somewhat with the addition of fglrx-updates package, though that isn't keeping pace with the AMD releases.

> and having to recompile kernel modules with every kernel update.


That's what dkms is for (to do that automatically). [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

