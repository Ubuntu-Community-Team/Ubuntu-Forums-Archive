---
title: "Dell TrueMobile 1300 not detected on Inspiron 8500"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by eljaco on 2006-01-29
Hey, I have not been able to set up my wireless card on Breezy. It was working when I used Windows, but I guess I just don't know how to configure it in (K)ubuntu. I posted this thread after following the HOWTO [http://ubuntuforums.org/showthread.php?t=25683&page=31&highlight=.inf]("http://ubuntuforums.org/showthread.php?t=25683&page=31&highlight=.inf")

If it helps, this is what I get from ```
 sudo lshw 
```
>  *-network:1 UNCLAIMED
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@02:03.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:faff6000-faff7fff irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master


Hope someone has had this problem before and can help me out. Let me know if you need any more specs.
Thanks.

---

