---
title: "Graphics Card problem in Dual Boot alongside with win10. UNCLAIMED display"
date: 2020-01-06
forum: Hardware
---

### Post by tolgayan on 2020-01-06
I am using ubuntu budgie alongside with win10. I am trying to use my external graphics card but I am facing some issues.

I have run the followinc command:
```
sudo lshw -C display

```

it says my graphics card is UNCLAIMED:

```

  *-display                 
       description: VGA compatible controller
       product: HD Graphics 620
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:128 memory:ed000000-edffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
  *-display UNCLAIMED
       description: 3D controller
       product: GM108M [GeForce 940MX]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:ee000000-eeffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:ef000000-ef07ffff

```

also,

```

nvidia-settings

```

gives

```

ERROR: NVIDIA driver is not loaded




ERROR: Unable to load info from any available system




(nvidia-settings:6286): GLib-GObject-CRITICAL **: 17:27:32.158: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 17:27:32.164: PRIME: Requires offloading
** Message: 17:27:32.164: PRIME: is it supported? yes



```

and,

```

lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
```

gives

```

00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 620 [8086:5916] (rev 02) (prog-if 00 [VGA controller])

```

When I run 

```

nvidia-smi

```

it gives, 

```

NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

```

I have installed nvidia-driver-430 from additional drivers. Then I also tried using nvidia-driver-390 but still the same (I have rebooted after installations).

I have searched in the web but could not find a probper solution. Any help would be appreciated.

---

### Post by CelticWarrior on 2020-01-07
The proper solution is to disable Secure Boot (assuming the recommended driver version has been correctly installed).

---

