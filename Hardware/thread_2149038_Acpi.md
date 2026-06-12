---
title: "Acpi"
date: 2013-05-27
forum: Hardware
---

### Post by YayaYo on 2013-05-27
[COLOR=#000000][FONT=monospace]Hello forum. A few weeks ago I tried to install Ubuntu server on my desktop machine just to try it out before upgrading to a new server. This installation failed (I don't remember exactly why) and somehow all advanced power options were removed from my BIOS. My fans now run at maximum speed from from the moment I boot.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]After loading Ubuntu 3.2.0-44-generic-pae[/FONT][/COLOR][COLOR=#000000][FONT=monospace], I am unable to run "detect-sensors", as in no sensors are found. Other threads have suggested various things including adding a boot option to GRUB2 `GRUB_CMDLINE_LINUX="acpi=off"`. After reboot, I am able to run detect-sensors and control the fanspeed using "fancontrol" service. However, using this boot setting, now Ubuntu is unable to detect duel core.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]The kernel log indicated this with option "acpi=off":[/FONT][/COLOR]
[COLOR=#00008B][FONT=monospace]May 27[/FONT][/COLOR][COLOR=#000000][FONT=monospace]03:00:26 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23[/FONT][/COLOR]
[COLOR=#00008B][FONT=monospace]May 27[/FONT][/COLOR][COLOR=#000000][FONT=monospace]03:00:26 kernel: [    0.000000] Processors: 1[/FONT][/COLOR]
[COLOR=#00008B][FONT=monospace]May 27[/FONT][/COLOR][COLOR=#000000][FONT=monospace]03:00:26 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]and this with option "acpi=on"[/FONT][/COLOR]
[COLOR=#00008B][FONT=monospace]May 27[/FONT][/COLOR][COLOR=#000000][FONT=monospace]02:49:17 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information[/FONT][/COLOR]
[COLOR=#00008B][FONT=monospace]May 27[/FONT][/COLOR][COLOR=#000000][FONT=monospace]02:49:17 kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]With "acpi=on" option, I tried manually loading my sensor drivers into the kernel using `ismod` to no avail.[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]# Adapter drivers
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]i2c_i801[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]# Chip drivers[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]dme1737[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]Is there a way to have both acpi=off and duel core on? Originally, all this was handled by the BIOS but somehow now the options don't exist anymore.[/FONT][/COLOR][FONT=monospace][SIZE=3][COLOR=#000000] Flashing the BIOS doesn't seem like a viable option (HP requires XP installation).[/COLOR][/SIZE][/FONT]

[FONT=monospace][SIZE=3][COLOR=#000000]Thanks in advance![/COLOR][/SIZE][/FONT]

---

