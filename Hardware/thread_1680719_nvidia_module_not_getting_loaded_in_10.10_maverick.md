---
title: "nvidia module not getting loaded in 10.10 maverick"
date: 2011-02-03
forum: Hardware
---

### Post by Mark Rose on 2011-02-03
I'm trying to use the binary nvidia driver to get 3D goodness.

Nouveau works fine, picks up both monitors, etc. If I remove the nouveau drivers, it falls back to the nv driver. I can't get it to pick up the nvidia driver.

uname -a:
Linux uberbox 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

lspci | grep VGA:
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)


Looking at the attached nvidia-bug-report.log.gz file, shows this:

[    49.695] (==) Matched nouveau as autoconfigured driver 0
[    49.695] (==) Matched nv as autoconfigured driver 1
[    49.695] (==) Matched vesa as autoconfigured driver 2
[    49.695] (==) Matched fbdev as autoconfigured driver 3
[    49.695] (==) Assigned the driver to the xf86ConfigLayout
[    49.695] (II) LoadModule: "nouveau"
[    49.696] (WW) Warning, couldn't open module nouveau
[    49.696] (II) UnloadModule: "nouveau"
[    49.696] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    49.696] (II) LoadModule: "nv"

So it's not even picking up the nvidia driver, even though it's in /usr/lib/xorg/modules/drivers, and the card is supported.

Help?

---

### Post by Mark Rose on 2011-02-03
Bump.


Is there another place I should ask for help?

I'd really like to fix this, as Nouveau frequently freezes, and nv doesn't support multiple monitors.

---

### Post by Mark Rose on 2011-02-03
Cross-posted on [NVIDIA Forums](http://forums.nvidia.com/index.php?showtopic=192421).

---

### Post by owenlinx on 2011-03-15
I have the exact same problem. 
```
$lsmod
Module                  Size  Used by
nouveau               568848  0 
ttm                    68212  1 nouveau
drm_kms_helper         32836  1 nouveau
drm                   206161  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6208  1 nouveau

```

I have tried x-swat ppa, installing from nvidia, Option "UseDisplayDevice" "DFP" & CRT (i am on vga). and disabling KMS. 

I am at a loss.

Thanks,
Justin

---

### Post by owenlinx on 2011-03-20
I solved my issue. 

```
sudo nano /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT="noacpi acpi=off"
GRUB_CMDLINE_LINUX="noacpi acpi=off"

```

[Nvidia breaks acpi]("http://www.google.com/search?aq=f&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=nvidia+acpi")

Hope this helps somebody.

---

