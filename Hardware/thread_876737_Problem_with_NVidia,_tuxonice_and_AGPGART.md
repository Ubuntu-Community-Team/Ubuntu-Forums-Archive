---
title: "Problem with NVidia, tuxonice and AGPGART"
date: 2008-08-01
forum: Hardware
---

### Post by DexterLB on 2008-08-01
Yesterday I patched my kernel to work with tuxonice (suspend2). And I found out that it is incompatible with AGPGART. So I need to disable the AGPGART kernel module

My question: How the hell do I do that???  How Can I disable AGPGART kernel module?

P.S. /proc/driver/nvidia/agp/status:
```
Status: 	 Enabled
Driver: 	 AGPGART
AGP Rate: 	 4x
Fast Writes: 	 Disabled
SBA: 		 Disabled

```

---

### Post by sempronius on 2008-08-27
> **DexterLB said:**
> Yesterday I patched my kernel to work with tuxonice (suspend2). And I found out that it is incompatible with AGPGART. So I need to disable the AGPGART kernel module

My question: How the hell do I do that???  How Can I disable AGPGART kernel module?

P.S. /proc/driver/nvidia/agp/status:
```
Status: 	 Enabled
Driver: 	 AGPGART
AGP Rate: 	 4x
Fast Writes: 	 Disabled
SBA: 		 Disabled

```


You appear to misunderstand something:

Not AGPGART is the problem with nvidia drivers/suspend to disk, but the agpgart *BACKEND* (e.g. sis_agp, intel_agp etc.).

AGPGART (with the more recent nvidia drivers, also with legacy drivers) ALWAYS needs to be there (by always I mean:
whether you use either nvidia agp OR kernel agp). What you need to unload/not load when using nvidia agp OR when disabling agp is the agpgart ***backend*** (see above: sis_agp or something with a similar name, look through lsmod...).

So you could try using nvagp "1" thus using nvidia agp instead of kernel agp - provided that your AGP chipset is supported by nvidia!

If you use nvgap "1" you may get this message:

NVRM: not using NVAGP, an AGPGART backend is loaded!

This means that nvidia agp was requested by you (setting nvagp 1) but could not be used because of either
a) loading an agpgart backend module (like sis_agp etc.) which prevents nvidia agp
OR
b) in spite of not loading a backend nvidia agp did not work because your chipset is not supported by nvidia agp

In either case AGP is not active.


In my case nvagp "1" gives me the above message because my chipset - unfortunately - is not being supported! (AGP chipset: SIS 741). Setting nvagp to "1" is pointless here, it is just like setting it to "0". -> no AGP used.

I can only use kernel agp (via the agpgart backend sis_agp) by setting NvAGP "2".

But this doesn't harmonize with suspend to disk/hibernation.

That's why I have to disable AGP.
With deactivated AGP hibernation works perfect for me and both hibernating and resuming is very fast!
The performance degradation by deactivating AGP is not even that dramatic for me (with a Geforce 3 TI 200), only a comparatively small loss of fps in glxgears/older games.


Hope, I didn't increase the confusion. :-)

sempronius

---

### Post by DexterLB on 2008-09-04
Thanks a lot. That works!

---

