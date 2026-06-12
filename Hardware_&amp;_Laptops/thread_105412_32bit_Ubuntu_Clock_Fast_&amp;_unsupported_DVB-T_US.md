---
title: "32bit Ubuntu Clock Fast &amp; unsupported DVB-T USB Adapter"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by sfabel on 2005-12-18
Hi everybody,

two things that concern me, as you might be able to decipher from the subject of this thread.

My system is a HP X2 dual-core AMD64 system, I am running the 32bit Version of Kubuntu 5.10. I am running kernel version 2.6.12-10-k7-smp.

I seem to have the "double speed clock" problem. When I open up the system monitor, both processors seem to run at top speeds. I also have an ATI motherboard although I don't know the exact type:

```

stephan@gemini:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 10)

```

In /var/log/syslog, the following lines seem to be connected to the fast playback of MP3's, etc.:

```

18.12.2005 15:01:08	localhost	kernel	[4310406.366000] APIC error on CPU0: 40(40)
18.12.2005 15:01:08	localhost	kernel	[4310406.366000] APIC error on CPU1: 40(40)
...
18.12.2005 17:12:29	localhost	kernel	[4294671.605000] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
18.12.2005 17:12:29	localhost	kernel	[4294671.605000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
18.12.2005 17:12:29	localhost	kernel	[4294671.605000] PCI: Using ACPI for IRQ routing

```

Several questions here. Where should I enter the suggested "pci=routeirq"? I have tried passing a kernel parameter called "notsc" to the kernel, but alas, this didn't have any effect. These are the entries concerning the TSC settings, I guess:

```

18.12.2005 17:12:29	localhost	kernel	[4294671.491000] checking TSC synchronization across 2 CPUs: 
18.12.2005 17:12:29	localhost	kernel	[4294671.491000] CPU#0 had 0 usecs TSC skew, fixed it up.
18.12.2005 17:12:29	localhost	kernel	[4294671.491000] CPU#1 had 0 usecs TSC skew, fixed it up.

```

I also get loads of these entries:

```

18.12.2005 17:26:25	localhost	kernel	[4295559.700000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```

So, I've tried out the noapic, no_timer_check, noacpi and notsc kernel parameters, to no avail. I don't know if any of the above messages concern my problem, if you know what they mean, please share your wisdom. :)

In any case, this bug seems to be fixed in some later kernel release. Is this true? If so, is there maybe a kernel patch to fix this problem?

I need to re-compile my kernel anyways, because I would like to use a DVB-T USB adapter I've bought which is supported by Linux, but requiring kernel 2.6.12. Great, I thought, but I had to find out that I'd need a kernel patch for that release, and that subsequent releases of the kernel (2.6.13 and up) have that patch already included.

The adapter is the DVB-T EuroMini 100 (with the 7045A chipset, if that matters).

So far I have been unable to find the required patch for that DVB-T adapter, and as well, any patch that would fix the double-speed clock problem. I know I can re-compile my kernel under Ubuntu with the official patches, there seems to be a HOWTO somewhere on the wiki, so I should be able to include both of these patches as well, right?

Does anyone know anything about this?

Thanks,
Stephan

---

