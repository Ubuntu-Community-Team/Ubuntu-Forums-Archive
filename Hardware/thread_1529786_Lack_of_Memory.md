---
title: "Lack of Memory?"
date: 2010-07-12
forum: Hardware
---

### Post by jncocontrol on 2010-07-12
Hello, I'm running a 5GIG of memory computer, It even says it in my BIO's, So, I'm getting the idea that nothing should be wrong with the RAM itself.
But, When i go into Ubuntu's "System Monitor" and goto the Monitor Tab at the top, It only Shows 3 GIG's of memory, And Further when i goto "System Processes" tab in System Monitor, It shows only 3GIG's of ram.

Now I'm not trying to sound like "perfectionist" here. But this kinda Rub's me the wrong way, And would like to Ubuntu to show the 5 gigs that i have, Or at least 4.9 GIG. I'm not gonna be too worried about the .1 loss.

I even ran the "recovery Mode" in the grub menu. That didn't even work.
Also, I'm running Ubuntu 10.4 incase it means anything.

EDIT: Though, I guess i should run the "Memory Test" in the Grub menu before i complain :p

---

### Post by Yellow Pasque on 2010-07-12
Are you running 64-bit? Is your BIOS updated? Output of:
```
uname -a
dmesg | grep mem
```

---

### Post by brokenromeo on 2010-07-12
I ran into this issue, was forced to run 32 bit because of cisco vpn capability, go to the below link...helped me.

[https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

---

### Post by jncocontrol on 2010-07-13
> **Temüjin said:**
> Are you running 64-bit? Is your BIOS updated? Output of:
```
uname -a
dmesg | grep mem
```

32bit, and yes

---

### Post by AltomineUK on 2010-07-13
> **jncocontrol said:**
> 32bit, and yes

32-bit cannot map memory more than 4GB max. Realistically they only go upto 2.5GB-3GB.

---

### Post by jncocontrol on 2010-07-13
> **AltomineUK said:**
> 32-bit cannot map memory more than 4GB max. Realistically they only go upto 2.5GB-3GB.

That can't be right.
It was showing it previously on my 32bit partition.
[IMG]http://i49.photobucket.com/albums/f270/Cyrax1/Screenshot.png[/IMG]
I had to format it using the same installation CD i did with the last one.

---

### Post by Yellow Pasque on 2010-07-13
Are you still running the pae kernel? (you were in the screenshot)
Post the output of:
```
uname -a
dmesg | grep mem
```
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by jncocontrol on 2010-07-14
```
Linux Brad 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

``````
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000] free_area_init_node: node 0, pgdat c0798760, node_mem_map c107b000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   HighMem zone: 4367 pages used for memmap
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Memory: 3084396k/3144704k available (4676k kernel code, 56896k reserved, 2118k data, 660k init, 2233556k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.008196] Initializing cgroup subsys memory
[    0.236589] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.241867] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.241870] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.241893] system 00:08: iomem range 0xffe00000-0xffffffff has been reserved
[    0.241896] system 00:08: iomem range 0xfed30000-0xfed3ffff has been reserved
[    0.241900] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.241917] system 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.241920] system 00:0a: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.241923] system 00:0a: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.241927] system 00:0a: iomem range 0xff000000-0xffffffff could not be reserved
[    0.276908] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.276914] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xd30fffff]
[    0.276920] pci_bus 0000:02: resource 1 mem: [0xd3500000-0xd36fffff]
[    0.276923] pci_bus 0000:02: resource 2 pref mem [0xd3700000-0xd38fffff]
[    0.276928] pci_bus 0000:03: resource 1 mem: [0xd3300000-0xd33fffff]
[    0.276931] pci_bus 0000:03: resource 2 pref mem [0xd3900000-0xd3afffff]
[    0.276936] pci_bus 0000:04: resource 1 mem: [0xd3200000-0xd32fffff]
[    0.276939] pci_bus 0000:04: resource 2 pref mem [0xd3b00000-0xd3cfffff]
[    0.276942] pci_bus 0000:05: resource 1 mem: [0xd3100000-0xd31fffff]
[    0.276947] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.380558] Freeing initrd memory: 7783k freed
[    3.480439] Scanning for low memory corruption every 60 seconds
[    3.491365] highmem bounce pool size: 64 pages
[    3.512901] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xd3425400
[    3.532186] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd3425000
[   14.381005] Freeing unused kernel memory: 660k freed

```

---

### Post by AltomineUK on 2010-07-14
> **jncocontrol said:**
> That can't be right.
It was showing it previously on my 32bit partition.
[IMG]http://i49.photobucket.com/albums/f270/Cyrax1/Screenshot.png[/IMG]
I had to format it using the same installation CD i did with the last one.

2 to the power of 32 is = **4294967296 bits**.

This equates to **4096 MB (roughly 4GB)**.

So technically speaking the 32-bit OS will not map more than the  aforementioned RAM memory size. What is your processor are you running this 32-bit OS on?

Nice desktop BTW :D

---

### Post by AltomineUK on 2010-07-14
> **jncocontrol said:**
> ```
Linux Brad 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

``````
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000] free_area_init_node: node 0, pgdat c0798760, node_mem_map c107b000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   HighMem zone: 4367 pages used for memmap
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Memory: 3084396k/3144704k available (4676k kernel code, 56896k reserved, 2118k data, 660k init, 2233556k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.008196] Initializing cgroup subsys memory
[    0.236589] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.241867] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.241870] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.241893] system 00:08: iomem range 0xffe00000-0xffffffff has been reserved
[    0.241896] system 00:08: iomem range 0xfed30000-0xfed3ffff has been reserved
[    0.241900] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.241917] system 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.241920] system 00:0a: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.241923] system 00:0a: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.241927] system 00:0a: iomem range 0xff000000-0xffffffff could not be reserved
[    0.276908] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.276914] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xd30fffff]
[    0.276920] pci_bus 0000:02: resource 1 mem: [0xd3500000-0xd36fffff]
[    0.276923] pci_bus 0000:02: resource 2 pref mem [0xd3700000-0xd38fffff]
[    0.276928] pci_bus 0000:03: resource 1 mem: [0xd3300000-0xd33fffff]
[    0.276931] pci_bus 0000:03: resource 2 pref mem [0xd3900000-0xd3afffff]
[    0.276936] pci_bus 0000:04: resource 1 mem: [0xd3200000-0xd32fffff]
[    0.276939] pci_bus 0000:04: resource 2 pref mem [0xd3b00000-0xd3cfffff]
[    0.276942] pci_bus 0000:05: resource 1 mem: [0xd3100000-0xd31fffff]
[    0.276947] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.380558] Freeing initrd memory: 7783k freed
[    3.480439] Scanning for low memory corruption every 60 seconds
[    3.491365] highmem bounce pool size: 64 pages
[    3.512901] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xd3425400
[    3.532186] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd3425000
[   14.381005] Freeing unused kernel memory: 660k freed

```

Looking at the output, your CPU is mapping from 0000000 - ffffffff suggesting that it's mapping 0MB to 4096MB as it should do....again what is your processor and what is your RAM layout...if you had posted this info earlier...my bad =(

---

### Post by jncocontrol on 2010-07-14
> **AltomineUK said:**
> 2 to the power of 32 is = **4294967296 bits**.

This equates to **4096 MB (roughly 4GB)**.

So technically speaking the 32-bit OS will not map more than the  aforementioned RAM memory size. What is your processor are you running this 32-bit OS on?

Nice desktop BTW :D

It's a Intel duo core 2 processor

and thank you :D

> processor and what is your RAM layout...if you had posted this info earlier...my bad =(
Processor above
My Ram Layout?
Slot 1 and 2 are 2 512MB's
3 and 4 are 2 2 Gig's

---

### Post by Yellow Pasque on 2010-07-14
You need to install the PAE kernel: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by AltomineUK on 2010-07-15
Hmmm that would explain all those resource locations..... as I said before a 32-bit will only use (in extreme cases) upto 4GB. It might display more that 4GB, but it won't make good use of all that extra RAM. A 64-bit version will do it some justice and your processor should support it quite nicely (although becareful of the 64 bit flash...it's only available from Adobe Labs)

---

### Post by cascade9 on 2010-07-15
> **AltomineUK said:**
> Hmmm that would explain all those resource locations..... as I said before a 32-bit will only use (in extreme cases) upto 4GB. It might display more that 4GB, but it won't make good use of all that extra RAM. A 64-bit version will do it some justice and your processor should support it quite nicely (although becareful of the 64 bit flash...it's only available from Adobe Labs)

No, PAE CAN use more than 4GB of RAM. IIRC you cant use more than 4GB for any single program, but it will see and use 4GB+.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

*edit- if you had actually checked the link that Temujin posted, you wouldhave known that- 

>  [Physical Address Extension]("http://en.wikipedia.org/wiki/Physical_Address_Extension") is a technology which allows 32 bit operating systems to use up to 64 Gb of memory (RAM), something which is normally achieved by switching to a 64 bit system. PAE is supported on the majority of computers today and it is an easy procedure to enable it in Ubuntu, if it is not already. 


[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by AltomineUK on 2010-07-15
ok, that's a decent, temporary solution.

@jncocontrol If the CPU supports it (which it does) and you are not bothered about RAM instances then PAE works as well.

---

