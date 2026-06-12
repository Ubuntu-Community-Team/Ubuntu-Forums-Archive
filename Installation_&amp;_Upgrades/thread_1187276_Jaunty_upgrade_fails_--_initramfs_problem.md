---
title: "Jaunty upgrade fails -- initramfs problem?"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by TVTrukChik on 2009-06-14
I tried to run the upgrade from Intrepid to Jaunty via the update manager.  Got a failure saying to run dpkg --configure -a, and another message saying  _cache->open() failed. Ran dpkg --configure, and wound up with this:

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-12-generic
cpio: ./sbin/cryptsetup: Cannot stat: No such file or directory
cpio: ./sbin/dmsetup: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-12-generic
dpkg: subprocess post-installation script returned error exit status 1

```

Googling leads me to believe this has to do with drive encryption.  I haven't encrypted the drive.  I even tried installing cryptsetup, but I get another message saying to run dpkg --configure -a.

I'm stuck.  Appreciate any thoughts you might have on this one.  Thanks!

---

### Post by TVTrukChik on 2009-06-24
Well, I managed to fix this.  I was at the point where I couldn't install or uninstall any packages, and figured I'd live dangerously since I'd pretty much resigned myself to wiping the drive and starting over.

What I did:  Copied /sbin/dmsetup off my other Ubuntu box that has a relatively fresh install of Jaunty.  It didn't have cryptsetup on it, so I installed that, and copied /sbin/cryptsetup to this machine as well.  Ran dpkg --configure -a, and all was well after that.  I was able to complete the upgrade to Jaunty on this machine and everything seems to be working fine.

---

