---
title: "How to power cycle Intel PCI bridge? using setpci?"
date: 2021-02-14
forum: Hardware
---

### Post by New_buntu_89 on 2021-02-14
I'm having an issue with my Ethernet card that resolves itself by just turning the computer off and on again. I haven't checked what happens with a reboot. There's more detail in this thread ([https://ubuntuforums.org/showthread.php?t=2457411](https://ubuntuforums.org/showthread.php?t=2457411)). Essentially, a lot of times the Ethernet interface won't be recognized at all as even being present. I tried changing the Ethernet driver to 3 different versions, but that didn't help.

When Ethernet is working well, lshw shows this:

```

        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL810xE PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: enp1s0
                version: 05
                serial: b8:70:f4:69:5b:4c
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes driver=r8169  duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.0.53 latency=0  link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:16 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
                

```           
                
                
                
When it's not working, it will show the same thing for -pci:0, but without the Ethernet section.
                
What I'd like to try is to do a full power cycle of that PCI bridge when the computer is already booted up, so I can just put it in a script and not have to reboot the whole computer. It wouldn't be a solution, but it's a potential workaround. 

I saw this issue ([https://unix.stackexchange.com/questions/73908/how-to-reset-cycle-power-to-a-pcie-device](https://unix.stackexchange.com/questions/73908/how-to-reset-cycle-power-to-a-pcie-device)), but my pci folder doesn't have anything to trigger under *power* (it's another directory, not a sysfs file), and I tried  *remove* , *reset*, and *rescan* to no effect (with the Ethernet card not working,  obviously). I only did it for pci@0000:00:1c.0 in particular though, I didn't attempt to find a higher level that would remove pci@0000:00:00.0, which I don't actually know if it's possible... It seems that none of those will actually power off the PCI bridge, though.

Apparently, it's possible to use setpci for this, but I am afraid it'll take me 10+ years to figure out how to do this on my own. Here's the datasheet for the PCI bridge, as far as I can tell: 

[https://www.intel.com/content/dam/www/public/us/en/documents/datasheets/6-chipset-c200-chipset-datasheet.pdf](https://www.intel.com/content/dam/www/public/us/en/documents/datasheets/6-chipset-c200-chipset-datasheet.pdf)

There's a newer version, but this laptop was purchased in August 2011, so I think specification changes won't match:

[https://www.intel.com/content/dam/www/public/us/en/documents/specification-updates/6-and-c200-chipset-specification-update.pdf](https://www.intel.com/content/dam/www/public/us/en/documents/specification-updates/6-and-c200-chipset-specification-update.pdf)

I believe what I'm looking for is either a bad configuration with the Power Management policies (which I think will take forever to find), or to write a configuration to it that will send it to an S5 (Soft OFF) state first, and then trigger a wake event. 

From what I've read so far, it looks like you can trigger the wake event manually using the PME_B0_EN bit in the GPE0_EN register, but I haven't found how to turn it off first. Alternatively, it may be possible to do the whole reset with the Secondary Bus Reset bit in the Bridge Control Register. Another alternative seems to be in the PCI Power Management Control and Status Register. 

Has anyone here done similar stuff before, or worked with Intel PCI Express specifically? What should I be looking out for before I start testing stuff? Which status registers should I be reading before I try to send any writes? Better yet, has anyone been able to power cycle this type of PCI bridge from setpci?

I need a bit of guidance to be able to get this done in a reasonable time.

---

### Post by TheFu on 2021-02-18
pm-suspend?

---

### Post by New_buntu_89 on 2021-02-24
Well, no, I'm not trying to restart the whole computer. I just need to power cycle the Ethernet card (and/or the PCI bridge) to recover Ethernet function after bootup. Suspend won't be that different from a restart... Unless there's options in one of those commands that can cause this...

---

### Post by TheFu on 2021-02-24
> **New_buntu_89 said:**
> Well, no, I'm not trying to restart the whole computer. I just need to power cycle the Ethernet card (and/or the PCI bridge) to recover Ethernet function after bootup. Suspend won't be that different from a restart... Unless there's options in one of those commands that can cause this...

It is 15 seconds to try it and see if it works at all or not.  If it doesn't work, that's important.  If it does work, you can research how it gets done.

---

### Post by New_buntu_89 on 2021-02-27
So, it did not work, but it did cause a couple of other issues. The screen was dimmed to its minimum, and it caused a glitch on the second monitor (which goes away with a single click). 

Thanks for the quick reply, btw. I'll be paying more attention now.

---

### Post by TheFu on 2021-02-28
When suspend is working, it tells the different parts to shutoff. Coming out of suspect reinitializes the hardware and renews connections. For network devices, it disconnects and reconnects during that process.  That's why it was my suggestion. If it had worked, then your system would already have the needed tools and settings on it to accomplish what you wanted.

I have a laptop.  Sometimes when NFS shares become stale, I don't want to restart stuff or even hunt down the command to restart the NFS client connection.  But I can close the lid for 10 seconds, then reopen the lid and have it all working again.  That method works for other issues sometimes too - like when the system seems to be locked up (it is just 1 bloated program), I'll close the lid and wait for the LEDs so show it isn't running anymore. Then reopen the lid and have control back. Of course, in the 2nd instance, it doesn't always work and sometimes I need to go to a different computer and ssh into the laptop, check the process table for what's eating all the CPU/RAM, then kill that process.  99.999999% of the time, it is firefox or chromium. Huge, bloated, programs.

Alas, power controls for 10+ yr old computers were poor and often didn't work correctly due to poor linux driver support, if it worked with that other OS. About the last 8 yrs, Linux power management has sorta just worked for laptops.  3 of my laptops since 2012 have worked. Perhaps I was just lucky and that is skewing my view on this?

Doubt I'd waste much time with a 10/100 NIC.  A new NIC, say an Intel PRO/1000, is $25 and makes this issue go away unless there is some other issue with the motherboard.

---

### Post by New_buntu_89 on 2021-02-28
Well, mines is a laptop, so replacing the Ethernet card may not be that simple :(...  Any other ideas? I can try opening the case and checking tomorrow...

---

### Post by New_buntu_89 on 2021-03-14
WAAAAAIT! I just tried again with pm-suspend, and I got into a very weird state. I left it suspended for a longer time than before, and disconnected the fan, which was plugged to a USB port right next to the Ethernet port. This time, lshw returns this:


> 
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24

           *-network UNCLAIMED
                description: Ethernet controller
                product: RTL810xE PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 05
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd cap_list
                configuration: latency=0

        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:f7e00000-f7efffff

           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1000 [Condor Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 00
                serial: 74:e5:0b:06:f2:62
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-66-generic firmware=39.31.5.1 build 35138 ip=192.168.0.51 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:39 memory:f7e00000-f7e01fff



Also, lspci -knn returns the following:


```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba Corporation RTL810xE PCI Express Fast Ethernet controller [1179:fc30]
    Kernel modules: r8169
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
```



Basically, the PCI bridge is still missing something in the "resources" section, but at least the Ethernet port is being recognized. From what I found online, it seems that this only means that there's no driver assigned to the Ethernet port. Is it possible assign it manually, or to get the computer to re-check and find the appropriate driver automatically?


I already tried **sudo modprobe -r r8169** and re-adding it.

---

