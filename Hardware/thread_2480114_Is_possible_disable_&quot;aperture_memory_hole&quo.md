---
title: "Is possible disable &quot;aperture memory hole&quot; (AGP aperture) if using PCI-E video card ?"
date: 2022-10-19
forum: Hardware
---

### Post by aug7744 on 2022-10-19
Hello.
Mainboard only have PCI-E slot.
In OS starting log

[    0.048774] kernel: AGP: Checking aperture...
[    0.059086] kernel: AGP: No AGP bridge found
[    0.059088] kernel: AGP: Node 0: aperture [bus addr 0x00000000-0x01ffffff] (32MB)
[    0.059090] kernel: AGP: Your BIOS doesn't leave an aperture memory hole
[    0.059091] kernel: AGP: Please enable the IOMMU option in the BIOS setup
[    0.059092] kernel: AGP: This costs you 64MB of RAM
[    0.059094] kernel: AGP: Mapping aperture over RAM [mem 0xd8000000-0xdbffffff] (65536KB)

If using an PCI-E video card need "aperture memory hole" ?
If not as disable it ?

Thanks for reading.

---

### Post by #&amp;thj^% on 2022-10-19
Please include this:
```
sudo cat /proc/mtrr
```
Using code tags for the return paste.

---

### Post by aug7744 on 2022-10-19
Thanks for replying me.
I not understand if really is being done an agp memory allocation in an PCI-E video card.
I only want understand if is being used memory for an resource not being used in an machine not having AGP slot and disabling that module too.
However if that module is also used for PCI-E not is good disable it.

sudo cat /proc/mtrr

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  512MB, count=1: write-back

---

### Post by #&amp;thj^% on 2022-10-19
That Looks Ok to me:
```
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-back
reg03: base=0x0ff000000 ( 4080MB), size=   16MB, count=1: write-protect


```

If nothing is wrong don't fix this one, we can get over zealous and do the exact opposite of what's intended.
Dual Graphics on this sytem>>AMDGPU && Nvidia.
```
cat  /proc/iomem
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
  00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : PCI Bus 0000:00
00000000-00000000 : System ROM
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : ACPI Non-volatile Storage
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : System RAM
00000000-00000000 : Unknown E820 type
00000000-00000000 : Reserved
  00000000-00000000 : MSFT0101:00
    00000000-00000000 : MSFT0101:00
  00000000-00000000 : MSFT0101:00
    00000000-00000000 : MSFT0101:00
00000000-00000000 : ACPI Non-volatile Storage
  00000000-00000000 : USBC000:00
00000000-00000000 : ACPI Tables
00000000-00000000 : System RAM
00000000-00000000 : Reserved
00000000-00000000 : RAM buffer
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : PCI Bus 0000:01
    00000000-00000000 : 0000:01:00.0
      00000000-00000000 : nvidia
    00000000-00000000 : 0000:01:00.1
      00000000-00000000 : ICH HD audio
    00000000-00000000 : 0000:01:00.0
  00000000-00000000 : PCI Bus 0000:06
    00000000-00000000 : 0000:06:00.1
      00000000-00000000 : ahci
    00000000-00000000 : 0000:06:00.0
      00000000-00000000 : ahci
  00000000-00000000 : PCI Bus 0000:05
    00000000-00000000 : 0000:05:00.4
      00000000-00000000 : xhci-hcd
    00000000-00000000 : 0000:05:00.3
      00000000-00000000 : xhci-hcd
    00000000-00000000 : 0000:05:00.2
      00000000-00000000 : ccp
    00000000-00000000 : 0000:05:00.5
    00000000-00000000 : 0000:05:00.6
      00000000-00000000 : ICH HD audio
    00000000-00000000 : 0000:05:00.2
      00000000-00000000 : ccp
  00000000-00000000 : PCI Bus 0000:04
    00000000-00000000 : 0000:04:00.0
      00000000-00000000 : iwlwifi
  00000000-00000000 : PCI Bus 0000:03
    00000000-00000000 : 0000:03:00.0
    00000000-00000000 : 0000:03:00.0
      00000000-00000000 : r8169
  00000000-00000000 : PCI Bus 0000:02
    00000000-00000000 : 0000:02:00.0
      00000000-00000000 : nvme
00000000-00000000 : PCI MMCONFIG 0000 [bus 00-3f]
  00000000-00000000 : Reserved
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : Reserved
    00000000-00000000 : pnp 00:00
      00000000-00000000 : MSFT0101:00
  00000000-00000000 : SB800 TCO
  00000000-00000000 : Reserved
    00000000-00000000 : IOAPIC 0
  00000000-00000000 : IOAPIC 1
  00000000-00000000 : Reserved
  00000000-00000000 : HPET 0
    00000000-00000000 : PNP0103:00
00000000-00000000 : Reserved
00000000-00000000 : AMDI0030:00
00000000-00000000 : AMDI0030:00
  00000000-00000000 : AMDI0030:00 AMDI0030:00
00000000-00000000 : AMDI0010:03
  00000000-00000000 : AMDI0010:03 AMDI0010:03
00000000-00000000 : Local APIC
  00000000-00000000 : Reserved
    00000000-00000000 : pnp 00:00
00000000-00000000 : Reserved
00000000-00000000 : System RAM
  00000000-00000000 : Kernel code
  00000000-00000000 : Kernel rodata
  00000000-00000000 : Kernel data
  00000000-00000000 : Kernel bss
00000000-00000000 : Reserved
00000000-00000000 : PCI Bus 0000:00
  00000000-00000000 : PCI Bus 0000:01
    00000000-00000000 : 0000:01:00.0
      00000000-00000000 : efifb
    00000000-00000000 : 0000:01:00.0

```

You can see mine is disabled, If you DO NOT have a IMOU parameter in your /etc/default/grub **don't add it**, just leave this sleeping dog lie...;)
I'll add this if helps to understand the above:
```
sudo dmesg | grep iommu
[    0.284347] iommu: Default domain type: Translated 
[    0.284348] iommu: DMA domain TLB invalidation policy: lazy mode 


```

---

### Post by Yellow Pasque on 2022-10-19
> **aug7744 said:**
> Hello.
Mainboard only have PCI-E slot.
In OS starting log

[    0.048774] kernel: AGP: Checking aperture...
[    0.059086] kernel: AGP: No AGP bridge found
[    0.059088] kernel: AGP: Node 0: aperture [bus addr 0x00000000-0x01ffffff] (32MB)
[    0.059090] kernel: AGP: Your BIOS doesn't leave an aperture memory hole
[    0.059091] kernel: AGP: Please enable the IOMMU option in the BIOS setup
[    0.059092] kernel: AGP: This costs you 64MB of RAM
[    0.059094] kernel: AGP: Mapping aperture over RAM [mem 0xd8000000-0xdbffffff] (65536KB)

If using an PCI-E video card need "aperture memory hole" ?
If not as disable it ?

Thanks for reading.

And yet, you don't mention what motherboard you're using.

---

### Post by Yellow Pasque on 2022-10-21
Maybe this will help:
[https://www.kernel.org/doc/html/latest/x86/x86_64/boot-options.html?highlight=noagp](https://www.kernel.org/doc/html/latest/x86/x86_64/boot-options.html?highlight=noagp)

---

### Post by Yellow Pasque on 2022-10-22
> **Yellow Pasque said:**
> Maybe this will help:
[https://www.kernel.org/doc/html/latest/x86/x86_64/boot-options.html?highlight=noagp](https://www.kernel.org/doc/html/latest/x86/x86_64/boot-options.html?highlight=noagp)

Sorry, the link didn't take it to exactly what I was pointing to. You should try booting with iommu=noagp kernel parameter. Let us know if you need help with that.

---

