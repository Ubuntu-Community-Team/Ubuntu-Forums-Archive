---
title: "hp pavilion g6-1113eo freezing. bios error system"
date: 2011-08-11
forum: Hardware
---

### Post by supermeow on 2011-08-11
Hi everyone, 

hope this is  the right place for posting this, if not, apologies in advance.

i am having problems with a (possibly) bios-software related issue regarding fan and temperature.

my specifications:

i have made a clean install of pinguy 11.04 64 bit on a newly bought (4 days ago) on this machine:
 
hp pavilion g6 - 1113eo
RAM 4GB
processor intel core i5 - 2410M cpu at 2.30Ghz
system 64 bit
hard drive is NTFS, 600 GB
ATA = intel mobile express chipset Sata Ahci Controller
Wireless card should be realink 5390

Laptop came with windows 7 preinstalled, which i kept only 24 hours and then switched to pinguy.

i remember running windows-hp automatic updates on my first days and that was it.

the issue is: my laptop freezes almost everyday and i am forced to shut down by pressing the start button. 

everytime i restart (due to freezing or not) i get a bios error message saying my "system went into thermal shutdown due to high temperature (90D)" and i should visit the hp website for more info.
 
a note which may be useful, i bought this latop in finland where i currently live, and the hp website redirects me to their finnish page... where i can't understand a word... as i am not a finnish speaker.

also let me specify that: the fan is not really going on at all, the laptop is new and very silent, i have it on my desk, in front of a window (open), so getting fresh air is not an issue here, pinguy itself is running smoothly except for a wifi problem (which i may be able to solve thanks to another post here) and in general my machine is not getting hot at all.

as u can imagine this is super annoying as it screws up my wok with no chance of saving... and forces me to shutdown every time.

my guess (i am a total newbie) is that something is preventing the fan from doing its work. or the settings for temperature and fan level are wrong...or maybe it is just the bios which is messed up

any help is greatly appreciated, possibly in not-too-complicated terms as i am not an expert at all (i can copy-paste commands in terminal, that's it)

cheers

---

### Post by supermeow on 2011-08-11
i hope someone can answer me...
meanwhile.. i found out  that pinguy comes with Ailurus, which gave me  this readings... maybe they can help some expert understand what is  wrong with the bios ?

here they are:

**Hardware Information**
   Motherboard name: 166F
   Motherboard vendor: Hewlett-Packard
   BIOS vendor:     Hewlett-Packard
   BIOS version:     F.24
   BIOS release date:     07/01/2011
   CPU 1 name:    Intel® Core™ i5-2410M CPU @ 2.30GHz
   CPU 1 level 1 cache size:     32K Data cache. 32K Instruction cache. 
   CPU 1 level 2 cache size:     256K Unified cache. 
   CPU 1 Mips:     4589.49
   CPU 2 name:     Intel® Core™ i5-2410M CPU @ 2.30GHz
   CPU 2 level 1 cache size:     32K Data cache. 32K Instruction cache. 
   CPU 2 level 2 cache size:     256K Unified cache. 
   CPU 2 Mips:     4589.59
   CPU 3 name:     Intel® Core™ i5-2410M CPU @ 2.30GHz
   CPU 3 level 1 cache size:     32K Data cache. 32K Instruction cache. 
   CPU 3 level 2 cache size:     256K Unified cache. 
   CPU 3 Mips:     4589.57
   CPU 4 name:     Intel® Core™ i5-2410M CPU @ 2.30GHz
   CPU 4 level 1 cache size:     32K Data cache. 32K Instruction cache. 
   CPU 4 level 2 cache size:     256K Unified cache. 
   CPU 4 Mips:     4589.62
   64 bit CPU?     Yes!
   Total memory:     3.8 GB
   Total swap:     4140 MBytes
   Ethernet card: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)   
   Battery charging state:     charged   
   Battery remaining capacity:     4320 mAh   
   Battery full capacity: 4320 mAh

**Linux Information**
   Host name:    supermeow-rebirth2011
   Uptime:     4 hours 6 minutes
   Kernel version:     2.6.38-9-generic
   Kernel arch:     x86_64
   Default shell:    /bin/bash
   X server version:     X.Org X Server 1.10.1
   OpenGL direct rendering:     Yes
   OpenGL vendor:     Tungsten Graphics, Inc
   OpenGL renderer:     Mesa DRI Intel® Sandybridge Mobile GEM 20100330 DEVELOPMENT
   OpenGL version:     2.1 Mesa 7.10.2
   GCC version:     4.5.2
   Java version:    1.6.0_26
   Python version:     2.7.1+
   GTK version:     2.24.4
   PyGTK version:     2.22.0
   Firefox version:    Mozilla Firefox 5.0
   Ubuntu version:   11.04
   GNOME version:     2.32.1
   GNOME locale:     en_GB.UTF-8

also, i typed *sensors * in terminal and this is the output:
acpitz-virtual-0
Adapter: Virtual device
temp1:       +42.0°C 

any idea?

thanks

---

