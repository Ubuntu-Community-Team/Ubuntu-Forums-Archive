---
title: "Graphics card question, Radeon HD 3450"
date: 2013-02-11
forum: Hardware
---

### Post by HHx66 on 2013-02-11
I recently had a PC failure (my laptop died) and well honestly I cannot afford to build a brand-new rig right now like I really want to, so I sprung for winning some cheap hardware on eBay to hold me over until I have the expendable money in a few months or so to build a brand new system, but anyways:

The system I sprung for comes with a Radeon HD 3450 256MB graphics card (I do very light gaming/emulators and older 1999-2005 games as far as PC games go) but my main question is will this card be supported at all by Ubuntu? Looking to run 12.04 on it when I get it all here.

---

### Post by QIII on 2013-02-11
It will work fine with 12.04 and either the open source Radeon driver or the proprietary ATI driver in the Precise repo.

It will not work with any ATI driver with Ubuntu 12.10 or later.  For that you will have to use the open source driver.

---

### Post by HHx66 on 2013-02-13
So the proprietary drivers are available on 12.04?

---

### Post by Mark Phelps on 2013-02-13
> **HHx66 said:**
> So the proprietary drivers are available on 12.04?

They should be offered through Additional Drivers.  If you install those, when you do updates that affect the kernel, the drives will get updated automatically, as well.

---

### Post by Yellow Pasque on 2013-02-13
> **HHx66 said:**
> So the proprietary drivers are available on 12.04?
Yes, but you'll probably be happier with the open-source drivers. I'm a casual/light gamer myself, and the open-source drivers have served me well for the past few years (RadeonHD 4350).

---

