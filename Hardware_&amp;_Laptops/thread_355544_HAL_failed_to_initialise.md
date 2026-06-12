---
title: "HAL failed to initialise"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by MrHorus on 2007-02-07
I'm getting this error message when I log in on (what is now) a clean boot.

I noticed about a week ago that the system was hanging on boot at "Starting Hardware Abstraction Layer (HALd)" and wouldn't progress after that (I was running Kubuntu happily until that point).

If I booted an older (i386) kernel it did progress past (but HALd dies) and if I alter my K7 kernel entry in the boot menu to "acpi=off" it will boot but again, die in the background.

I know it dies as if I run dmesg it shows a Kernel Oops occuring along with a list of loaded modules and where the oops occured and yeah, the trace shows that it's HALd that brings the kernel down.

It's odd as I backed up home, etc and var onto my xbox and formatted the laptop to reinstall 6.06 but the fault is pretty much the same except it boots and gives the "HAL did not initialise" error.

Bit worrying that it's suddenly started doing this and persists after a clean install.

Hardware fault?

---

### Post by MrHorus on 2007-02-08
Hardware fault indeed.

I noticed a function call to acpi_get_battery_status was the last thing that was done before the Kernel Oops (it showed this in the trace) so I tried with the battery out.

Voila! 
Magic!

Everything was fine, updates installed great, things were good until I tried putting the battery back in.

The problem returned exactly like I was getting before the reinstall so I took the battery out and yeah, the problem went away.

Not sure if it's the battery itself that's a goner or the interface on the laptop side but I might try buying a replacement battery off the net.

At least now I know what the problem is, I know that the laptop is working again and at any rate I now have a shiney and fast clean installation :)

---

