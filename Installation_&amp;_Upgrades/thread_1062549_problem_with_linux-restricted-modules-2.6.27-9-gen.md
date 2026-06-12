---
title: "problem with linux-restricted-modules-2.6.27-9-generic"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by starling on 2009-02-07
I've been having troubles with various packages not configuring properly after install after upgrading to 8.10. Generally I've just removed them using dpkg -r, but in this case that doesn't work.

```
starling@starling-desktop:~$ sudo dpkg --remove linux-restricted-modules-2.6.27-9-generic
(Reading database ... 131575 files and directories currently installed.)
Removing linux-restricted-modules-2.6.27-9-generic ...
rmdir: failed to remove `/lib/modules/2.6.27-9-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.27-9-generic': No such file or directory
/usr/sbin/update-initramfs: 547: awk: not found
dpkg: error processing linux-restricted-modules-2.6.27-9-generic (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 linux-restricted-modules-2.6.27-9-generic

```

apt won't uninstall it, and dpkg --configure -a doesn't think there is a problem. What's going on?

---

### Post by tommcd on 2009-02-07
Try running:
```

sudo dpkg --configure -a
sudo apt-get update

```
This should fix any broken packages you may have.

---

### Post by starling on 2009-02-07
> **tommcd said:**
> Try running:
```

sudo dpkg --configure -a
sudo apt-get update

```
This should fix any broken packages you may have.

Nope. Both work, but the package is still marked as broken and apt wants to, but can't remove it. I have a suspicion that it is not actually installed.

---

### Post by tommcd on 2009-02-08
Another thing to try is:
```
sudo apt-get install -f
```
to try to fix broken packages.

---

### Post by theOtherMarino on 2009-05-21
Hello,

Others like me are stuck with this kind of problem (a broken package that neither dpkg nor apt-get can remove).
See [http://ubuntuforums.org/showthread.php?t=1147434&page=2](http://ubuntuforums.org/showthread.php?t=1147434&page=2)

If you found a solution, please post it in the thread. That would help.

Thanks in advance,

Marino

---

