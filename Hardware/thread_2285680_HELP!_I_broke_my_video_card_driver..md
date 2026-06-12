---
title: "HELP! I broke my video card driver."
date: 2015-07-07
forum: Hardware
---

### Post by josh142 on 2015-07-07
I typed sudo apt-get install nvidia-current into the terminal to update my graphics card drivers but I think I mismatched my graphics card to its driver and now my application that uses openGL and SDL doesn't even launch a window.  

My graphics card is this: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
Its an Acer laptop.

How do I get my old drivers back?

---

### Post by josh142 on 2015-07-07
Actually, I just used sudo apt-get remove to get rid of the nvidia driver, but I'm back at my original problem. How do I update graphics card drivers?

---

### Post by Bashing-om on 2015-07-07
josh142; Hello;

If Intel is the only Graphics Processor Unit in the box. best advise is leave well enough alone. Intel offers full support for linux with what they provide out of the box . Anything other, then you are "testing" .

To verify the hardware:
```

lspci -vnn | grep VGA -A 12

```

If we are looking then at a hybrid graphics situation (nvidia), then the alternate graphics  chip set controls the chip set in use. This control is most often via nvidia-settings .

[INDENT][INDENT]can't beat best
[/INDENT][/INDENT]

---

### Post by westie457 on 2015-07-07
Welcome to the Forums josh142
In the terminal run ```
sudo lshw -C video
```
In the output you should see driver=i915, which is the current driver provided by Intel. to the best of my knowledge there is not another driver available for Intel graphic cards.

---

### Post by josh142 on 2015-07-07
Thanks for the quick reply!
I typed sudo lshw -C video and got this output:
> *-display               
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
       resources: irq:64 memory:b3000000-b33fffff memory:c0000000-cfffffff ioport:5000(size=64)
  *-display UNCLAIMED
       description: 3D controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b2000000-b2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128)
So I have the right driver, but I have a feeling the NVIDIA display shouldn't be there. When I go to displays, only the laptop monitor shows. The problems I have been having are a flashing mouse cursor and openGL applications running slow.

---

### Post by Bashing-om on 2015-07-08
josh142; Hey;

Indications are that this is a hybrid graphics situation.
Let's look at what the hardware is:
```

lspci -vnn | grep VGA -A 12

```
and match a driver to this hardware.

[INDENT][INDENT]that link in between
[/INDENT][/INDENT]

---

### Post by josh142 on 2015-07-08
output of  lspci -vnn | grep VGA -A 12:

> 00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device [1025:0866]
    Flags: bus master, fast devsel, latency 0, IRQ 64
    Memory at b3000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:03.0 Audio device [0403]: Intel Corporation Device [8086:0a0c] (rev 0b)
    Subsystem: Acer Incorporated [ALI] Device [1025:0866]



---

### Post by Bashing-om on 2015-07-08
josh142; Hummm ...

Not at all sure what to make of the 'lshw' output. We do have these outputs:
> 
I typed sudo lshw -C video and got this output:
product: Haswell-ULT Integrated Graphics Controller >> bus info: pci@0000:00:02.0 >> configuration: driver=i915
product: NVIDIA Corporation >> bus info: pci@0000:03:00.0 >> configuration: ( no driver loaded)


But; but but
In the 'lspci' output there is no mention of the Nvidia device. What gives ? 
Is it turned off in bios ?

[INDENT][INDENT]maybe then when 'on'
[INDENT][INDENT][INDENT][INDENT]we can load a driver 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2015-07-09
> In the 'lspci' output there is no mention of the Nvidia device. What gives ? 
Nvidia Optimus devices are listed as "3D controllers" so you if grep for "VGA", they won't show up..

---

