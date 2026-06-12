---
title: "ATI Driver Problem"
date: 2010-01-05
forum: Hardware
---

### Post by Face_Man on 2010-01-05
Hello all,

i have acer aspire 5910  and i am trying to install the right driver for "Mobility Radeon X2100". is there a driver for it ?

Any help would be much appreciated.
ubuntu 9.10  amd64

---

### Post by jschall1 on 2010-01-05
> **Face_Man said:**
> Hello all,

i have acer aspire 5910  and i am trying to install the right driver for "Mobility Radeon X2100". is there a driver for it ?

Any help would be much appreciated.
ubuntu 9.10  amd64

I believe it should be using the open-source Radeon driver by default, which is what you want.

---

### Post by clevertomato on 2010-01-05
I don't have experience with your particular ATI GPU, but I can point you in some directions.

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) to learn about the open source RadeonHD drivers

Go to System/Administration/Hardware Drivers if you want a very simple way of installing the non open source proprietary drivers from ATI. These provide 3D and bells and whistles, but are not open source. If you're new and/or want a very simple solution to try first, I'd recommend this before anything else. If you want to activate, simply choose activate on the "Hardware Drivers" dialog window and it should take care of the rest for you.

---

### Post by Face_Man on 2010-01-05
> **jschall1 said:**
> I believe it should be using the open-source Radeon driver by default, which is what you want.

yah but when i try to configer external monitor i dont have much option like  TwinView or Sparate X screen

---

### Post by clevertomato on 2010-01-05
You may have to use the ATI proprietary drivers ("Hardware Drivers" under System/Administration).

For a good explanation of the different drivers available for ATI GPUs and how to get & install them, see:

[http://humphreybc.wordpress.com/2009/11/27/understanding-ati-linux-drivers/](http://humphreybc.wordpress.com/2009/11/27/understanding-ati-linux-drivers/)

---

### Post by darkksyde on 2010-01-06
i believe legacy ati cards have the drivers already installed

---

