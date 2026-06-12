---
title: "ubuntu 8.10 hangs randomly with jerky mouse cursor"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by spesa on 2009-01-21
Hi everyone,

I have installed Ubuntu 8.10 yesterday. Installation went well. I noticed that the system hangs randomly. Mouse cursor becomes jerky and everything else is frozen. Keyboard is not working either, pressing Ctrl+Altv+BckSpace has no effect, nor Ctrl+Alt+Del.

The only way out is to hold power button to turn off computer then restart it over.

I haven't got time yet to install updates (222 listed). I have installed instead various codec (using Gnome GUI) for playing restricted multimedia file format as well as Macromedia flash player (through Add/Remove menu entry)...

I have the assumption that this problem has started after installing those codec... but I haven't used Ubuntu 8.10 for long enough to make sure of this.

Has anyone got such experience?
thank you for any help....

---

### Post by SkyLeach on 2009-01-21
> **spesa said:**
> Hi everyone,

I have installed Ubuntu 8.10 yesterday. Installation went well. I noticed that the system hangs randomly. Mouse cursor becomes jerky and everything else is frozen. Keyboard is not working either, pressing Ctrl+Altv+BckSpace has no effect, nor Ctrl+Alt+Del.

The only way out is to hold power button to turn off computer then restart it over.

I haven't got time yet to install updates (222 listed). I have installed instead various codec (using Gnome GUI) for playing restricted multimedia file format as well as Macromedia flash player (through Add/Remove menu entry)...

I have the assumption that this problem has started after installing those codec... but I haven't used Ubuntu 8.10 for long enough to make sure of this.

Has anyone got such experience?
thank you for any help....

the things I have seen cause this include:

thrashing the swap partition (using up all available memory): check to be sure that your highmem is correctly loading with cat /proc/meminfo.

Results good: 3GB of memory
```

mgregory@gregory-gentoo ~/src/ttv/trunk $ cat /proc/meminfo 
MemTotal:      3112976 kB
<rest cut>

```

Results bad (highmem misconfigured): only 800KB of memory
```

ironman2 ~ # cat /proc/meminfo 
MemTotal:       894220 kB
<rest cut>

```

This can be caused ty running amd64/x86_64 but accidentally forgetting to set 64bit memory and io in the kernel settings.  Unlikely if you are using the default kernel.

unsupported and/or missing chipset information in the kernel: check to be certain that  your chipset has a driver and is not using the generic pci driver by running "lspci -v | less" and then search for "Host bridge" by typing exactly '/Host bridge' into the pager (less).  You should see the name of your hardware and the name of the kernel module that is handling it.  The livecd kernel doesn't support everything out of the box, it can't, but it does support most chipsets.  If your coputer is very new then you may need to download and compile a kernel for your hardware including the driver patch from the manufacturer.

driver collisions on IRQs and/or power management.  When you get to the grub boot loader try booting with 'noapic' and/or 'acpi=off' and see if this takes care of the issue.  You can edit your boot options by hitting 'e' in grub (for edit) and then editing the kernel line.  The options should go after the root= or real_root= option.  IMHO this is the most likely cause of your problem.

---

