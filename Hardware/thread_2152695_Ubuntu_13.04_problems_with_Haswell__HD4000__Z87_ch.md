---
title: "Ubuntu 13.04 problems with Haswell / HD4000 / Z87 chipset"
date: 2013-06-08
forum: Hardware
---

### Post by kornelix on 2013-06-08
The main board is ASRock Z87E and it has two problems:

1. 
The max monitor resolution available is 1920 x 1080, but my monitor is 2560 x 1440.
This is by using the standard Displays dialog in System Settings.
The ASRock ads claim the board will go up to 4K x 2K using the HMDI interface, albeit with less than 60Hz refresh.
I tried to make an xorg.conf file but only succeeded in blowing up the X server.
Can someone give me a sample of a valid xorg.conf to set a higher monitor resolution?

2. 
The onboard WiFi is not recognized. A USB stick WiFi works fine. 
Installing the Broadcom WiFi driver from the repos did not help. 


Here is some more hardware information in case this is relevant:

~ $: sudo lshw -C network
  *-network
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:19 memory:f0600000-f0607fff memory:f0400000-f05fffff


~ $: sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Haswell Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:f000(size=64)
~ $:

---

### Post by wujj123456 on 2013-06-10
Sorry that I can't answer your question, but looks like you've at least get Ubuntu installed.  I flashed the image onto my USB stick, but after I select "Try Ubuntu", the screen just goes black.  Were you able to go into LiveCD easily?

---

### Post by kornelix on 2013-06-10
wujj: yes the live CD worked fine. only the monitor resolution sucks.

---

### Post by kornelix on 2013-06-10
I solved the monitor resolution problem.
I changed the cable from HMDI to Display Port.
The full monitor resolution of 2560x1440 is now available.

---

### Post by Ten Ten Steve on 2013-07-14
I'm running the same mob as you with Ubuntu 13.04 and I'm having an issue with my SMBus controller driver. Could you tun the command 

sudo lshw -class bus

and see if you get 

*-serial UNCLAIMED
       description: SMBus
       product: Lynx Point SMBus Controller
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       version: 04
       width: 64 bits
       clock: 33MHz
       configuration: latency=0
       resources: memory:f1535000-f15350ff ioport:f040(size=32)

I've installed a NIC into the PICe and the two network interfaces are detected by lshw but I only see the board Ethernet interface when I open /etc/udev/rules.d/70-persistent-net.rules
The NIC was working perfectly in my old rig.
I'm hoping that resolving the SMBus Controller driver will get my NIC to work. 
Thanks in advance

---

### Post by kornelix on 2013-07-15
YES - here it is:

   *-serial UNCLAIMED       description: SMBus
       product: Lynx Point SMBus Controller
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       version: 04
       width: 64 bits
       clock: 33MHz
       configuration: latency=0
       resources: memory:f0739000-f07390ff ioport:f040(size=32)

---

### Post by Ten Ten Steve on 2013-07-15
I'm glad I'm not the only one. 
Are you using the PCIe slot for anything?

By the way, upgrading to the 3.10 generic kernel helped to clear up some errors I was seeing in dmesg.

---

### Post by kornelix on 2013-07-15
No, I am not using the PCIe slot.
The HD4000 onboard GPU is adequate for me.

---

