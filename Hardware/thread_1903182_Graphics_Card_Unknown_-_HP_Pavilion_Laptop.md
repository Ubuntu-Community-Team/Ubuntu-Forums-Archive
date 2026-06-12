---
title: "Graphics Card: Unknown - HP Pavilion Laptop"
date: 2012-01-01
forum: Hardware
---

### Post by iDoiStuff on 2012-01-01
System Settings> Additional Drivers doesn't show anything. I have an HP Pavilion DV2 laptop with an ati x1200 series graphics.

[http://i.imgur.com/hZCiq.png](http://imgur.com/hZCiq)

---

### Post by MoreOrLess on 2012-01-01
This a known/common issue with the system info program. You can ignore it (and mark this thread solved).

---

### Post by iDoiStuff on 2012-01-01
> **MoreOrLess said:**
> This a known/common issue with the system info program. You can ignore it (and mark this thread solved).

The laptop doesn't run good, when I move windows it stutters a lot. I know the graphics card driver isn't installed.

How can I check if the graphics driver is installed?

---

### Post by MoreOrLess on 2012-01-02
The x1200 uses the open-source ati driver, which is installed/used by default.

---

### Post by Mark Phelps on 2012-01-02
> **iDoiStuff said:**
> How can I check if the graphics driver is installed?

If you're seeing a desktop, not forced into using the Command Line Interface, then you already HAVE graphics drivers installed.

AMD/ATI dropped Linux driver support for your card years ago.

The existing drivers, the ones already installed, are the only ones that will work now in Linux distros.

---

### Post by iDoiStuff on 2012-01-02
> **Mark Phelps said:**
> If you're seeing a desktop, not forced into using the Command Line Interface, then you already HAVE graphics drivers installed.

AMD/ATI dropped Linux driver support for your card years ago.

The existing drivers, the ones already installed, are the only ones that will work now in Linux distros.

How come Ubuntu shows "unknown" and runs like utter crap, while other distros like Fedora run smooth and say more than "unknown"

---

### Post by Mark Phelps on 2012-01-02
> **iDoiStuff said:**
> How come Ubuntu shows "unknown" and runs like utter crap, while other distros like Fedora run smooth and say more than "unknown"

Possibly because any Linux distro is a combination of a Linux kernel and OTHER software.  Obviously, the stuff that's included in Fedora does a better job of handling "legacy" ATI cards than the stuff included with Ubuntu.

---

### Post by MoreOrLess on 2012-01-02
> **iDoiStuff said:**
> How come Ubuntu shows "unknown" and runs like utter crap, while other distros like Fedora run smooth and say more than "unknown"
Fedora tends to have more up-to-date mesa 3D code. You can get a fresh graphics stack in Ubuntu by using the xorg-edgers PPA.

---

