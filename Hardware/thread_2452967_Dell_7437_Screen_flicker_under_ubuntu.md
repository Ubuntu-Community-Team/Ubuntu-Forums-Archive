---
title: "Dell 7437 Screen flicker under ubuntu"
date: 2020-10-31
forum: Hardware
---

### Post by sultanofswing on 2020-10-31
hello,

recently i've update my dell 7437 (i5 4th gen, i915) with an ips fhd screen (previously i had an hd panel). Under ubuntu studio 20.04, the screen flicker at random frequencies (from 1 to 6 seconds): this causes the screen to go black randomy for some seconds. I tried to use different kernel parameters such as:

```
i915.enable_dpcd_backlight=1
```

but unfortunately, this has no effect.

This is the output of ```
lsmod | egrep 'i915'
```

```
i915                 1990656  0
drm_kms_helper        184320  1 i915
i2c_algo_bit           16384  1 i915
drm                   487424  2 drm_kms_helper,i915
video                  49152  3 dell_wmi,dell_laptop,i915
```

eventually varying the parameters' values, but no chance. This is the result of ```
lshw -video
```

  ```
*-display NON-RÉCLAMÉ ("UNCLAIMED")
       description: VGA compatible controller
       produit: Haswell-ULT Integrated Graphics Controller
       fabricant: Intel Corporation
       identifiant matériel: 2
       information bus: pci@0000:00:02.0
       version: 0b
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: msi pm vga_controller bus_master cap_list
       configuration : latency=0
       ressources : mémoire:f0000000-f03fffff mémoire:e0000000-efffffff portE/S:3000(taille=64) mémoire:c0000-dffff
```


this is the output of ```
lspci | grep VGA
```

```
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
```


the only working combination is "```
i915.enable_dpcd_backlight=1 i915.modeset=0 acpi_backlight=vendor
```" as kernel option. However, in his case I have no flicker BUT the brightness controls have no effect. Using the other options for acpi_backlight (intel, legacy, etc.) the brightness control disappear, I cannot neither adjust via the function keys.

The command "```
xbacklight -get
```" returns nothing at all

Any idea on how to fix this?

ps it is not an hardware problem as i have no problem at all under windows 10.


davide

---

