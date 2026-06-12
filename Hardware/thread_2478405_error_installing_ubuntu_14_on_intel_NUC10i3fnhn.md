---
title: "error installing ubuntu 14 on intel NUC10i3fnhn"
date: 2022-08-25
forum: Hardware
---

### Post by juanjose3 on 2022-08-25
Hi to everyone.

I've tried to install Ubuntu 14 on a MINIPC Intel NUC NUC10i3FNHN.

The first screes is only in black with a symbol "-" and freezes totally.

Just with Ubuntu 14 occurs this error. 

I've installed Windows 10 and Ubuntu 22 without problem.

Does exist some BIOS config or drivers, config file on the usb installer?

Thanks for the support.

---

### Post by QIII on 2022-08-25
Both 14.04 and 14.10 are very well beyond their end of standard support.  I'm not even sure if there is extended support for them

It is entirely possible that a release that old will simply not work on newer hardware.

It is probably not worth your time to try, and it is almost certainly not worth the community's time to try to help with that.

---

### Post by guiverc on 2022-08-25
Ubuntu release using the *year* format are different to the far more widely used *year.month* format.  ie. Ubuntu 22.04 LTS is the main release of Ubuntu for 2022-April, the *specialist* 22 products were release last month for example Ubuntu Core 22.

Ubuntu *year* products (*snap only*) didn't exist before 2016, ie. Ubuntu Core 16 was the first.

Ubuntu 14.04 LTS does have ESM support, with *paid* support options available. Refer [https://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/](https://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/) but be aware that ESM isn't the same as a *standard support *product.

Many packages are supported only via *snap* in ESM, which isn't a concern if your box is *offline*, but that can require more resources than the original packaging, but for businesses with *legacy* hardware that runs the 2014-April release well & don't have capacity to currently upgrade;  ESM is an available option.

There will be devices where some 14.04 media will *not* boot on, that is expected & why later ISOs were produced with security fixes, but media is still old for hardware that *then* existed when the software stack was packaged.

---

### Post by juanjose3 on 2022-08-29
Thanks for your comments.
I just need install Ubuntu 14 only in one miniPC.
But I'm thinking on change the pc to do this stuff.
Thanks for your time.

---

### Post by juanjose3 on 2022-08-29
Thanks for your comments.

---

### Post by juanjose3 on 2022-08-30
I solved my issue with this MiniPC model. The Bios configuration comes with S3 ENERGY MODERN STANDBY. I just disabled this parameter and changed to S3 LEGACY STANDBY  and disabled SECURE BOOT. This allow me enable LEGACY BOOT and the computer ran Ubuntu 14 whitout problems. 

Thanks for your advices.

[https://community.intel.com/t5/Intel-NUCs/NUC10-can-t-enable-Legacy-Boot/td-p/602288?profile.language=en](https://community.intel.com/t5/Intel-NUCs/NUC10-can-t-enable-Legacy-Boot/td-p/602288?profile.language=en)

---

