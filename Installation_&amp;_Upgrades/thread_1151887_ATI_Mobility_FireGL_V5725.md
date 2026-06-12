---
title: "ATI Mobility FireGL V5725"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by xender69 on 2009-05-07
Hi,

Just installed ubuntu 9.04 on hp elitebook 8730w with ATI Mobility FireGL V5725.  I was trying to enable the Extras in the Visual Effects so I can use AWN and I see that there is ATI/AMD proprietary FGLRX graphics drivers that the system recognizes but AFTER activating this driver and rebooting the system my screen just goes completely blank and I am not able to do anything.

Has anyone been able to work around this ?

Tks in advance.

---

### Post by wsando on 2009-05-07
I have experienced the same thing.  I have tried to use the ATI drivers for linux with the same result of blank screen.

---

### Post by sharpone on 2009-05-23
I own this laptop, and had the same issue. Boot into rescue mode and run the following as root. This fixed the issue for me.

```
aticonfig --acpi-services=off
```I did this with the 9.5 fglrx drivers, but it should work with the drivers in ubuntu's repositories. After you get it running, you may find that resizing/maximizing windows is very slow (1-3 seconds). I installed a replacement xorg-server as talked about in this thread [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all) and it fixed that issue for me.

Hope that helps.

---

### Post by xender69 on 2009-06-09
> **sharpone said:**
> I own this laptop, and had the same issue. Boot into rescue mode and run the following as root. This fixed the issue for me.

```
aticonfig --acpi-services=off
```I did this with the 9.5 fglrx drivers, but it should work with the drivers in ubuntu's repositories. After you get it running, you may find that resizing/maximizing windows is very slow (1-3 seconds). I installed a replacement xorg-server as talked about in this thread [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all) and it fixed that issue for me.

Hope that helps.

Do you think this would also work for fedora 11 ?

---

### Post by MoarBewbs on 2009-12-12
I have a laptop (hp elitebook 8730w) with the same graphics card on ubuntu 9.10. 
I'd like to use compiz but therefore I have to enable the proprietary ATI drivers, which gives me the exact same problem as xender69. I tried the rescue mode thing but it didn't work.
So now I've reinstalled ubuntu and am trying to get compiz to work again.
Is there anything else I can try to fix this?

Also, before trying to enable the proprietary again I'd like to make some system restore point to revert to in case I get a blank screen again and can't fix it (I'd hate to have to reinstall again -.-' ) 
How is this done on ubuntu? (It has to be possible to revert to the system restore from recovery mode) Is this possible?

Thanks in advance!

---

