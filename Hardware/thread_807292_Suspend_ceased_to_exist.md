---
title: "Suspend ceased to exist"
date: 2008-05-25
forum: Hardware
---

### Post by dagfinn on 2008-05-25
I had few problems after upgrading to Hardy, but trouble has been showing up later. A peculiar problem that just happened recently is the following: In KDE 3 (which I use mostly), neither the battery manager nor the logout dialog has a suspend button any more. (Hibernate is present, though.) Nor does it suspend when I close the lid. In the power manager configuration dialog, the "battery powered" options are greyed out. Also CPU frequency and battery charge are no longer shown.

I tried Gnome, and it seems even worse.

I have no idea what could have caused it, and I can't find a report of anything similar anywhere.

Any ideas?

P.S. My computer is a Dell Vostro 1000.

---

### Post by dagfinn on 2008-05-26
I finally found some info on the Gnome power manager page. It tell me to do "lshal | grep can_suspend", which returns

```
power_management.can_suspend = false  (bool)
power_management.can_suspend_hybrid = false  (bool)
power_management.can_suspend_to_disk = true  (bool)
power_management.can_suspend_to_ram = false  (bool)

```

That at least makes sense. Now I'm advised:

> If HAL doesn't list the options you want, then maybe you need to check your BIOS to check that it's running in the correct mode, and also that you have compiled your kernel with the correct options.


So, searching for BIOS in dmesg I find this:

```

[   17.660952] PCI: BIOS BUG #81[49435000] found
[   17.660991] PCI: Using configuration type 1
[   17.660993] Setting up standard PCI resources
[   17.662218] ACPI: Interpreter disabled.
[   17.662221] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.662248] pnp: PnP ACPI: disabled
[   17.662252] PnPBIOS: Scanning system for PnP BIOS support...
[   17.662259] PnPBIOS: Found PnP BIOS installation structure at 0xc00f8540
[   17.662262] PnPBIOS: PnP BIOS version 1.0, entry 0xe5cc:0x9499, dseg 0x400
[   17.662267] PNPBIOS fault.. attempting recovery.
[   17.662303] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[   17.662340] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[   17.662377] PnPBIOS: Check with your vendor for an updated BIOS
[   17.662413] PnPBIOS: dev_node_info: unexpected status 0x37
[   17.662449] PnPBIOS: Unable to get node info.  Aborting.
```

I don't have sufficient insight to do anything meaningful with this.

I installed a fresh Kubuntu Hardy, and the PnPBIOS problem doesn't occur there. The power manager looks normal there, but I can't get suspend to work and I'm not keen on trying to find out why. I've had several suspend issues and fixed some, but this is another behavior that's looks new. When I try to suspend, it displays all the messages. They look fine, but I can't resume.

:frown:

---

