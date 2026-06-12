---
title: "Nvidia installation -&gt; Black Screen."
date: 2009-01-04
forum: Hardware
---

### Post by OlivierB on 2009-01-04
Hi guys!

Im new to this forum and also new to Ubuntu. Im getting to understand it better and better, but still I have a problem with my Nvidia card to get it working.

Im using Ubuntu 8.10 (kernel 2.6.27-9-generic) and my Nvidia card is the 9300m GS.

My problem is: when i install the device driver (177) I reboot and get a black screen. I don´t hear the startup sound and also the keys like ctrl+alt+f1 and ctrl+alt+backspace aren´t working.



This is done on the low quality mode in ubuntu.

```
lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
```

```
       
lshw

 *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 9300M GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia

```


I really can´t get it to work and would be very thankfull if someone could tell me how to solve this problem!


Yours,

Olivier B.

---

