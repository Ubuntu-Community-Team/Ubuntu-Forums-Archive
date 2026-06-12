---
title: "hardlocking"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by z987k on 2006-09-25
I hope someone can help me out with this.  I recently switched to ubuntu from mandriva 2006 hoping that some of my problems woud go away.  One being random hardlocks.  It never happened before I upgraded to 2006 from 10.1 and it never happens when I boot into windows to play games.  So I am thinking this has to be some problem with the newer distros and my machine.

The big problem is it leaves nothing in the log files, so I have no idea what it is.  It's also completely random.  Sometimes i'll get 30mins sometimes days and sometimes 10 seconds or less but never before the desktop loads.

Thanks for any help,
Zach

---

### Post by z987k on 2006-09-25
This is getting rather annoying and I'm still unable to track it down.

Some more info:
Kernel: 2.6.15-27-686
Vid Card: Nvidia 6200 running latest (but not beta) drivers
P4 3ghz
1.5gb ram

Here's some pieces from various logs, see if someone can see something I can't.  Lock happened at 20:36:02

[B]
Syslog:[/B]
```
Sep 25 20:23:38 localhost gdm[4578]: Couldn't authenticate user
Sep 25 20:23:43 localhost gconfd (zach-5040): starting (version 2.14.0), pid 5040 user 'zach'
Sep 25 20:23:43 localhost gconfd (zach-5040): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep 25 20:23:43 localhost gconfd (zach-5040): Resolved address "xml:readwrite:/home/zach/.gconf" to a writable configuration source at position 1
Sep 25 20:23:43 localhost gconfd (zach-5040): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep 25 20:23:43 localhost gconfd (zach-5040): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep 25 20:23:43 localhost gconfd (zach-5040): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep 25 20:23:46 localhost gconfd (zach-5040): Resolved address "xml:readwrite:/home/zach/.gconf" to a writable configuration source at position 0
Sep 25 20:23:46 localhost kernel: [17179619.168000] cdrom: hdc: mrw address space DMA selected
Sep 25 20:23:46 localhost kernel: [17179619.404000] cdrom: hdc: mrw address space DMA selected
Sep 25 20:37:06 localhost syslogd 1.4.1#17ubuntu7: restart.
Sep 25 20:37:06 localhost kernel: Inspecting /boot/System.map-2.6.15-26-386
Sep 25 20:37:06 localhost kernel: Loaded 23037 symbols from /boot/System.map-2.6.15-26-386.
Sep 25 20:37:06 localhost kernel: Symbols match kernel version 2.6.15.
Sep 25 20:37:06 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Sep 25 20:37:06 localhost kernel: [17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006
Sep 25 20:37:06 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000005ffb0000 (usable)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 000000005ffb0000 - 000000005ffc0000 (ACPI data)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 000000005ffc0000 - 000000005fff0000 (ACPI NVS)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 000000005fff0000 - 0000000060000000 (reserved)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Sep 25 20:37:06 localhost kernel: [17179569.184000] 639MB HIGHMEM available.
Sep 25 20:37:06 localhost kernel: [17179569.184000] 896MB LOWMEM available.
Sep 25 20:37:06 localhost kernel: [17179569.184000] On node 0 totalpages: 393136
Sep 25 20:37:06 localhost kernel: [17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
Sep 25 20:37:06 localhost kernel: [17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
Sep 25 20:37:06 localhost kernel: [17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
Sep 25 20:37:06 localhost kernel: [17179569.184000]   HighMem zone: 163760 pages, LIFO batch:31
Sep 25 20:37:06 localhost kernel: [17179569.184000] DMI 2.3 present.
```


**Kernel Log**
```
Sep 25 20:23:33 localhost kernel: [17179606.248000] ath0: no IPv6 routers present
Sep 25 20:23:46 localhost kernel: [17179619.168000] cdrom: hdc: mrw address space DMA selected
Sep 25 20:23:46 localhost kernel: [17179619.404000] cdrom: hdc: mrw address space DMA selected
Sep 25 20:37:06 localhost kernel: Inspecting /boot/System.map-2.6.15-26-386
Sep 25 20:37:06 localhost kernel: Loaded 23037 symbols from /boot/System.map-2.6.15-26-386.
Sep 25 20:37:06 localhost kernel: Symbols match kernel version 2.6.15.
Sep 25 20:37:06 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Sep 25 20:37:06 localhost kernel: [17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006
Sep 25 20:37:06 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000005ffb0000 (usable)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 000000005ffb0000 - 000000005ffc0000 (ACPI data)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 000000005ffc0000 - 000000005fff0000 (ACPI NVS)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 000000005fff0000 - 0000000060000000 (reserved)
Sep 25 20:37:06 localhost kernel: [17179569.184000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Sep 25 20:37:06 localhost kernel: [17179569.184000] 639MB HIGHMEM available.
Sep 25 20:37:06 localhost kernel: [17179569.184000] 896MB LOWMEM available.
Sep 25 20:37:06 localhost kernel: [17179569.184000] On node 0 totalpages: 393136
Sep 25 20:37:06 localhost kernel: [17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
Sep 25 20:37:06 localhost kernel: [17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
Sep 25 20:37:06 localhost kernel: [17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
Sep 25 20:37:06 localhost kernel: [17179569.184000]   HighMem zone: 163760 pages, LIFO batch:31
Sep 25 20:37:06 localhost kernel: [17179569.184000] DMI 2.3 present.
```

If you need more please say so.

Zach

---

### Post by z987k on 2006-09-27
Well I narowed it down to the nvidia drivers, simply because it doesn't happen if I have the generic "nv" driver loaded instead of nvidia's.

Problem is I don't like not having xgl!

---

