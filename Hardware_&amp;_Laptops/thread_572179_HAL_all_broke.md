---
title: "HAL all broke"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by stuartguthrie on 2007-10-10
I was running out of disk space and after deleting some /var contents I seem to a have broken some of HAL. I used to be able to load my E61 as a hard drive and copy files to it. Now it fails to mount. 

Oct 10 20:26:29 poloniousLaptop NetworkManager: <debug info>^I[1192011989.615422
] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/dev
ices/volume_part_1_size_2041974784').

I get the above in my daemon.log so it's seeing something. Does anyone know what I need to do?

---

