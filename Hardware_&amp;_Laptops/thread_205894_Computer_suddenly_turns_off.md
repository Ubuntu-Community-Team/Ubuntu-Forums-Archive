---
title: "Computer suddenly turns off"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by grw on 2006-06-29
I have a major problem with my laptop suddenly turning itself off. Bang - like what happens when you press the power button for 5 seconds. It's happened twice today and once yesterday and, of course, I lose everything I was working on. I am running Ubuntu 6.06 on my old Dell 2500 laptop. I have kernel 2.6.15-25. I'd really appreciate any help on this. 

Below is the output from var/log/messages from yesterday. There seems to be lots of activty relating to ACPI and Bluetooth (which I have no use for) before eveything suddenly stops - I think at 14:13:27. I restarted immediately but this doesn't show up in teh log. You get ...Mark ... Mark  every half hour and then 'gconfd (gwyn-17298): starting (version 2.14.0), pid 17298 user 'gwyn'' just before I shut down my computer for teh day.

???

Jun 28 14:12:55 localhost kernel: [17179611.948000] NET: Registered protocol family 10
Jun 28 14:12:55 localhost kernel: [17179611.948000] lo: Disabled Privacy Extensions
Jun 28 14:12:55 localhost kernel: [17179611.952000] IPv6 over IPv4 tunneling driver
Jun 28 14:12:55 localhost kernel: [17179612.628000] cdrom: open failed.
Jun 28 14:12:55 localhost kernel: [17179613.944000] NTFS driver 2.1.25 [Flags: R/O MODULE].
Jun 28 14:12:55 localhost kernel: [17179614.116000] NTFS volume version 3.1.
Jun 28 14:12:55 localhost kernel: [17179622.288000] ACPI: AC Adapter [AC] (on-line)
Jun 28 14:12:55 localhost kernel: [17179622.448000] pcc_acpi: loading...
Jun 28 14:12:55 localhost kernel: [17179622.484000] ACPI: Power Button (FF) [PWRF]
Jun 28 14:12:55 localhost kernel: [17179622.484000] ACPI: Lid Switch [LID]
Jun 28 14:12:55 localhost kernel: [17179622.484000] ACPI: Sleep Button (CM) [SLPB]
Jun 28 14:12:55 localhost kernel: [17179622.700000] ACPI: Battery Slot [BAT0] (battery present)
Jun 28 14:12:55 localhost kernel: [17179622.784000] ACPI: Video Device [GCH0] (multi-head: yes  rom: no  post: no)
Jun 28 14:13:01 localhost hpiod: 0.9.7 accepting connections at 34364... 
Jun 28 14:13:05 localhost kernel: [17179634.004000] ppdev: user-space parallel port driver
Jun 28 14:13:05 localhost kernel: [17179634.436000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jun 28 14:13:05 localhost kernel: [17179634.440000] apm: overridden by ACPI.
Jun 28 14:13:12 localhost kernel: [17179640.908000] Bluetooth: Core ver 2.8
Jun 28 14:13:12 localhost kernel: [17179640.908000] NET: Registered protocol family 31
Jun 28 14:13:12 localhost kernel: [17179640.908000] Bluetooth: HCI device and connection manager initialized
Jun 28 14:13:12 localhost kernel: [17179640.908000] Bluetooth: HCI socket layer initialized
Jun 28 14:13:12 localhost kernel: [17179641.004000] Bluetooth: L2CAP ver 2.8
Jun 28 14:13:12 localhost kernel: [17179641.004000] Bluetooth: L2CAP socket layer initialized
Jun 28 14:13:12 localhost kernel: [17179641.028000] Bluetooth: RFCOMM socket layer initialized
Jun 28 14:13:12 localhost kernel: [17179641.028000] Bluetooth: RFCOMM TTY layer initialized
Jun 28 14:13:12 localhost kernel: [17179641.028000] Bluetooth: RFCOMM ver 1.7
Jun 28 14:13:15 localhost gconfd (gwyn-4781): starting (version 2.14.0), pid 4781 user 'gwyn'
Jun 28 14:13:15 localhost gconfd (gwyn-4781): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 28 14:13:15 localhost gconfd (gwyn-4781): Resolved address "xml:readwrite:/home/gwyn/.gconf" to a writable configuration source at position 1
Jun 28 14:13:15 localhost gconfd (gwyn-4781): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 28 14:13:15 localhost gconfd (gwyn-4781): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 28 14:13:15 localhost gconfd (gwyn-4781): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 28 14:13:27 localhost gconfd (gwyn-4781): Resolved address "xml:readwrite:/home/gwyn/.gconf" to a writable configuration source at position 0
Jun 28 14:32:55 localhost -- MARK --
Jun 28 14:52:55 localhost -- MARK --
Jun 28 15:12:55 localhost -- MARK --
Jun 28 15:32:55 localhost -- MARK --
Jun 28 15:52:56 localhost -- MARK --
Jun 28 16:12:56 localhost -- MARK --
Jun 28 16:32:56 localhost -- MARK --
Jun 28 16:52:57 localhost -- MARK --
Jun 28 17:12:57 localhost -- MARK --
Jun 28 17:32:57 localhost -- MARK --
Jun 28 17:52:57 localhost -- MARK --
Jun 28 18:12:58 localhost -- MARK --
Jun 28 18:32:58 localhost -- MARK --
Jun 28 18:52:58 localhost -- MARK --
Jun 28 19:00:36 localhost gconfd (gwyn-4781): Exiting
Jun 28 19:00:36 localhost gconfd (gwyn-17298): starting (version 2.14.0), pid 17298 user 'gwyn'
Jun 28 19:00:37 localhost gconfd (gwyn-17298): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 28 19:00:37 localhost gconfd (gwyn-17298): Resolved address "xml:readwrite:/home/gwyn/.gconf" to a writable configuration source at position 1
Jun 28 19:00:37 localhost gconfd (gwyn-17298): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 28 19:00:37 localhost gconfd (gwyn-17298): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 28 19:00:37 localhost gconfd (gwyn-17298): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 28 19:00:39 localhost shutdown[4268]: shutting down for system halt
Jun 28 19:00:44 localhost kernel: [17196892.152000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jun 28 19:00:44 localhost kernel: [17196892.152000] apm: disabled on user request.
Jun 28 19:00:52 localhost kernel: Kernel logging (proc) stopped.
Jun 28 19:00:52 localhost kernel: Kernel log daemon terminating.
Jun 28 19:00:53 localhost exiting on signal 15
Jun 29 09:26:47 localhost syslogd 1.4.1#17ubuntu7: restart.

---

