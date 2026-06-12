---
title: "Dell Vostro 3550 Dual Display Fail!"
date: 2011-10-28
forum: Hardware
---

### Post by 0mbr3 on 2011-10-28
Hi, 

I am using a Dell Vostro 3550 (Ironically the same that Ubuntu website use as a display picture the website) and after almost a week of installing and reinstalling different built of ubuntu (10.xx, 11.xx, kubuntu) i am about to give up. 

On a fresh install whether it s (10, or 11) i make all updates, but no proprietray drivers, so far all works fine, but as soon as i plug in my external monitor to extend my desktop, the headaches starts: 
My display resolution and positioning will keep on switching while X server is running. Which means that when using my computer in a time range of 10 minutes i would get through 5 different dispositions and resolutions. It could be both display working fine, then only one but with wrong resolution, then the two again but with mirror, then just the second, and so on.. 

I tried all advises i found out there. Using Xorg.conf, Xrandr, updating kernel, flashing my Bios .. and i finally arrived to the conclusion that no version of Ubuntu works with a Dell Vostro 3550, at least if you plan on using an extended Desktop. 

I would hope that a future update would fix that, but since i experience the exact same problem under 10.04 LTS, that makes doubt that this would happen anytime soon.

 So is there anyone out there that managed to make such a setup work on Ubuntu ? If not, maybe you ll find this thread in time before buying a vostro and plan as using it with any Ubuntu release.

---

### Post by leewillis77 on 2011-12-20
I'm seeing the same thing:


$ sudo lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series]


$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: NI Whistler [AMD Radeon HD 6600M Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:52 memory:e0000000-efffffff memory:f7b20000-f7b3ffff ioport:e000(size=256) memory:f7b00000-f7b1ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)

Running non-ATI drivers. Any steps to help debug this would be great - happy to do some investigative work on it.

---

### Post by Alexislavie on 2012-02-23
Check this post : [http://ubuntuforums.org/showthread.php?p=11712748](http://ubuntuforums.org/showthread.php?p=11712748)

---

