---
title: "Ubuntu 10.04 VGA not detected Lenovo T420"
date: 2011-11-03
forum: Hardware
---

### Post by linux83 on 2011-11-03
Hello,

i have problem with VGA driver that is not detected on my Lenovo T420 installed with ubuntu 10.04 
.
i issuing lshw :
> *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64)this is output from lspci -nn:
> 
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0116] (rev 09)
but when i install version 11 for testing it can detect the drivers:

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)

 *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64)

any help to fix this on ubuntu 10.04 will be appreciated.

linux83

---

### Post by ahiung on 2011-11-03
Did you install the VGA driver from the Additional driver?

---

### Post by linux83 on 2011-11-03
> **ahiung said:**
> Did you install the VGA driver from the Additional driver?

hi from where i can get the addtional driver, i'm new to linux.

thanks alot

---

### Post by linux83 on 2011-11-04
i got the issue is the driver ( i915) that is not detected on current kernel.

when i install 10.10 or 11 as a testing on other HDD, i got it to work, but i don't want to upgrade.


i try this:
[http://askubuntu.com/questions/58376/how-do-i-install-the-intel-hd-3000-video-driver-on-ubuntu-10-04](http://askubuntu.com/questions/58376/how-do-i-install-the-intel-hd-3000-video-driver-on-ubuntu-10-04)

it's almost 2 weeks since trying to fix it without any luck, any help please.

linux83

---

### Post by linux83 on 2011-11-04
I found if i boot from live CD Graphs working fine and perfect while from normal hard disk boot is not. any suggestion please.

---

