---
title: "Error upgrading intel graphics driver"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by qewrtyuiop on 2009-01-24
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.1-1ubuntu10.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.1-1ubuntu10.1_i386.deb)

I am trying to update the graphics driver for the intel graphics card on my Aspire one and it is trying to download a package that doesn't exist.  I do have an internet connection and I went on the site to manually download it and it simply wasn't on the list of files.  Any Ideas?
Thanks

---

### Post by pytheas22 on 2009-01-24
A package does exist at [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.1-1ubuntu10](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.1-1ubuntu10).**3_i386.deb**.  It looks like they just changed the version build.  Try running:
```

sudo apt-get update
```

Then try to install the package again.

Also, why are you trying to do this?  Ubuntu updates should take care of this for you...

---

### Post by qewrtyuiop on 2009-01-24
Thanks, it worked.  The updater was actually what was throwing this error.

---

### Post by boffergeld on 2009-01-25
Hi,

I had the issue that I was able to upgrade but afterwards the X-Server was crippled.

To get back to the old version of the driver
download [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.1-1ubuntu10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.1-1ubuntu10_i386.deb)

and "dpkg -i xserver-xorg-video-intel_2.4.1-1ubuntu10_i386.deb"

BTW: the non-working version is 
xserver-xorg-video-intel_2.4.1-1ubuntu10.3_i386.deb

Regards

---

