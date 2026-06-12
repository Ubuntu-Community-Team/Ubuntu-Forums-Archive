---
title: "Getting timeout errors on ATA4, but no SATA device there?"
date: 2018-10-10
forum: Hardware
---

### Post by fovea1959 on 2018-10-10
Have a Lenovo T420 laptop here (got it used), put a Crucial MX500 SSD in it, reinstalled Windows 7, and put Ubuntu 18.04 on it.

I noticed today that I'm getting these when copying files from a thumb drive of dubious quality, with varying frequency (sometimes multiple times per second):
```

[   19.956422] ata4: exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen
[   19.956426] ata4: irq_stat 0x00000040, connection status changed
[   19.956430] ata4: SError: { CommWake DevExch }
[   19.956435] ata4: hard resetting link
[   20.672093] ata4: SATA link down (SStatus 0 SControl 300)
[   20.672103] ata4: EH complete
```

Concerned the heck out of me, until I realized that neither the SSD not the onboard DVDROM are on ATA4...

```

[    1.695071] ata1.00: ATA-10: CT500MX500SSD1, M3CR020, max UDMA/133
...
[    2.018746] ata2.00: ATAPI: HL-DT-ST DVDRAM GT50N, LT20, max UDMA/33
```
How do I determine where these are coming from? I get a set of these at boot with no thumb drive plugged in....

---

### Post by SeijiSensei on 2018-10-10
Look in the BIOS.  Any nonexistent devices referenced there?

Also you can run "sudo lshw" for a complete hardware census.  Do you see an ata4?

---

### Post by fovea1959 on 2018-10-14
I could find no option to show connected SATA devices in the BIOS. Closest I could get was for setting up boot order; it showed the CT500MX500SSD1 connect to SATA0, along with options to disable some other ATA disk drives for boot.

lshw does not show any deviuces named ata* at all. It does show the controller:

```
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:24 ioport:60a8(size=8) ioport:60bc(size=4) ioport:60a0(size=8) ioport:60b8(size=4) ioport:6060(size=32) memory:f3a28000-f3a287ff
```

It shows the hard disk and DVD as connected to emulated scsi0 and scsi1 devices.

The ata4 is reporting as being within the addresses that lshw shows as used by the controller:
```
[    1.250737] ata4: SATA max UDMA/133 abar m2048@0xf3a28000 port 0xf3a28280 irq 24
```

I guess it's just an unused port on the controller being weird; funny that it acts up intermittently....

---

### Post by Yellow Pasque on 2018-10-15
> driver=ahci

Have you tried changing to IDE mode in BIOS to see if anything changes?

---

