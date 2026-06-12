---
title: "AMD Legacy Drivers"
date: 2013-10-08
forum: Hardware
---

### Post by Johnathan_Smith on 2013-10-08
So I just want to make sure that what i've found in my research is that the Radeon 3200 graphics card is now packaged in a Legacy Drivers bundle that is no longer updated. I am somehwat new to Ubuntu and am trying to resolve the issue that I see in my dysplay driver settings that say "unknown" and am using a "standard experience".

Thanks.

---

### Post by Mark Phelps on 2013-10-08
If you have a Radeon HD 32xx card, you can not install the AMD drivers in any Ubuntu newer than 12.04.1 -- because, starting with 12.04.2, Ubuntu updated the X-server to a new version that is incompatible with the AMD 2x/3x/4x-series driver.

So, unless you're running an older version of Ubuntu, you can't install the Legacy drivers.

---

### Post by Yellow Pasque on 2013-10-08
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

---

