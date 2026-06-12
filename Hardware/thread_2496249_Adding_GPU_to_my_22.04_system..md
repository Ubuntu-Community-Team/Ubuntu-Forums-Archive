---
title: "Adding GPU to my 22.04 system."
date: 2024-03-19
forum: Hardware
---

### Post by BrassCat on 2024-03-19
I have been using the APU for graphics on my AMD 5600G. I am going to add AMD gpu rx 5600. Will the gpu driver already
be present on the installed system -or- will I need to add a driver to my system before I install the gpu ??
If I need to install a gpu driver, where can I find the procedure for the software installation ??

Thanks for any advice, Stan.

---

### Post by Yellow Pasque on 2024-03-19
If you are using the 6.5 kernel, it should work with the builtin amdgpu kernel module/driver:
```
echo `uname -r`
```

---

### Post by MAFoElffen on 2024-03-19
Just a note to the OP... (Learning moment.)

Copy and paste that command into the terminal. Note that those are not single-quote characters. Those are back-ticks, which are the lowercase of the `/~ key, which means command substitution within... Would also be equivalent to
```

echo $(uname -r)

```
But then again, if you just did
```

uname -r

```
It will give you the same text output.

He is absolutely correct... Just many ways of doing the same thing.

---

### Post by BrassCat on 2024-03-21
Thanks for the responses. Sorry to delay, life's been hectic.

I get no video from the Rx 5600.
Update on the Ubuntu
System is Mantic 23.10
Kernel is  6.5.0-25-generic.

Installed the GPU. Monitor connected to GPU only.
I get repeated boots, no screen shows
gigabyte b550 motherboard.

Is it possible that this kernel was still ion development ?

I checked bios using the integrated graphics, no card (GPU) is identified in the PCIe slot.

---

### Post by BrassCat on 2024-03-21
I will be borrowing a known good GPU to test if it will show up in bios or not. motherboard or GPU is faulty.

---

### Post by MAFoElffen on 2024-03-22
Do this first:
```

sudo lspci -knnn | grep -A3 -E 'VGA|Display|3D'

```
Please post the output within CODE Tags, like this
```

[noparse][CODE]
mafoelffen@Mikes-ThinkPad-T520:~$ sudo lspci -knnn | grep -A3 -E 'VGA|Display|3D'
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
    Subsystem: Lenovo 2nd Generation Core Processor Family Integrated Graphics Controller [17aa:21d1]
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119M [Quadro NVS 4200M] [10de:1057] (rev a1)
    Subsystem: Lenovo GF119M [Quadro NVS 4200M] [17aa:21d1]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

```[/noparse]
[/code]

---

### Post by him610 on 2024-03-24
> I get no video from the Rx 5600.
Did you connect the video cable to your new GFX card? (not motherboard connection)

---

### Post by Yellow Pasque on 2024-03-24
> I checked bios using the integrated graphics, no card (GPU) is identified in the PCIe slot. 

Try removing and reseating the card. Make sure you connect any external power connector(s). It looks like this card probably has an 8-pin connector.
If you can't get the BIOS screen to show up when your monitor is connected to the GPU, then the problem is not the kernel/OS.

---

### Post by MAFoElffen on 2024-03-24
+1 ---
> **Yellow Pasque said:**
> Try removing and reseating the card. Make sure you connect any external power connector(s). [COLOR=#ff0000]It looks like this card probably has an 8-pin connector.[/COLOR]
If you can't get the BIOS screen to show up when your monitor is connected to the GPU, then the problem is not the kernel/OS.

Additional to the power cable going to the card itself, on the motherboard, there is a plugin for the power to the PCIe Bus to power the PCIe cards... ensure both those have power.

---

### Post by Yellow Pasque on 2024-03-24
> **MAFoElffen said:**
> 
Additional to the power cable going to the card itself, on the motherboard, there is a plugin for the power to the PCIe Bus to power the PCIe cards... ensure both those have power.

Are you referring to a 4-pin Molex connector on the motherboard? I don't think most motherboards have those nowadays. Even the ones that do probably don't need it connected if just using one GPU and not OC'ing it.

---

### Post by BrassCat on 2024-04-01
Well, I see even more responses.  I thank you for the replies.I am now functional with the Radeon GPU.

So, to the following:

GPU tested good on another system.
GPU was inserted correctly.
Power supply is Corsair 650 watt (enough) with Ryzen 5600G.
8 pin GPU cable was inserted both ends firmly (GPU and PS).
One HP monitor on iGPU and one HP on GPU. All Display port.

It was a BIOS setup issue. I knew I had to enable the GPU. I did in fact.
Even to the point of setting it to GPU only. This did not work either, and froze 
my system, had to reset bios to get back to iGPU function.  Still did not display (Yes, good monitors.)
Restudied the motherboard manual, on another Uefi bios page, I found ANOTHER setting 
as to which device (internal or GPU) to try first !!! 
That is what made the difference and it started working. Why separate these settings 
across 2 different pages? The motherboard is a Gigabyte B550 Aurous elite ax v2.

Again thanks, just wanted to report the end of the issue. Stan.

---

