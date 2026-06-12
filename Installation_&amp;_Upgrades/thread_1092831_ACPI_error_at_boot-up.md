---
title: "ACPI error at boot-up"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by pat.bradford1 on 2009-03-10
My son and I just put together a machine using a Gigaparts GA-MA74GM-SG motherboard and an AMD Performa CPU. We are attempting to "try out" Ubuntu from the 6.06 Live-CD. At first, the boot screen would not recognize a USB keyboard or mouse. The loader would time out, the system would attempt to boot, but I get the ACPI error. 

A couple of trips into the BIOS revealed USB Keyboard and Mouse Enable.  This allowed the two to be enabled, and I could use F6 to enter "noapci" into the boot command line (that IS how the flag is spelled, isn't it?).

Unfortunately, on reboot, the boot failed, and the call stack looked like this:

acpi_rs_create_pci_routing_table+0x1e/0x17a
acpi_ex_opcode_1A_0T_1R+0x392/0x427
acpi_rs_get_ptr_method_data+0x2b/0x3e
acpi_pci_irq_add_ptr+0xb3/0x153
acpi_pci_bind_+0x20f/0x23e
acpi_add_single_object+0x113/0x141
acpi_bus_scan+0x11f/0x191
acpi_scan_init+0x69/0x85
do_init_calls_0x4d/0xc0
init+0x0/0x150
init+0x31/0x150
kernel_thread_helper+0x5/0x10

Code: 83 c4 10 5b 5e 5f 5d c3 55 57 56 53 51 8b 44 24 18 8b 50
0c 89 14 24 8b 68 1c 31 f6 31 ff eb 5f 8b 44 bd 00 8b 50 1c 31
db 8b 0a <8a>  41 01 3c 02 74 12 3c 14 75 07 66 83 79 0a 2d 74
07 83 c2 04

<0> Kernel panic - not syncing:  Attempted to kill init!

Any suggestions?

---

### Post by Neo_The_User on 2009-03-10
Try turning ACPI off before boot. One of the F keys after you select language. ;) Also, 6.06 is kinda old hahaha.

---

### Post by avtolle on 2009-03-10
Just wondering; wouldn't the correct boot option be "acpi=off"?

---

### Post by Neo_The_User on 2009-03-10
> **avtolle said:**
> Just wondering; wouldn't the correct boot option be "acpi=off"?

Oh yeah thats right! You can easily turn acpi off though via F command.

---

### Post by avtolle on 2009-03-10
I stand corrected; "noacpi" and "acpi=off" have the same effect. Does [https://help.ubuntu.com/community/BootOptions#Kernel%20Options](https://help.ubuntu.com/community/BootOptions#Kernel%20Options) give you any other possible options?

---

### Post by pat.bradford1 on 2009-03-11
Thanks! acpi=off seems to do the trick!

---

