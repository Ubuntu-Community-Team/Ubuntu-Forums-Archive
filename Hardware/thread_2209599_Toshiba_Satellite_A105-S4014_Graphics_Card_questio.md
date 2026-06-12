---
title: "Toshiba Satellite A105-S4014 Graphics Card question"
date: 2014-03-06
forum: Hardware
---

### Post by Joe_Johnston on 2014-03-06
Hello All,

I am brand new to Ubuntu/Linux but absolutely in love with it right out of the gate! Such an amazing OS and I hope to convince more people to use it over time.  

I do have a question regarding my system. On the Toshiba website, [http://support.toshiba.com/support/modelHome?freeText=1311509](http://support.toshiba.com/support/modelHome?freeText=1311509) my system specs show the GMA950 graphics card but when I run, sudo lshw -c display the output seems to show a different graphics driver:

```
*-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f0a00000-f0a7ffff ioport:1800(size=8) memory:d0000000-dfffffff memory:f0b00000-f0b3ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0a80000-f0afffff

```
Is this correct information and does Ubuntu know better what my laptop contains or is this an issue I need to resolve?

Thank you for the input and forgive my newbieness! :) I am anxious to become an Ubuntu Guru.

Joe

---

### Post by phidia on 2014-03-06
Just for a little light reading:  > GMA 950[edit]
The GMA 950 was the second graphics core produced under Intel's Graphics Media Accelerator product name, and was incorporated in the Intel 945G chipsets.
The processor includes a 400 MHz 256-bit core, supporting up to 10.6GB/s memory bandwidth with DDR2-667 system RAM, up to 224MB max. video memory through DVMT scheme, 1.6GPixels/s and 1.6GTexels/s fill rate, a max. resolution of 2048x1536 for both analog and digital displays, 2 SDVO ports for flat-panels and/or TV-Out via ADD2 cards or media expansion cards.
3D-wise, GMA 950 supports up to 4pixels per clock rendering, Microsoft DirectX 9.0 hardware acceleration & Vertex shader 3.0 and OpenGL 1.4 with ARB extensions. From wikipedia 

So I believe lshw is just giving you the fine details. Intel GPUs are generally pretty well supported OOTB in linux.
Summing up: as long as you're not seeing any abnormalities you're fine.

---

### Post by Joe_Johnston on 2014-03-06
Thank you for this info as I have not noticed any issues but it confused me when things did not seem to match for specs. I just wanted to confirm with more experienced users if this was normal or acceptable.

To add more confusion to the mix, when I click on Details - Graphics it shows Driver Unknown and Experience Standard, for whatever that means.

---

### Post by Yellow Pasque on 2014-03-06
> Is this correct information and does Ubuntu know better what my laptop contains

They're both correct; lspci is just being more specific.
Ubuntu takes information from the PCI database. If you had a Windows program that read PCI ID's, it would say the same thing.

> To add more confusion to the mix, when I click on Details - Graphics it shows Driver Unknown and Experience Standard,
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

> is this an issue I need to resolve?
No.

---

### Post by Joe_Johnston on 2014-03-06
> **Temüjin said:**
> They're both correct; lspci is just being more specific.
Ubuntu takes information from the PCI database. If you had a Windows program that read PCI ID's, it would say the same thing.


[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)


No.


Thank you so much for the clarification! I am loving my Ubuntu!

Joe

---

