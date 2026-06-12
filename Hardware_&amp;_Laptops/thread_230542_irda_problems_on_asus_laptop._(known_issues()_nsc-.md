---
title: "irda problems on asus laptop. (known issues(?) nsc-ircc)"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by zenek on 2006-08-06
Hello. I'm using kubuntu, but I believe the same problem applies to ubuntu.

I have infrared on my asus m6 laptop. # cat /sys/bus/pnp/devices/00\:07/id
NSC6001

(this is probably it).

# modprobe nsc-ircc
FATAL: Error inserting nsc_ircc (/lib/modules/2.6.17.7/kernel/drivers/net/irda/nsc-ircc.ko): No such device


[17180475.996000] pnp: Device 00:07 activated.
[17180475.996000] nsc-ircc, chip->init
[17180475.996000] nsc-ircc, Found chip at base=0x02e
[17180475.996000] nsc-ircc, Wrong chip version ff
[17180475.996000] nsc-ircc, Found chip at base=0x02e
[17180475.996000] nsc-ircc, Wrong chip version 00
[17180476.004000] pnp: Device 00:07 disabled.

I've googles and read lots of informations on concerning this subject and problems. Tried everything...
Could anyone help?
(this could also be a kernel issue)

oh, tried it on distro kernel (2.6.12) and my own 2.6.17.7 (almost the same options, but it shutdowns and reboots ok, as distro kernel has problems with it)

PS. I also tried one (well, actually, not one) hack found on google:

install nsc-ircc /bin/setserial /dev/ttyS1 uart none port 0 irq 0; /sbin/modprobe --ignore-install nsc-irccalias irda0 nsc-ircc options nsc-ircc dongle_id=0x09 io=0x2f8 irq=3dma=3

---

### Post by woody_green on 2006-09-16
I have similar problems. I'm using an Asus L300H, and when I run dmesg, it says that it found a dongle named HP HSDL-110/HSDL-2100. I was just wondering why it would specify a dongle when in fact the IR device is built-in. 

I've tried to read, comprehend and understand several different documentations about the Linux/IrDA Project and I haven't made the IR port work yet. Maybe I'll just exert a bit more effort to at least get it working. Ah, the challenges of Linux. ](*,)

If I get this task done, I'll be ditching my Windows partition. ;)

---

### Post by lunatc on 2006-10-03
Similar problems on an Asus A6VC + irda (pnp: Device 00:07 disabled), and I've solved it passing the boot paramenter "**pnpacpi=off**" to the kernel (on grub)

It seems a problem related to ACPI/pnp BIOS.

IrDA working after that :)

---

### Post by Nonno Bassotto on 2006-10-04
And what did you lose in change?

---

### Post by lunatc on 2006-10-05
Nothing for the moment! :) 
Seeing kernel logs acpi is still used for power management and the like. So keys, batt.. etc is working correcty.

---

### Post by leeyee on 2007-02-17
> **lunatc said:**
> Similar problems on an Asus A6VC + irda (pnp: Device 00:07 disabled), and I've solved it passing the boot paramenter "**pnpacpi=off**" to the kernel (on grub)

It seems a problem related to ACPI/pnp BIOS.

IrDA working after that :)
Yeah, followed your idea, IrDA works again, although I'm not sure what is "pnpacpi=off" working for?

---

