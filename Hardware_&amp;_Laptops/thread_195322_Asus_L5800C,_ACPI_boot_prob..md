---
title: "Asus L5800C, ACPI boot prob."
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by rmerry on 2006-06-12
Won't boot unless I set pci=noacpi at boot time. Last message (which clued me that it might be an ACPI prob hence the boot option).

```

ACPI: PCI Interrupt 0000: 00: 04.0[A]: no GSI.

```

Running:

2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

Which is odd, as this has just started happening and the kernel was working fine.

Any ideas? It's not a huge issue as I can workaround but wondering if anyone can shed any light on why it is happening.

---

### Post by norman_h on 2006-06-13
Similar problems with my ASUS M6R.

Instead of the kernel boot time option, I removed the link to S10acpid from the bootscripts in /etc/rc2.d

From what I can understand, it appears to be an ACPI problem that extends beyond ubuntu.  Making acpi4linux work with the kernel is still under heavy development.  As for any workaround, i'd love to hear of it.  I'm looking into upgrading the dapper kernel to the latest version as there appears to be some acpi work done within it.  If i'm succesfull i'll definately tell ASUS owners about it!

---

### Post by rmerry on 2006-06-15
Oddly enough, this was caused by having my usb keybord (which is also a hub with mouse plugged into it) plugged in at boot time.

Remove it, laptop boots fine. Put it back, boot fails. Works fine if I connect it post boot.

Very odd.

---

### Post by norman_h on 2006-06-15
^^  That doesn't happen with me.  This may also have something to do with dbus.  Please correct me if i'm wrong, but I think that dbus has only been included with the dapper release.  I remember reading that dbus connects usb and acpi in some way, for some reason...

By the way, I tried compiling the latest kernel version and it didn't solve my problems.  There seems to be a new kernel in the auto updates, i'm about to reboot and try that one...

:)

---

