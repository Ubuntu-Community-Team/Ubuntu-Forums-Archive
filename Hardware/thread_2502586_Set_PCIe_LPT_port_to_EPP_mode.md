---
title: "Set PCIe LPT port to EPP mode"
date: 2024-11-20
forum: Hardware
---

### Post by peyre on 2024-11-20
I just upgraded from a computer that had old legacy adapters, including a built-in LPT port.  The device I'm using (an old 250MB Zip drive! Love it) performed best in EPP mode; it ran at about 300-350kb/s, while in SPP or ECP mode it runs at 120kb/s.  I plugged a PCIe LPT card into this new machine, added **imm** to /etc/modules, fired up the computer, and the Zip drive works!  But it's slow, so must be in SPP or ECP mode.

The manufacturer does include a PCIConfigure.exe tool, but it's useless, and doesn't even seem to have a selection to change its mode.  I've tried booting with a Windows live disk, installing the device, then running the tool, but that doesn't work really any better.

I've found instructions online for changing the settings via halcmd, but that doesn't seem to be a thing anymore in modern distros.

If it helps, this is what dmesg returns for the parport:

```
[    4.604632] parport0: PC-style at 0xc100, irq 16 [PCSPP,TRISTATE]
[    4.606550] parport0: Device ID was 64 bytes while device told it would be 63 bytes
[    4.608945] parport0 (addr 0): SCSI adapter, IMG VP1
[    4.658264] lp0: using parport0 (interrupt-driven).

```

I suppose PC-style and PCSPP mean it's running in SPP mode, fwiw.

---

