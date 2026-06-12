---
title: "Kernel atkbd.c modification: Samsung X360"
date: 2011-03-27
forum: Hardware
---

### Post by cavilling_elite on 2011-03-27
Hello, I've had a Samsung x360 for a number of years, and since 10.04 I've had to recompile a kernel due to the Fn keys not releasing for the backlight.

There is a bug for Samsung Nxxx models ([Bug #295251]("https://bugs.launchpad.net/bugs/295251")) 

Add @ line 1656-ish
```

    {
        /* Samsung X360 */
        .matches = {
            DMI_MATCH(DMI_SYS_VENDOR, "SAMSUNG ELECTRONICS CO., LTD."),
            DMI_MATCH(DMI_PRODUCT_NAME, "X360"),
        },
        .callback = atkbd_setup_forced_release,
        .driver_data = atkbd_samsung_forced_release_keys,
    },



```[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/399911](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/399911)

It also would be nice to add the easy-slow-down-manager to the additional drivers manager.

[http://code.google.com/p/easy-slow-down-manager/](http://code.google.com/p/easy-slow-down-manager/)

---

### Post by cavilling_elite on 2011-03-29
I have submitted a patch to the 2.6.35 ubuntu kernel to fix this problem. 

[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/745094](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/745094)

How can one go about adding easy-slow-down-manage to the "Additional Drivers" in ubuntu being a default?

I would assume by looking at the other bug reports on Samsungs, that all newer Nxxx or even the new Series 9 are affected.

---

