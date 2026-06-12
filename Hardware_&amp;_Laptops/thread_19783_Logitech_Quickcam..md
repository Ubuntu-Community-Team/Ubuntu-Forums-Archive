---
title: "Logitech Quickcam."
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by KennethR on 2005-03-13
How can i get my Logitech Quickcam up and running?
Logitech does not support Linux. 
Is there any 3rd party drivers out there?

Do i have to recompile my kernel?

Thanks for any help.

Cheers,
KennethR

---

### Post by kleeman on 2005-03-13
If you have a Quickcam Pro 3000 or 4000 it is supported. See here for instructions on getting it working:

[http://www.lavrsen.dk/twiki/bin/view/PWC/InstallationStandAloneModuleKernel2x6](http://www.lavrsen.dk/twiki/bin/view/PWC/InstallationStandAloneModuleKernel2x6)

---

### Post by mac57 on 2005-03-14
Logitech Quickcam Pro 4000s are supported by kernel module pwc. I have used this successfully in about 5 different distros. I was pleased to see that Ubuntu 5.04 comes with the latest and greatest, the 10.0.6 version by Luc Saillard. What an excellent start, I thought. 

No joy. At least with the 5.04 Live CD, Gnomemeeting simply complains that it has an error opening /dev/video0, and refuses to go further. I changed permissions on /dev/video0 to ensure that all users had read/write access (the usual cure for this problem) but that did not work. There are only two reasons I can think that this shouldn't works:

1) You HAVE to be a member of group video - I am too new to Gnome to know how to do this, and so I have given up for the moment - I know how to do it in KDE, but not in Gnome.

2) The Saillard driver pretty much REQUIRES that it be compiled against the source for the currently executing kernel. Even minor version differences will stop it from working properly. I am suspecting that the version or pwc provided is not compatible with the kernel used in the Live CD. No matter what, this is egg on the face of Ubuntu, which is vaunted for its hardware recognition and support capabilities. I was disappointed to say the least.

If anyone does get their Logitech Quickcam Pro 4000 going with Ubuntu 5.04, I would love to hear about it. Thanks.

---

