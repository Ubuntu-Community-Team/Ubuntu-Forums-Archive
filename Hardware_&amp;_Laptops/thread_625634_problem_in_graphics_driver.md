---
title: "problem in graphics driver"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by vip090 on 2007-11-28
hi 

I recently installed Ubuntu 7.10 in my Acer Laptop 

but I have a problem in the Graphics Driver

my VGA is Intel 82852/855GM

i tried to install the related driver from Intel's website but when install it's gave me a message said :

  "The DRI drivers cannot be installed without the latest kernel modules"

can any one help me ??!!

---

### Post by Sef on 2007-11-28
> "The DRI drivers cannot be installed without the latest kernel modules"

What kernel modules does it need?  It should be on their website.

---

### Post by vip090 on 2007-11-28
> **Sef said:**
> What kernel modules does it need?  It should be on their website.

I download it from here

[http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=922&DwnldID=8203&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=922&DwnldID=8203&lang=eng)


it said :

 required Linux* kernel modules (AGP GART and DRM) 


What to do ?

---

### Post by PmDematagoda on 2007-11-28
Is this the driver you are looking for:-

> X.Org X server -- Intel i8xx, i9xx display driver 
This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
and i965 series chips.

This package also provides an XvMC (XVideo Motion Compensation) driver
for the same chipsets.

More information about X.Org can be found at:
<URL:http://www.X.org>
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

This package is built from the X.org xf86-video-intel driver module.

---

### Post by vip090 on 2007-11-28
> **PmDematagoda said:**
> Is this the driver you are looking for:-

Excuse me  :
how to install this driver?

---

### Post by PmDematagoda on 2007-11-28
The package is known as xserver-xorg-video-intel and should be installed simply by using:-
```

sudo apt-get install xserver-xorg-video-intel
```

---

### Post by vip090 on 2007-11-28
> **PmDematagoda said:**
> The package is known as xserver-xorg-video-intel and should be installed simply by using:-
```

sudo apt-get install xserver-xorg-video-intel
```


thank you for Responsing

i will try to install it

---

### Post by vip090 on 2007-11-28
> **PmDematagoda said:**
> The package is known as xserver-xorg-video-intel and should be installed simply by using:-
```

sudo apt-get install xserver-xorg-video-intel
```


not the right driver :(

---

