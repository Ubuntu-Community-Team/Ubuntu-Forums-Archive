---
title: "how to swich from different VGA on Ubuntu 14 lts"
date: 2015-07-24
forum: Hardware
---

### Post by marco109 on 2015-07-24
*What I checked out:*
  **sudo lshw -c video**
  ```
*-display               
   description: VGA compatible controller
   product: Haswell-ULT Integrated Graphics Controller
   vendor: Intel Corporation
   physical id: 2
   bus info: pci@0000:00:02.0
   version: 09
   width: 64 bits
   clock: 33MHz
   capabilities: msi pm vga_controller bus_master cap_list rom
   configuration: driver=i915 latency=0
```
  **sudo lspci -nnk | grep -i vga -A3 | grep 'in use'**
  ```
Kernel driver in use: i915
Kernel driver in use: radeon
```
  **sudo lspci -nnk | grep -i vga -A2**
  ```
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
Subsystem: Dell Device [1028:0609]
Kernel driver in use: i915
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Venus PRO [Radeon HD 8850M] [1002:6823] (rev ff)
Kernel driver in use: radeon
```
  *What I want to achieve:* I would like to know if the Radeon  VGA is the main in use on my sistem. And if it's not, I would like to  set it as the default one. How can I do this? 
  I can provide additional info, if needed.

---

### Post by Julind on 2015-07-24
To check what graphics card is in use run this command on the terminal.
```
[SIZE=2]lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA[/SIZE]
```
Whatever device has the **[VGA controller] **line at the end is the one in use.

---

### Post by marco109 on 2015-07-24
then I have the Intel integrated one in use... how can I set just the ATI VGA?

---

### Post by Julind on 2015-07-24
I run on a nVidia so i don't know how. But i saw this post and maybe it could be useful to you.
[https://xpressrazor.wordpress.com/2013/01/13/how-to-setup-amdintel-hybrid-graphics-cards-in-linux-ubuntu/](https://xpressrazor.wordpress.com/2013/01/13/how-to-setup-amdintel-hybrid-graphics-cards-in-linux-ubuntu/)

---

### Post by Vladlenin5000 on 2015-07-24
> **Julind said:**
> I run on a nVidia so i don't know how. But i saw this post and maybe it could be useful to you.
[https://xpressrazor.wordpress.com/2013/01/13/how-to-setup-amdintel-hybrid-graphics-cards-in-linux-ubuntu/](https://xpressrazor.wordpress.com/2013/01/13/how-to-setup-amdintel-hybrid-graphics-cards-in-linux-ubuntu/)

^^^^
This.
-or-
You can simply disable the integrated one (Intel) in your BIOS/UEFI settings. If what you want is to always use the better card then that would be the logical way to do it.
Use the above post link for instructions on how to setup a hybrid system where you can toggle the cards only (reboot usually needed). Just disable one or the other if you don't want to deal with the hybrid feature.

---

### Post by marco109 on 2015-07-29
Ok, I've followed that hybrid installation guide.. But I figured out those problems:
[LIST=1]
[*]I've never been able to see under 'Software & Updates" -> "Additional Drivers" some experimental version of fglrx drivers; 
[*]I've never been able to run the **sudo aticonfig --initial -f** command. 
[/LIST]
Of course I've tried to install proprietary drivers anyway, rebooted my laptop and then the black screen with low-graphics appeared: ctrl + alt + f1 and logged in.
I run again those commands, and here you can see my outputs:
**sudo lspci -nnk | grep -i vga -A3 | grep 'in use'**
```
    Kernel driver in use: i915
    Kernel driver in use: fglrx_pci
```
**sudo lspci -nnk | grep -i vga -A2**
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
    Subsystem: Dell Device [1028:0609]
    Kernel driver in use: i915
--
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Venus PRO [Radeon HD 8850M] [1002:6823]
    Subsystem: Dell Device [1028:0609]
    Kernel driver in use: fglrx_pci
```
**sudo lshw -c video**
```
  *-display
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:62 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64)
  *-display
       description: VGA compatible controller
       product: Venus PRO [Radeon HD 8850M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:65 memory:d0000000-dfffffff memory:f0500000-f053ffff ioport:3000(size=256) memory:f0540000-f055ffff
```
**sudo lspci -vnnn | perl -lne 'print if /^\d+\:.+(\S+|:|S+|])/' | grep VGA**
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09) (prog-if 00 [VGA controller])
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Venus PRO [Radeon HD 8850M] [1002:6823] (prog-if 00 [VGA controller])
```

Any suggestion???

---

