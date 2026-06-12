---
title: "Problem Configuring Extendend monitor on a Laptop"
date: 2011-10-24
forum: Hardware
---

### Post by 0mbr3 on 2011-10-24
I am having a strange issue when plugging in an extended monitor on my Dell Vostro 3550 Laptop. 

On a fresh install of Ubuntu 11.10, as soon as i plug in an extended monitor it get detected, the monitors will keep on randomly turning themself on and off and switching resolution. Sometime i have both screen ok, and then one switch to wrong resolution other screen turned OFF, then switch again to both wrong resolution or both ON but with Mirror.. and so on. (At least 5 swtich while writing this post)

I could not identify any patterns or triggers to this phenomena 

Also when i check the Display GUI i can see that the configuration is changing there as well.

So i thought that maybe by creating a xorg.conf file, things will get solved, but when i try to generate a xorg.conf i get the following:

```

X.Org X Server 1.10.4 
Release Date: 2011-08-19 
X Protocol Version 11, 
Revision 0 Build 
Operating System: Linux 2.6.24-29-server x86_64 Ubuntu Current 
Operating System: Linux my-machine 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=e2b7e4b2-720a-4ea7-af1c-3757f4c36bfc ro quiet splash vt.handoff=7 
Build Date: 29 September 2011  02:45:13AM xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support)  Current version of pixman: 0.22.2     
Before reporting problems, check http://wiki.x.org     to make sure that you have the latest version. Markers: (--) probed, (**) from config file, (==) default setting,     (++) from command line, (!!) notice, (II) informational,     (WW) warning, (EE) error, (NI) not implemented, (??) unknown. (==) Log file: "/var/log/Xorg.0.log", 
Time: Sat Oct 15 14:07:13 2011 List of video drivers:     

siliconmotion     radeon     displaylink     qxl     s3     sis     neomagic     trident     tdfx     r128     vmwlegacy     ati     vmware     nouveau     mga     intel     savage     openchrome     mach64     cirrus     sisusb     fbdev     vesa

 (EE) Failed to load module "vmwgfx" (module does not exist, 0)
 (EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx 
/xorg.conf.new" (==) Using system config directory "/usr/share/X11/xorg.conf.d
" Number of created screens does not match number of detected devices.   
Configuration failed. 
 ddxSigGiveUp: Closing log
```

End i end up with a default empty template of the xorg.conf

Maybe i should mention that this laptop is using and Hybrid Graphic card (intel/ATI).

My lshw -video looks like this: 
```
id:display
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

id:display
description: VGA compatible controller        
product: 2nd Generation Core Processor Family Integrated Graphics Controller        
vendor: Intel Corporation       
 physical id: 2
        bus info: pci@0000:00:02.0
        version: 09        width: 64 bits        c
lock: 33MHz        capabilities: msi pm vga_controller bus_master cap_list rom         
configuration: driver=i915 latency=0       
 resources: irq:53 
memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)

```I am totally new to Linux, and all of this is very frustrating as i spent my first day of linux trying to solve this still no improvent. So any insight would be much appreciated.

---

