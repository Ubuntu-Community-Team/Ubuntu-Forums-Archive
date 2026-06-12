---
title: "Driver for AMD Radeon Graphic Card"
date: 2017-09-25
forum: Hardware
---

### Post by Nayab Basha Sayed on 2017-09-25
Hi there,

I am having hard time finding driver for my AMD Radeon graphic card. Anybody provide the link or instructions to install driver for my GPU please...
Here is my driver GPU

```
me@linux:~$ lspci | grep Display
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun LE [Radeon HD 8550M / R5 M230]



```

---

### Post by deadflowr on 2017-09-25
On Ubuntu 16.04 and newer you can only use the open-source radeon or amdgpu already provided drivers.
(AMD has abandoned the closed-source fglrx drivers for any system running linux 3.19 and xserver  1.17 or newer, which 16.04 and newer use)

To install the legacy fglrx drivers you can only do so on Ubuntu 14.04.1.
From here [http://old-releases.ubuntu.com/releases/14.04.1/]("http://old-releases.ubuntu.com/releases/14.04.1/")

---

### Post by Nayab Basha Sayed on 2017-09-25
> **deadflowr said:**
> 
To install the legacy fglrx drivers you can only do so on Ubuntu 14.04.1.
From here [http://old-releases.ubuntu.com/releases/14.04.1/](http://old-releases.ubuntu.com/releases/14.04.1/)

I don't have any problem installing open source drivers. Would you please provide the link or instructions to install it?

---

### Post by QIII on 2017-09-25
If you are getting output to your screen, you have either the Radeon driver or AMDGPU running (both are open source).  Ibuntu will use whichever is appropriate for you hardware on onstall.

---

### Post by deadflowr on 2017-09-25
> **Nayab Basha Sayed said:**
> I don't have any problem installing open source drivers. Would you please provide the link or instructions to install it?

> **QIII said:**
> If you are getting output to your screen, you have either the Radeon driver or AMDGPU running (both are open source).  Ibuntu will use whichever is appropriate for you hardware on onstall.

This
Already installed.
(or would be installed for the Ubuntu Desktop installation, Server installations do not install graphical interfaces by default, so no need for drivers for those)

---

