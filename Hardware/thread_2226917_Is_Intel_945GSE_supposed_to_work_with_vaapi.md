---
title: "Is Intel 945GSE supposed to work with vaapi?"
date: 2014-05-29
forum: Hardware
---

### Post by monkeybrain20122 on 2014-05-29
Hi, this is the card

```
0:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

I have installed the i965 driver, but
```
vainfo
libva info: VA-API version 0.35.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/i386-linux-gnu/dri/i915_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

I know it is an old hard but I think some kind of hardware decoding may work.

Thanks.

---

### Post by tgalati4 on 2014-05-30
So even though you installed the i965 driver, libva is trying to use the i915 direct rendering module--maybe they share the same code, but it is unlikely you will have success using a different video driver.  Perhaps you don't have enough video RAM allocated--check your video shared RAM settings in BIOS.  Set it to maximum and try again.

---

### Post by monkeybrain20122 on 2014-05-30
Thanks for the reply, but there is no shared RAM setting in the BIOS.

---

### Post by Yellow Pasque on 2014-05-31
> **monkeybrain20122 said:**
> Thanks for the reply, but there is no shared RAM setting in the BIOS.

RAM allocation is done dynamically: [https://en.wikipedia.org/wiki/Dynamic_video_memory_technology](https://en.wikipedia.org/wiki/Dynamic_video_memory_technology)

As for VA-API, "You need an X4500 (i.e. GL40 chipset or better)" Hey, that's the second time today I answered that question ;)

---

### Post by monkeybrain20122 on 2014-05-31
> **Temüjin said:**
> RAM allocation is done dynamically: [https://en.wikipedia.org/wiki/Dynamic_video_memory_technology](https://en.wikipedia.org/wiki/Dynamic_video_memory_technology)

As for VA-API, "You need an X4500 (i.e. GL40 chipset or better)" Hey, that's the second time today I answered that question ;)

Hi, so how do I know if it is GL40 or better?

---

### Post by Yellow Pasque on 2014-05-31
It's not. 945 is older than 965: [https://en.wikipedia.org/wiki/List_of_Intel_chipsets#Core_2_mobile_chipsets](https://en.wikipedia.org/wiki/List_of_Intel_chipsets#Core_2_mobile_chipsets)

---

