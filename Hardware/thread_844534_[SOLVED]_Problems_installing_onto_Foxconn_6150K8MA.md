---
title: "[SOLVED] Problems installing onto Foxconn 6150K8MA-EKRS board."
date: 2008-06-29
forum: Hardware
---

### Post by Killer_B on 2008-06-29
Hi,

I was looking to install ubuntu onto this system:

Foxconn 6150K8MA-EKRS motherboard
AMD Opteron 165 CPU
1gb pc3200
1x80gb Maxtor PATA HDD
3x320gb Seagate SATA HDD
onboard video, network

And of course, there's the problem with getting kernel panics due to problems with apic and acpi in the kernel itself.

I have already turned ACPI off in the bios, I can't seem to turn APIC off, though...It's greyed out.

In this thread, 

[http://ubuntuforums.org/showpost.php?p=3392781&postcount=6](http://ubuntuforums.org/showpost.php?p=3392781&postcount=6)

The poster had stated he had to turn both APIC and ACPI off in the bios, and then use specific kernel flags upon attempting to install: 

noapic noacpi nolapic acpi=off irqpoll

I still seem to be having problems attempting to install any version of ubuntu on this board...Might the problem be that I'm using a dual-core cpu?

If so, I suppose that I could move back to a single-core cpu instead, and try again.

Am I on the right track here?

Thanks.

---

### Post by Killer_B on 2008-06-29
Installing a single-core opteron has allowed me to turn apic off in the bios.

I'm still no closer to being allowed to install ubuntu, or any other variety of linux for that matter.

Is there something that I'm missing still?

Thanks again.

---

### Post by Killer_B on 2008-06-30
Is this motherboard a lost cause? 

What might be a good alternative?

---

### Post by Killer_B on 2008-06-30
It appears that a stick of memory was giving errors when running memtest.

commandline Ubuntu 7.10 installs as normal.

Will now attempt to get a gui loaded.

Looks as though this issue's solved.

---

