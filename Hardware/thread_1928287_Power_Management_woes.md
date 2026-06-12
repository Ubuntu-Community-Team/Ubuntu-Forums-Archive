---
title: "Power Management woes"
date: 2012-02-19
forum: Hardware
---

### Post by freakalad on 2012-02-19
I'm sure this has come up numerous times, but I've still not found a good reference/resolution.

I've got a HP Mini 110:
`lshw`:
```

    description: Notebook
    product: HP Mini 110-1000
    vendor: Hewlett-Packard
    version: 03A8100000000000100300000
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=1
  *-core
       description: Motherboard
       product: 308F
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 02.0B
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 308F0 Ver. F.07 (06/18/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification

```

Running stock old Gnome desktop (not the new gnome shell, not unity) on 10.04.4 LTS (will upgrade to new LTS when released)

Unfortunately power-management is extremely poor.

The power-management profile is set up to suspend the device when the lid is closed (on wired or wireless networking).
Unfortunately this no loger works, and the machine continues running when I place it in my carry-bag. It does not suspend when I set it to suspend manually either.

In the past it worked OK, but it's stopped working correctly for a while now, and I have no idea why that would be.

Can anyone please provide me with some insight or assistance, please?

---

### Post by freakalad on 2012-02-19
on a hunch I installed kernel 3.n

It seems to work, although it's still too early to say whether or not it's actually resolved the issue.

---

### Post by freakalad on 2012-02-21
Standby works, but wireless is broken now...

---

