---
title: "Upgrade problems, dpkg --configure -a fails"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by washakie on 2009-07-07
Hello,

I was trying to upgrade some packages to karmic releases... in the end, I ended up doing a complete dist-upgrade to karmic. It seems too unstable at the moment (or at least never completely installed due to interruption). I am having many problems now, not the least of which is that apt-get / aptitude is broken. I run:
```
sudo dpkg --configure -a
```

But I keep getting:

```
jfb@niflino:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu33) ...
update-initramfs: deferring update (trigger activated)

dpkg: error processing cups (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of foo2zjs:
 foo2zjs depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing foo2zjs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-driver-gutenprint:
 cups-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.
dpkg: error processing cups-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on cups; however:
  Package cups is not configured yet.
 ubuntu-desktop depends on cups-driver-gutenprint; however:
  Package cups-driver-gutenprint is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ghostscript-cups:
 ghostscript-cups depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing ghostscript-cups (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
cpio: ./lib/udev/vol_id: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-13-generic
dpkg: subprocess post-installation script returned error exit status 1
jfb@niflino:~$

```

Any help greatly appreciated. BTW/ I have tried all variants of apt-get autoclean, update, clean, upgrade, etc...

Also, I have played around a little with different sources.list, nothing seems to help. Is there just a way to 'reset' apt?

-john

---

### Post by washakie on 2009-07-07
Seem I found the workaroun:

Not sure what the troubles were, but eventually I was able to solve the problem by removing any reference to cups from:

/etc/init.d/
/etc/rc2.d/
/var/cache/apt/archives/

also, it seems running aptitude just directly works quite well, though it is a little hard to get used to initially. Just type:

sudo aptitude -u

And you'll get into the textual interface to the program.

---

