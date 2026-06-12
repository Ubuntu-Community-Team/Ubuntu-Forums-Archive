---
title: "Live CD boot stops at loading isofs"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by Jeremy Owens-Boggs on 2006-01-05
Good evening,
I am having a problem booting the Kubuntu Live CD.  When the Live cd is searching for hardware, it freezes at 92% trying to load isofs.  The machine is hp pavilion 750c.  I saw someone post this problem to the 5.04 forums, but there was no follow up answer.  If no-one knows how to solve this problem, what would be the next step in figuring out what is going wrong?

---

### Post by Jeremy Owens-Boggs on 2006-01-31
Additional Info, It turns out the computer was not hung, but the boot took at least three hours to complete.  Anybody have any idea what the problem might be?

---

### Post by breezyfox on 2006-01-31
[QUOTE=Jeremy Owens-Boggs]Good evening,
I am having a problem booting the Kubuntu Live CD.  When the Live cd is searching for hardware, it freezes at 92% trying to load isofs.  The machine is hp pavilion 750c.  [/QUOTE]

 hi 
I have the similar problem. i was unable to install ubuntu on my laptop having working cd rom. in the begening it starts booting from cd (recognised ofcourse) and goes through very fast a few steps like contry location etc etc. when it reaches hardware detection hangs up for ever at 86%.

I tried to boot through my old hoary cd, it works perfactly amazing, no problem at all. But i donot want to install Hoary. I am waiting next release of Ubuntu.
I could not find any solution on forum.I have Toshiba CR-Rom XM-7002Bc
which works faultlessly with any other programme and otherwise.

Do let me know if you find any solution.
bz

---

### Post by Someone else on 2006-02-06
[QUOTE=Jeremy Owens-Boggs]Good evening,
I am having a problem booting the Kubuntu Live CD.  When the Live cd is searching for hardware, it freezes at 92% trying to load isofs. [/QUOTE]

I have exactly the same problem with Ubuntu. And it's not only with the Live CD, it also happens with the Install CD. 

So I can't use Ubuntu at all :-(

Can someone help me?

---

### Post by Someone else on 2006-02-07
I've waited for over one hour and the installation finally proceeded. But now it stops while loading the HDD Partition Tool. I've waited another two hours, but nothing happens. So all I' have seen from ubuntu so far are the screenshots at the ubuntu website :-(

---

### Post by Ndlovu on 2006-02-07
Hi,

I'm not sure if it's exactly the same, but I suggest you check these posts to see if there's any resonance with your issues...

[http://www.ubuntuforums.org/showthread.php?t=105460](http://www.ubuntuforums.org/showthread.php?t=105460)
[http://www.ubuntuforums.org/showthread.php?t=76482](http://www.ubuntuforums.org/showthread.php?t=76482)

---

### Post by Jeremy Owens-Boggs on 2006-02-07
Thanks for the links, I will try them out in the next couple of days.  Where can I find more information on what each option does?

Boot: linux noapic (especially if you have a Pentium IV or newer Pentium class processor)
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by subslug on 2006-02-07
booting "linux irqpoll" solved my problem. The issue had to do with my SATA hard drive as far as I can tell. When I unplugged the hard drive it booted right up....of course that makes it hard to install Ubuntu. I didn't think a hard drive was required to live boot, shows what I know.

I was even able to install Ubuntu from an external usb cd drive. Now all I need to do is get my screen resolution right and I'm all set.

---

### Post by Ndlovu on 2006-02-08
According to this thread:
[http://www.ussg.iu.edu/hypermail/linux/kernel/0312.2/0347.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0312.2/0347.html)

It seems that the boot options are documented in the kernel source tarball, in the following directory:
linux-m.n.p/Documentation/kernel-parameters.txt

That probably means that you need to download the source package for your kernel (sudo apt-get source linux-image-m.n.p) and find the text file there. I checked it out and the relevant documentation there for the above options seem to be (there's nothing there for framebuffer and irqpoll):

        noapic          [SMP,APIC] Tells the kernel to not make use of any
                        IOAPICs that may be present in the system.

        acpi=           [HW,ACPI] Advanced Configuration and Power Interface
                        Format: { force | off | ht | strict }
                        force -- enable ACPI if default was off
                        off -- disable ACPI if default was on
                        noirq -- do not use ACPI for IRQ routing
                        ht -- run only enough ACPI to enable Hyper Threading
                        strict --  Be less tolerant of platforms that are not
                                strictly ACPI specification compliant.

                        See also Documentation/pm.txt, pci=noacpi

        acpi_irq_balance        [HW,ACPI] ACPI will balance active IRQs
                                default in APIC mode

        acpi_irq_nobalance      [HW,ACPI] ACPI will not move active IRQs (default)
                                default in PIC mode

        acpi_irq_pci=   [HW,ACPI] If irq_balance, Clear listed IRQs for use by PCI
                        Format: <irq>,<irq>...

        pci=option[,option...]          [PCI] various PCI subsystem options:
                off                     [IA-32] don't probe for the PCI bus
                bios                    [IA-32] force use of PCI BIOS, don't access
                                        the hardware directly. Use this if your machine
                                        has a non-standard PCI host bridge.
                nobios                  [IA-32] disallow use of PCI BIOS, only direct
                                        hardware access methods are allowed. Use this
                                        if you experience crashes upon bootup and you
                                        suspect they are caused by the BIOS.
                conf1                   [IA-32] Force use of PCI Configuration Mechanism 1.
                conf2                   [IA-32] Force use of PCI Configuration Mechanism 2.
                nosort                  [IA-32] Don't sort PCI devices according to
                                        order given by the PCI BIOS. This sorting is done
                                        to get a device order compatible with older kernels.
                biosirq                 [IA-32] Use PCI BIOS calls to get the interrupt
                                        routing table. These calls are known to be buggy
                                        on several machines and they hang the machine when used,
                                        but on other computers it's the only way to get the
                                        interrupt routing table. Try this option if the kernel
                                        is unable to allocate IRQs or discover secondary PCI
                                        buses on your motherboard.
                rom                     [IA-32] Assign address space to expansion ROMs.
                                        Use with caution as certain devices share address
                                        decoders between ROMs and other resources.
                irqmask=0xMMMM          [IA-32] Set a bit mask of IRQs allowed to be assigned
                                        automatically to PCI devices. You can make the kernel
                                        exclude IRQs of your ISA cards this way.
                lastbus=N               [IA-32] Scan all buses till bus #N. Can be useful
                                        if the kernel is unable to find your secondary buses
                                        and you want to tell it explicitly which ones they are.

                assign-busses           [IA-32] Always assign all PCI bus
                                        numbers ourselves, overriding
                                        whatever the firmware may have
                                        done.
                usepirqmask             [IA-32] Honor the possible IRQ mask
                                        stored in the BIOS $PIR table. This is
                                        needed on some systems with broken
                                        BIOSes, notably some HP Pavilion N5400
                                        and Omnibook XE3 notebooks. This will
                                        have no effect if ACPI IRQ routing is
                                        enabled.
                noacpi                  [IA-32] Do not use ACPI for IRQ routing
                                        or for PCI scanning.
                routeirq                Do IRQ routing for all PCI devices.
                                        This is normally done in pci_enable_device(),
                                        so this option is a temporary workaround
                                        for broken drivers that don't call it.

                firmware                [ARM] Do not re-enumerate the bus but
                                        instead just use the configuration
                                        from the bootloader. This is currently
                                        used on IXP2000 systems where the
                                        bus has to be configured a certain way
                                        for adjunct CPUs.

        nolapic         [IA-32,APIC] Do not enable or use the local APIC.

---

### Post by Ndlovu on 2006-02-08
It definitely seems to be a problem with how Ubuntu assigns interrupts (IRQs). I would guess that your external hard drive was being assigned an IRQ that was conflicting with some other device.

Good luck with the rest of your setup!

---

### Post by Someone else on 2006-02-11
I tried nearly everything mentioned above. But I still can't boot or install ubuntu. After spending several hours I finally gave up on it. Seems Linux is still for Geeks only.

I will try again maybe next year. In the meantime I do some productive stuff using Windows instead. 

Bye

:-(

---

### Post by Jeremy Owens-Boggs on 2006-02-12
Give puppy linux a shot, it works fine on the machine I am having ubuntu problems with, and it doesn't need much hard drive space, a good companion on a windows box:)

---

