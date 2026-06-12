---
title: "AMD R7 360 - ubuntu 16.0.4 - no proprietory driver ?"
date: 2018-07-13
forum: Hardware
---

### Post by verenard on 2018-07-13
I looked through the list on the AMD website and didn't see anything for R7 360. It has R7 350, R7 260 -- but no 360.
What are my options for this card, pray tell ?

---

### Post by Yellow Pasque on 2018-07-13
Why do you think you need the proprietary driver? Most people are better off using the default open source driver nowadays.

---

### Post by verenard on 2018-07-13
Which open source driver - there are two now aren't there ? Radeon and AMDGPU ?
I get a funny picture in ubuntu, the card is fine in windows.

---

### Post by Yellow Pasque on 2018-07-13
> I get a funny picture in ubuntu

Is the resolution incorrect? Does this occur with a LiveUSB of Ubuntu 18.04?

---

### Post by QIII on 2018-07-14
During installation, the Ubuntu installer will chose the appropriate open source driver:  AMDGPU or Radeon.  You don't need to worry abou that, unless you are bent on installing AMDGPU-PRO, which you may not be able to do with your hardware in any case.

Anyway ... I agree that we need to know what "funny" means.

---

### Post by verenard on 2018-07-16
> **Temüjin said:**
> Is the resolution incorrect? Does this occur with a LiveUSB of Ubuntu 18.04?

Yeah I'm going to try a newer ubuntu, but aren't the drivers the same ?

---

### Post by Yellow Pasque on 2018-07-16
> **verenard said:**
> Yeah I'm going to try a newer ubuntu, but aren't the drivers the same ?

Ubuntu 18.04 will use the same radeon kernel module/driver, but it contains updated versions of kernel/X/mesa, etc.
Bugs do get fixed.

---

### Post by verenard on 2018-07-16
> **Temüjin said:**
> Ubuntu 18.04 will use the same radeon kernel module/driver, but it contains updated versions of kernel/X/mesa, etc.
Bugs do get fixed.

Well, I made a live USB of 18.04 and it looks great, so thanks for the support and I consider this solved.

---

### Post by mörgæs on 2018-07-16
Good, then please mark the thread so.

---

