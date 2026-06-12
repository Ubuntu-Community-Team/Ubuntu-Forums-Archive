---
title: "DEB drivers versus kernel upgrades"
date: 2008-08-04
forum: General Help
---

### Post by NTolerance on 2008-08-04
The current Hardy kernel has a [bug](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212497) that causes my onboard NIC not to work.  Some info about my system:

```
lspci | grep Eth
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

```
uname -r
2.6.24-19-generic
```

At the end of the launchpad report that I linked to is a fixed driver in a DEB file.  I installed this new driver and it makes my NIC work fine.  But I'm concerned about kernel updates that eventually will show up in update-manager.  Will these updates break my ethernet?  I want to be clear that I didn't add anything new to my sources.list file, I merely installed the fixed DEB file.  Thanks.

---

### Post by ModelM on 2008-08-04
It depends on how the package is built. I had a PCI modem once that had a driver built against the kernel version & installed, all from a .deb package.

At the next kernel update, I rebooted & expected to have to fuss with the modem to get it to work with the new kernel.

Instead, during the boot process messages I saw something similar to:

```
Loading hardware drivers
modem driver: oops, I see there's a new kernel!
modem driver: just a moment while I rebuild & install
.......
modem driver: your modem is ready!

```

The process was all automatic & took about 30 seconds.

So at least some packages can be built which will check for this.

---

