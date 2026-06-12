---
title: "Pinning packages not working"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by slakkie on 2009-04-14
Hello all,

I'm currently pinning my kernel version (updating kernels only when upgrading to a new release). And something is not going as expected on one of my boxes:

```

$ cat /etc/apt/preferences
Package: linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic linux-server linux-image-server
Pin: version 2.6.24.19.21
Pin-Priority: 1001

```

The incorrect upgrade.. 

```

aptitude -s safe-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  amarok-xine k3b
The following packages have been kept back:
  amarok
The following packages will be upgraded:
  libkrb53 libpq5 linux-headers-2.6.24-23 linux-headers-2.6.24-23-generic linux-image-2.6.24-23-generic linux-libc-dev tzdata
7 packages upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Need to get 29.3MB of archives. After unpacking 4096B will be used.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.

```

As you can see, it wants to upgrade packages I do not want to upgrade.. I can change it in the preferences file, not to install these packages, but I have a similar preferences file on other Ubuntu (and Debian machines) and on these boxes I do not have the issue of upgrading packages which are normally pinned. Does anyone know how to tackle this problem?

Somehow I've upgraded the kernel to:

Linux eniac 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

How is this possible when I've pinned a package? Why do I upgrade when I've instructed not to upgrade to a certain package?

I thought it was related to an upgrade to 8.04.2 but my other box still runs the correct kernel and it also 8.04.2. The really fun thing is that all my previous kernels are missing from /boot, so I cannot load the previous kernel :(

---

### Post by slakkie on 2009-04-15
No one?

---

### Post by Chame_Wizard on 2009-04-16
check in the grub list.

---

### Post by slakkie on 2009-04-17
> **Chame_Wizard said:**
> check in the grub list.

Grub only mentions my new kernel, which is weird, but confirms the upgrade.

---

