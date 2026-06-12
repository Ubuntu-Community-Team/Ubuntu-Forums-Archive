---
title: "nouveau supports RTX 3050 ?"
date: 2024-01-21
forum: Hardware
---

### Post by johnmne on 2024-01-21
Does "nouveau" driver supports Nvidia's RTX 3050 in Ubuntu 22.04 ?

Per my understanding, the driver should support RTX 3050, but prefer to verify with you.

---

### Post by Autodave on 2024-01-22
It will allow the 3050 to operate, but you really need to update to the newer driver....either 525 or 535.

---

### Post by johnmne on 2024-01-23
> **Autodave said:**
> It will allow the 3050 to operate, but you really need to update to the newer driver....either 525 or 535.

Why do I need 525 or 535?
525 or 535 is Nvidia's proprietary driver, no..?

I'm only looking for basic functionality of the GPU to browser the internet and see movies.
And maybe DisplayPort MST (daisy chaining monitors)

---

### Post by MAFoElffen on 2024-01-24
@AutoDave misunderstood you... 525 & 535 would refer to the nvidia driver, not the opensource Nouveau driver...

RE: [https://nouveau.freedesktop.org/FeatureMatrix.html](https://nouveau.freedesktop.org/FeatureMatrix.html)

The driver itself is going to depend on the kernel version...

Nvidia NV176 (GA106) is GeForce RTX (3050, 3060)...
NVidia NV177 (GA107) is GeForce RTX 3050...

To find if your RTX 3050 is GA106 or GA107, do this
```

sudo lspci -nnnk | grep -A3 -E 'Display|VGA|3D'

```

---

### Post by johnmne on 2024-01-24
> **MAFoElffen said:**
> @AutoDave misunderstood you... 525 & 535 would refer to the nvidia driver, not the opensource Nouveau driver...

RE: [https://nouveau.freedesktop.org/FeatureMatrix.html](https://nouveau.freedesktop.org/FeatureMatrix.html)

The driver itself is going to depend on the kernel version...

Nvidia NV176 (GA106) is GeForce RTX (3050, 3060)...
NVidia NV177 (GA107) is GeForce RTX 3050...

To find if your RTX 3050 is GA106 or GA107, do this
```

sudo lspci -nnnk | grep -A3 -E 'Display|VGA|3D'

```

The [URL]("https://nouveau.freedesktop.org/FeatureMatrix.html") provided in your post display a webpage with a table.
That table shows the feature support for every GPU according to its codename.

The GPU RTX 3050 has codename "NV177".
According to the table, the corresponding column "NV170" has the following 2D features marked as "TODO" (meaning, the code to support the feature needs to be written):

[LIST]
[*]basic 2D (EXA)
[*]fast 2D (XRender)
[*]play videos (Xv[SUP]2[/SUP])
[*]video decoding accel
(VDPAU/XvMC)
[/LIST]

These seems like basic features which are required for basic GPU usage.
So, RTX 3050 **isn't** supported yet by the nouveau driver.

Additionally, that table shows that **older** GPU aren't supported yet:
[LIST]
[*]NV160 (e.g. RTX 2070, RTX 2060, GTX 1660, GTX 1650)
[*]NV140 (e.g. Titan V)
[/LIST]

So there's lot of missing support in the nouveau driver for even older GPUs.


However, there seems to be a decent support for NV130 which includes:
[LIST]
[*]GTX 1080
[*]GTX 1070
[*]GTX 1060
[*]GTX 1050
[*]GT 1030
[/LIST]

So I can use the nouveau driver with GT 1030 or GTX 1050 or GTX 1060 for the following usage:
[LIST]
[*]Browsing the web.
[*]Playing videos.
[*]DisplayPort MST (which is daisy chaining monitors).
[/LIST]


Verifying with you  - everything that I wrote above is correct?

Thank you.

---

### Post by MAFoElffen on 2024-01-24
Yes...

basic 2D (EXA), fast 2D (XRender), play videos (Xv2), video decoding accel, (VDPAU/XvMC) don't work yet for RTX 3050. I alos heard when the support first came out for it as opensource, that the benchmarks were pretty slow.

But on passthrough, which is what you want to do, you could always use one of the NVidia drivers for it, and it would be the same. So you do have options open, just not the same and how you want to do it.

---

### Post by Yellow Pasque on 2024-01-24
> **MAFoElffen said:**
> basic 2D (EXA), fast 2D (XRender), play videos (Xv2), video decoding accel...

Xv isn't widely used anymore. And as the footnote says, 2D accel can be done with the X modesetting/"GLAMOR" driver. The one that hurts is no VDPAU support.

---

### Post by johnnyd716 on 2024-08-11
I had terrible problems during boots with my computer because of the Nouveau driver (my computer has both Intel GPU and Nvidia 3050 Ti Mobile GPUs), combined with the fact that I'm using ecrypted root partition (that includes the boot directory). The complete solution was to blacklist the nouveau driver from loading, in /etc/modprobe.d, (so I'm not using nouveau anymore), and I also to add the kernel parameter "nouveau.modeset=0" in Grub, because nouveau was being loaded anyway during boot phase in Linux kernels 6.9 and above. I haven't heard or read of anyone else having the same problem as me, no matter how much I searched on the web.

---

