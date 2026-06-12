---
title: "How to install ATI drivers, tried the guide but no luck"
date: 2008-08-03
forum: General Help
---

### Post by Recall on 2008-08-03
Need some help here, I have tried various different ways to install the drivers but nothing works.

I have downloaded the latest ATI driver to my desktop.

ati-driver-installer-8-7-x86.x86_64.run

I then went to this guide

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I did the following:

sudo apt-get update
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)

Which worked

Then did:

sh ati-driver-installer-8-7-x86.x86_64.run --buildpkg Ubuntu/hardy

And get:

sh: Can't open ati-driver-installer-8-7-x86.x86_64.run

Then I read here:

[http://ubuntuforums.org/showthread.php?t=866495&page=2](http://ubuntuforums.org/showthread.php?t=866495&page=2)

To do the following:

chmod +x ati-driver-installer-8-7-x86.x86_64.run --buildpkg Ubuntu/8.04 

Which gave me:

chmod: unrecognised option `--buildpkg'
Try `chmod --help' for more information.

And thats it, cannot get any further. I am using the 64bit version and installed the libs32 thing that I was told to. In fact I followed the guide to the letter, so what am I missing?

---

### Post by Recall on 2008-08-03
OK had to type cd~ desktop

Next thing, how do I get vysnc on the desktop. Windows tear all over the place currently :(

---

