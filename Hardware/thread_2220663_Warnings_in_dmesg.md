---
title: "Warnings in dmesg"
date: 2014-04-28
forum: Hardware
---

### Post by erdosain92 on 2014-04-28
Hello.
Can someone tell what i should do???

```
ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   36.084937] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.084941] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   36.084945] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.084946] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   36.084949] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.084951] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   36.084954] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```

```
systemd-hostnamed[4168]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  499.122118] systemd-hostnamed[16293]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

```
 WARNING: CPU: 1 PID: 9446 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_uncore.c:125 gen6_gt_check_fifodbg.isra.9+0x38/0x50 [i915]()
[ 5481.870340] MMIO read or write has been dropped ffffffff
```

Thanks

---

### Post by tgalati4 on 2014-04-28
The first two warnings are not important.  The ACPI warnings are telling you that you have a BIOS that is using those memory locations for some special purpose.  If you upgrade the BIOS for your computer, those error messages may go away.  Look through the BIOS and see if there are special features that can be activated.  These features would need a special software driver to turn them on or off from within the operating system.

The second warning applies to servers.  If you are running a server, you will specify a hostname so that other computers can talk to it.  Open a terminal:

```
hostname
```

That name should match your terminal prompt and is the name that your computer will show up on the network if you share files or printers.

The last error could be a hardware problem with your Intel graphics chip.  The message is telling you:  "This is Generation 6 of this Intel 915 Series driver and checking for First-In-First-Out memory management."  And it had a problem with the memory management input ouput unit (MMIO).  This may be a bug in the driver or your graphics chip has developed a problem.  If your graphics are OK, then don't worry about it.  If you get video tearing or video dropouts then you might have an issue.  How old is the motherboard?

---

