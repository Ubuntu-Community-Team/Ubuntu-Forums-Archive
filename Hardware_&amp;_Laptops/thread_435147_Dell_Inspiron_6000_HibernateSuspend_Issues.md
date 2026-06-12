---
title: "Dell Inspiron 6000 Hibernate/Suspend Issues"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by ryodoan on 2007-05-06
When I first updated to Feisty Fawn the hibernate was working fine.  Then after some installations, and a few days I noticed that Hibernate was no longer functioning properly.

The first thing that happened was when I told it to hibernate the one day, a bunch of unfriendly white text showed up on the screen.  I just figured something went wrong and force shut it down.

Now when I tell it to hibernate the screen just goes black and a little white cursor blinks in the upper left hand corner of the screen and it just sits there.

I checked /var/log/messages and saw this:

> May  6 16:55:22 Caffeine-Linux gnome-power-manager: (vincenpt) Hibernating computer because the DBUS method Hibernate() was invoked
May  6 16:55:22 Caffeine-Linux kernel: [  619.192000] ADDRCONF(NETDEV_UP): eth1: link is not ready
May  6 16:55:23 Caffeine-Linux kernel: [  619.328000] pccard: card ejected from slot 0
May  6 16:55:23 Caffeine-Linux kernel: [  619.724000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
May  6 16:55:23 Caffeine-Linux kernel: [  620.120000] ACPI: PCI interrupt for device 0000:03:03.0 disabled

Also it has been about a week now since the problem surfaced and I cant remember everything that I did leading up to the problem.  I dont know if it matters but I have Compiz (desktop Effects) enabled, restricted Drivers for an x300 ATI mobility video card enabled, and my desktop session is Gnome-XGL.

Any suggestions? If you need more information, please tell me, I am pretty new to linux and still have not fully figured out how to trouble shoot my machine.

Thanks for any help.

---

### Post by ryodoan on 2007-05-18
Some further information I am not sure if I posted this, I have CPUfreq installed also, could that be causing the problem?

---

### Post by Parlay on 2007-05-30
I'm new to these forums and I am having similar problems.  The only reason I'm on these forums is to find a solution.  I'm using a Dell Inspiron 6000 with ubuntu 7.04 and hibernate/suspend will not work.  I'm going crazy over this.  I have tried everything I can think of and I have used all the resources at my disposal.  At this point I'm not even sure if this laptop will ever hibernate.  It worked with a fresh Ubuntu install once, and hasn't worked again.  If anyone, anyone at all can help I'd be so elated.  I've been using linux for a few months now, and this is one heck of a stumbling block.

-Parlay

---

### Post by nicktmro on 2007-07-03
I used to have similiar issues but I managed to fix them thanks to a little googling.

What I would suggest is to have a look at this blog and see if the reason you can't suspend to disk (hibernate) has to do with the swap partition: [http://tmro.blogspot.com/2007/07/my-dell-inspiron-6400-running-ubuntu.html]("http://tmro.blogspot.com/2007/07/my-dell-inspiron-6400-running-ubuntu.html")

The other thing worth looking at is the ubuntu laptop testing wiki pages and see if they help: [https://wiki.ubuntu.com/LaptopTestingTeam/Dell]("https://wiki.ubuntu.com/LaptopTestingTeam/Dell")

---

### Post by ryodoan on 2007-07-05
the first link did not help me. I am thinking about just reinstalling ubuntu on my laptop.  I think that I might have messed up the hibernate somehow when I installed cpufreq.

---

### Post by AncientPC on 2007-07-05
I'm having the same problem (also an Inspiron 6000, Pentium M 1.6GHz), here's the relevant section from my logs:
```
Jul  5 12:25:56 Ubuntu gnome-power-manager: (username) Hibernating computer because the DBUS method Hibernate() was invoked
Jul  5 12:25:58 Ubuntu kernel: [15332.580000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul  5 12:25:58 Ubuntu kernel: [15332.916000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Jul  5 12:25:59 Ubuntu kernel: [15333.544000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
Jul  5 12:26:11 Ubuntu kernel: [15336.152000] Disabling non-boot CPUs ...
Jul  5 12:26:16 Ubuntu kernel: [15336.152000] Stopping tasks ... done.
Jul  5 12:26:16 Ubuntu kernel: [15336.524000] ShrinUbuntug memory...  ^H-^H\^H|^H/^H-^H\^H|^H/^Hdone (96040 pages freed)
Jul  5 12:26:16 Ubuntu kernel: [15343.068000] Freed 384160 kbytes in 6.64 seconds (57.85 MB/s)
Jul  5 12:26:16 Ubuntu kernel: [15343.068000] Suspending console(s)
Jul  5 12:26:16 Ubuntu kernel: [15343.796000] ACPI: PCI interrupt for device 0000:03:01.2 disabled
Jul  5 12:26:16 Ubuntu kernel: [15343.812000] ohci1394 does not fully support suspend and resume yet
Jul  5 12:26:17 Ubuntu kernel: [15343.812000] ieee1394: hpsb_bus_reset called while bus reset already in progress
Jul  5 12:26:17 Ubuntu kernel: [15343.828000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Jul  5 12:26:17 Ubuntu kernel: [15343.828000] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
Jul  5 12:26:17 Ubuntu kernel: [15343.828000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Jul  5 12:26:17 Ubuntu kernel: [15343.844000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Jul  5 12:26:17 Ubuntu kernel: [15343.844000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Jul  5 12:26:17 Ubuntu kernel: [15343.844000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Jul  5 12:26:17 Ubuntu kernel: [15343.844000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Jul  5 12:26:17 Ubuntu kernel: [15343.844000] swsusp: critical section: 
Jul  5 12:26:17 Ubuntu kernel: [15343.844000] swsusp: Need to copy 93805 pages
Jul  5 12:26:17 Ubuntu kernel: [15343.844000] swsusp: critical section/: done (93805 pages copied)
Jul  5 12:26:17 Ubuntu kernel: [15345.848000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  5 12:26:17 Ubuntu kernel: [15345.848000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Jul  5 12:26:17 Ubuntu kernel: [15345.848000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Jul  5 12:26:17 Ubuntu kernel: [15345.848000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Jul  5 12:26:17 Ubuntu kernel: [15345.864000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Jul  5 12:26:17 Ubuntu kernel: [15345.864000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
Jul  5 12:26:17 Ubuntu kernel: [15345.864000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul  5 12:26:17 Ubuntu kernel: [15346.868000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 18
Jul  5 12:26:17 Ubuntu kernel: [15346.868000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  5 12:26:17 Ubuntu kernel: [15346.908000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfcfc800-dfcfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jul  5 12:26:17 Ubuntu kernel: [15346.928000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 17 (level, low) -> IRQ 18
Jul  5 12:26:17 Ubuntu kernel: [15346.928000] pnp: Device 00:04 does not support activation.
Jul  5 12:26:17 Ubuntu kernel: [15346.928000] pnp: Device 00:05 does not support activation.
Jul  5 12:26:17 Ubuntu kernel: [15346.988000] Restarting tasks ... done.
Jul  5 12:26:17 Ubuntu kernel: [15347.040000] Enabling non-boot CPUs ...
Jul  5 12:26:17 Ubuntu kernel: [15347.312000] input: PS/2 Mouse as /class/input/input18
Jul  5 12:26:17 Ubuntu kernel: [15347.332000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input19
Jul  5 12:26:17 Ubuntu kernel: [15348.048000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
Jul  5 12:26:17 Ubuntu kernel: [15348.056000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
Jul  5 12:26:17 Ubuntu kernel: [15348.056000] ata1.00: configured for UDMA/100
Jul  5 12:26:17 Ubuntu kernel: [15348.056000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
Jul  5 12:26:17 Ubuntu kernel: [15348.088000] sda: Write Protect is off
Jul  5 12:26:17 Ubuntu kernel: [15348.092000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  5 12:26:17 Ubuntu kernel: [15348.432000] ata2.00: configured for UDMA/33
Jul  5 12:26:22 Ubuntu gnome-power-manager: (username) DBUS timed out, but recovering
Jul  5 12:26:23 Ubuntu gnome-power-manager: (username) Resuming computerp
```

I dual-boot and WinXP Pro hibernates just fine, so I'm not sure why it says:
Jul  5 12:26:16 Ubuntu kernel: [15343.812000] ohci1394 does not fully support suspend and resume yet
Jul  5 12:26:17 Ubuntu kernel: [15346.928000] pnp: Device 00:04 does not support activation.
Jul  5 12:26:17 Ubuntu kernel: [15346.928000] pnp: Device 00:05 does not support activation.

---

