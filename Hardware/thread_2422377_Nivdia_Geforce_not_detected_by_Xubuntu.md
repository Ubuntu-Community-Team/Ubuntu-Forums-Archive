---
title: "Nivdia Geforce not detected by Xubuntu"
date: 2019-07-06
forum: Hardware
---

### Post by ahmed-k on 2019-07-06
Hi, I have the following laptop:
[https://support.hp.com/us-en/product/HP-Pavilion-15-p100-Notebook-PC-series/7234915/model/7489382](https://support.hp.com/us-en/product/HP-Pavilion-15-p100-Notebook-PC-series/7234915/model/7489382)
[https://support.hp.com/us-en/product/HP-Pavilion-15-p100-Notebook-PC-series/7234915]("https://support.hp.com/us-en/product/HP-Pavilion-15-p100-Notebook-PC-series/7234915/model/7489382")

It has:
**1. **Intel inside CORE i5
**2. **NIVDIA GEFORCE
[You can see more about that in the link at the top at "Downloads" or "Product Information"]

Now I can't see where Xubuntu hides the System Information but when I saw some commands in the internet to type into the Terminal, I did and I searched everything and only found "Intel" written, there was **no where** something called "Nivdia" or "Geforce"

So I think that "Nivdia Geforce" is not detected my Xubuntu
But also I don't know how to know if Nivdia Geforce is detected or not

So:
[B]1. Is Nivdia Geforce a GPU and Intel a CPU?
2. And how can I make Xubuntu to detect Nivdia Geforce
[/B]

---

### Post by ahmed-k on 2019-07-06
**And here is what the terminal says:**

[PHP]***************************************************:~$ lspci -k | grep -A 2 -i "VGA"
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
    Subsystem: Hewlett-Packard Company Haswell-ULT Integrated Graphics Controller
    Kernel driver in use: i915[/PHP]

**And here is what its suppose to say:**
[IMG]https://www.linuxbabe.com/wp-content/uploads/2016/04/Selection_010-1.png[/IMG]

As you can see the second one in the image(which is about Nivdia Geforce) is missing

---

### Post by him610 on 2019-07-06
Please show results of *inxi -Fxz* within code tags

---

### Post by Bashing-om on 2019-07-06
ahmed-k; Hey -


See him610's last -

In addition there is ->
Well like this:
> 
lspci -k | grep -A 2 -i "VGA"

where the command is looking at "vga"  the analog device.

to see both the analog and digital (nvidia) run:
```

lspci -k|grep -iEA5 'vga|3d'

```

to see what is loaded:
```

sudo lshw -C display

```

and to know which Nvidia driver(s):
```

dpkg -l | grep -i nvidia

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by mastablasta on 2019-07-08
You have 2 GPUs

[https://support.hp.com/si-en/document/c04475582](https://support.hp.com/si-en/document/c04475582)

> [COLOR=#000000][FONT=HPSimplifiedLight]Intel Core i5-4210U **with Intel HD Graphics 4400** (1.7 GHz, 3 MB cache, 2 cores)[/FONT][/COLOR]

> [COLOR=#000000][FONT=HPSimplifiedLight]**NVIDIA GeForce 840M** (2 GB DDR3 dedicated)[/FONT][/COLOR]

if you want to use nvidia, you will have to installproprietary drivers and then do a manual switch using bumblebee (optirun). more here: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

else you will have high performance option turne on all the time, so it won't conserve the laptop battery

---

### Post by ahmed-k on 2019-07-11
**Sorry for the late response,**

I covered my name in these codes

@him610
[PHP]
*****@*****-HP-Pavilion-15-Notebook-PC:~$ inxi -fxz
CPU:       Dual core Intel Core i5-4210U (-MT-MCP-) 
           arch: Haswell rev.1 cache: 3072 KB bmips: 9577
           clock speeds: max: 2700 MHz 1: 1161 MHz 2: 1212 MHz 3: 1199 MHz
           4: 1210 MHz
           CPU Flags: abm acpi aes aperfmperf apic arat arch_perfmon avx avx2
           bmi1 bmi2 bts clflush cmov constant_tsc cpuid cpuid_fault cx16 cx8
           de ds_cpl dtes64 dtherm dts epb ept erms est f16c flexpriority
           flush_l1d fma fpu fsgsbase fxsr ht ibpb ibrs ida invpcid
           invpcid_single lahf_lm lm mca mce md_clear mmx monitor movbe msr
           mtrr nonstop_tsc nopl nx pae pat pbe pcid pclmulqdq pdcm pdpe1gb
           pebs pge pln pni popcnt pse pse36 pti pts rdrand rdtscp rep_good
           sdbg sep smep ss ssbd sse sse2 sse4_1 sse4_2 ssse3 stibp syscall tm
           tm2 tpr_shadow tsc tsc_adjust tsc_deadline_timer vme vmx vnmi vpid
           xsave xsaveopt xtopology xtpr

[/PHP]














@Bashing-om
[PHP]
*****@*****-HP-Pavilion-15-Notebook-PC:~$ lspci -k | grep -A 2 -i "VGA" 
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
    Subsystem: Hewlett-Packard Company Haswell-ULT Integrated Graphics Controller
    Kernel driver in use: i915
[/PHP]

[PHP]
*****@*****-HP-Pavilion-15-Notebook-PC:~$ lspci -k|grep -iEA5 'vga|3d'
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
    Subsystem: Hewlett-Packard Company Haswell-ULT Integrated Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
    Subsystem: Hewlett-Packard Company Haswell-ULT HD Audio Controller
[/PHP]

[PHP]
*****@*****-HP-HP-Pavilion-15-Notebook-PC:~$ sudo lshw -C display
[sudo] password for suleiman: 
  *-display                 
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:b2000000-b23fffff memory:a0000000-afffffff ioport:6000(size=64) memory:c0000-dffff

[/PHP]

[PHP]
*****@*****-HP-Pavilion-15-Notebook-PC:~$ dpkg -l | grep -i nvidia
[/PHP]
Nothing came for the last one








@mastablasta
I don't really understand what you're saying could you explain more please?

---

### Post by mastablasta on 2019-07-12
you have two graphics processors (GPU). Intel is running. if you want to use the nvidia chip, you need to install closed source drivers (additional drivers app).

in windows the system would then switch between intel GPU and nvidia automatically (Optimus technology). it would use intel GPU for office work and nvidia for heavy tasks (e.g. running games, picture editing...) since nvidia didn't make this Optimus technology work on linux drivers, the users made it themselves using manual switch and named it Bumblebee (more on this in the link i posted).

---

### Post by him610 on 2019-07-12
I am sure most of the forum regulars have heard about the availability of current Nvidia drivers, but this article explains it, [https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its]("https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its")

@ahmed-k, *inxi -Fxz* is supposed to be with an uppercase [COLOR="#FF0000"]F,[/COLOR]
Linux and most operating systems are case sensitive.

---

