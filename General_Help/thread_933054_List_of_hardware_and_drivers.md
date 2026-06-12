---
title: "List of hardware and drivers"
date: 2008-09-29
forum: General Help
---

### Post by mundo on 2008-09-29
Hi,

How do I view the hardware that I have on my machine and the drivers that are being used?

---

### Post by jualin on 2008-09-29
Go to the terminal and type > lshw

---

### Post by mundo on 2008-09-30
Thanks, this shows the hardware but how can I see the drivers?

---

### Post by ryanhaigh on 2008-09-30
First a little note on lshw, I have always found having it output html to a file and openning in the browser a lot easier to read:
```
lshw -html > system.html && xdg-open ./system.html
```

The following command will list all currently utilised modules:
```
lsmod
```

---

### Post by jualin on 2008-10-01
> **mundo said:**
> Thanks, this shows the hardware but how can I see the drivers?

Wherever the hardware is mentioned the driver should also be mentioned somewhere on the file. 
For instance >  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1e:4c:3f:5d:d4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver**=ath5k_pci ip=128.186.243.81 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

In my case the driver ath5k_pci is being used for my wireless adapter.

---

### Post by ryanhaigh on 2008-10-01
> **jualin said:**
> Wherever the hardware is mentioned the driver should also be mentioned somewhere on the file. 
For instance 
In my case the driver ath5k_pci is being used for my wireless adapter.

Thanks for that info, I hadn't really gone through the output of lshw properly, this will be very useful as I will soon be compiling a custom kernel for a very low-powered system.

---

### Post by MehdizLinux on 2009-11-19
I cannot see the version of driver. Is there any other way? And how can I quickly go to the post I'm waiting for a replay in that?

```

 *-display
                description: VGA compatible controller
                product: G71 [Quadro FX 1500]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:e1000000-e1ffffff memory:d0000000-dfffffff(prefetchable) memory:e2000000-e2ffffff ioport:1000(size=128) memory:e0000000-e001ffff(prefetchable)

```

---

### Post by ryanhaigh on 2009-11-19
You are using the nvidia driver, so to determine the version you can either search synaptic for 'nvidia' and see which version is installed or run nvidia-settings which will also give you the version.

---

