---
title: "Nvidia driver not loading on Ubuntu 20.10"
date: 2021-01-22
forum: Hardware
---

### Post by grabasimo on 2021-01-22
[COLOR=#000000]Ubuntu 20.10 Nvidia driver not loading.

Hi. Have problem with nvidia drivers at ubuntu 20.10. Installed a new system and llast drivers nvidia 460.[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]but nvidia-smi dot see driver[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]```
nvidia-smi
```[/COLOR]```

[COLOR=#000000]NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.[/COLOR]
```
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]```
sudo lshw -C display
```[/COLOR]```

[COLOR=#000000]*-display UNCLAIMED[/COLOR]
[COLOR=#000000]description: 3D controller[/COLOR]
[COLOR=#000000]product: GP107M [GeForce GTX 1050 Ti Mobile][/COLOR]
[COLOR=#000000]vendor: NVIDIA Corporation[/COLOR]
[COLOR=#000000]physical id: 0[/COLOR]
[COLOR=#000000]bus info: pci@0000:01:00.0[/COLOR]
[COLOR=#000000]version: a1[/COLOR]
[COLOR=#000000]width: 64 bits[/COLOR]
[COLOR=#000000]clock: 33MHz[/COLOR]
[COLOR=#000000]capabilities: pm msi pciexpress bus_master cap_list[/COLOR]
[COLOR=#000000]configuration: latency=0[/COLOR]
[COLOR=#000000]resources: memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff[/COLOR]
[COLOR=#000000]*-display[/COLOR]
[COLOR=#000000]description: VGA compatible controller[/COLOR]
[COLOR=#000000]product: HD Graphics 630[/COLOR]
[COLOR=#000000]vendor: Intel Corporation[/COLOR]
[COLOR=#000000]physical id: 2[/COLOR]
[COLOR=#000000]bus info: pci@0000:00:02.0[/COLOR]
[COLOR=#000000]version: 04[/COLOR]
[COLOR=#000000]width: 64 bits[/COLOR]
[COLOR=#000000]clock: 33MHz[/COLOR]
[COLOR=#000000]capabilities: pciexpress msi pm vga_controller bus_master cap_list rom[/COLOR]
[COLOR=#000000]configuration: driver=i915 latency=0[/COLOR]
[COLOR=#000000]resources: irq:126 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff[/COLOR]
```
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]nvidia-settings[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]```
 nvidia-settings
```[/COLOR]```

[COLOR=#000000]
[/COLOR]
[COLOR=#000000]ERROR: NVIDIA driver is not loaded[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]ERROR: Unable to load info from any available system[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000](nvidia-settings:3702): GLib-GObject-CRITICAL **: 13:16:51.057: g_object_unref: assertion 'G_IS_OBJECT (object)' failed[/COLOR]
[COLOR=#000000]** Message: 13:16:51.065: PRIME: Requires offloading[/COLOR]
[COLOR=#000000]** Message: 13:16:51.065: PRIME: is it supported? yes[/COLOR]
[COLOR=#000000]** Message: 13:16:51.108: PRIME: Usage: /usr/bin/prime-select nvidia|intel|on-demand|query[/COLOR]
[COLOR=#000000]** Message: 13:16:51.108: PRIME: on-demand mode: "1"[/COLOR]
[COLOR=#000000]** Message: 13:16:51.108: PRIME: is "on-demand" mode supported? Yes[/COLOR]

```
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]prime-select

```
rime-select query
```[/COLOR]```

[COLOR=#000000]nvidia[/COLOR]
```
[COLOR=#000000]
[/COLOR]I don't have any idea how to load this driver... 
Any ideas?

cheers
[COLOR=#000000]
[/COLOR]

---

### Post by CelticWarrior on 2021-01-22
Have you disabled Secure Boot? If so how exactly have you installed the drivers? Did it work at some point and then this happen or never worked?

---

### Post by grabasimo on 2021-01-22
Secure boot is off. I installed drivers on new system. Yes worked before. Happens after when i upgrade system from 20.04 to 20.10. I tried all drivers (ppa from 418 to 460, drivers from nvidia.com). I update bios and my kernel lost signed. i decide to install new system should work without issues.  Even when using nouveau looks it not see nvidia card. just use intel card...


[B]

EDIT!

Finally i installed driver and working. I removed all  nvidia driver from system (ppa) and dkms. reboot system and without any drivers (ctrl+alt+f3) login to system. install binary drivers from nvidia.com without dkms! after reboot is working.




[/B]```
nvidia-smi Fri Jan 22 18:16:48 2021       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 460.32.03    Driver Version: 460.32.03    CUDA Version: 11.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  GeForce GTX 105...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   50C    P0    N/A /  N/A |    140MiB /  2002MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1536      G   /usr/lib/xorg/Xorg                 54MiB |
|    0   N/A  N/A      1747      G   /usr/bin/gnome-shell               85MiB |
+-----------------------------------------------------------------------------+
```

---

