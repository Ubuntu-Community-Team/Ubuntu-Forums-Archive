---
title: "Video Card not detected in lspci."
date: 2013-04-20
forum: Hardware
---

### Post by lorderico on 2013-04-20
Hello,

I have an NVidia quadro 290 video card and I'm not 100% sure it works.  I would like to use CUDA on it.  I am running  xubuntu 12.04.  Do you think there is any way I am missing anything?

Thanks a lot,
Eric
 

My motherboard is here:

Motherboard:
[http://www.msi.com/product/mb/H61M-E33--B3-.html](http://www.msi.com/product/mb/H61M-E33--B3-.html)

uname -a
Linux singularity 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


Here is lspci -t:
 lspci -t
-[0000:00]-+-00.0
           +-01.0-[01]--
           +-02.0
           +-16.0
           +-1a.0
           +-1b.0
           +-1c.0-[02]--
           +-1c.2-[03-04]----00.0-[04]----00.0
           +-1c.4-[05]----00.0
           +-1d.0
           +-1f.0
           +-1f.2
           +-1f.3
           \-1f.5

Here is lspci:

lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (re 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Expess Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Conroller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced HostController #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audo Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port5 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced HostController #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Cotroller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Cotroller (rev 05)
03:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)
04:00.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 1)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit thernet controller (rev 06)

---

### Post by Tamlynmac on 2013-04-21
> lorderico
I have an NVidia quadro 290 video card and I'm not 100% sure it works.  I  would like to use CUDA on it.  I am running  xubuntu 12.04.  Do you  think there is any way I am missing anything?

Take a look at this CUDA 5 toolkit download release note.
 [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads)

Notice that the last version of Ubuntu supported was 11.10.

Just a thought
Good Luck

---

### Post by lorderico on 2013-04-21
That shouldn't affect the video card though, right?  I haven't tried to installed CUDA yet.  Is there any way I can get useful info from dmesg?

Eric

---

