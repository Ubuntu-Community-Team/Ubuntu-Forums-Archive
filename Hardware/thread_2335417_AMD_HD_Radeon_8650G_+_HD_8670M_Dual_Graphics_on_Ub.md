---
title: "AMD HD Radeon 8650G + HD 8670M Dual Graphics on Ubuntu 16.04 LTS"
date: 2016-08-28
forum: Hardware
---

### Post by thewire2 on 2016-08-28
I'm currently a Windows 10 user, but would like to install Ubuntu alongside Windows. According to this, the AMD 8670M (Oland) driver is supported by the open source graphics driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I'm wondering if the 8650G (Richland) driver is supported as well? Also, would there be any problems with a dual graphics setup in Ubuntu 16.04?

---

### Post by Mark Phelps on 2016-08-29
I don't know about this pair specifically, but in general, dual-graphics does not work on Linux without a huge amount of extra work -- and you are severely hampered by the fact that the AMD fglrx drivers simply do not work in Ubuntu 16.04.  That uses a new kernel version and AMD is not going to update their fglrx drivers to work with that version.  They are working on a new open-source driver but it is still in progress and only works with a handful of very new AMD video chipsets.  For more info on this, do a search on AMDGPU.

---

