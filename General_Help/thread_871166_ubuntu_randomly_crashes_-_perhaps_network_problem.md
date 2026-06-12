---
title: "ubuntu randomly crashes - perhaps network problem?"
date: 2008-07-26
forum: General Help
---

### Post by subgeneric on 2008-07-26
ubuntu 8.04
kernel 2.6.24-19-generic
pentium III 1.16 GHZ (512K RAM)
NVIDIA GeForce 2 200MMX (32MB RAM)

Hello.  I first noticed this a couple of weeks ago when I was playing around with nmap.  I was running some scans on another computer when ubuntu froze and the num and caps lock lights on my keyboard started blinking.  I restarted and ran the same scan on my ubuntu box from the other computer and it crashed again.  This seemed like an isolated event until about three ago when i loaded up deluge (bittorrent client) and my computer crashed several times in a row.  I played around with some of the settings in deluge like lowered the max connections and throttled the bandwidth but my comp still crashes randomly.  Now it has started crashing with other programs as well and it is becoming more and more frequent.  It has crashed while running deluge, MPlayer, and firefox simultaneously; deluge, firefox, and vlc simultaneously; MPlayer by itself; deluge and firefox simultaneously.

So I decided to join the forums and seek an answer.  I don't really know what information is required but i am providing /var/log/messages at the time of the last crash.  If anything more is needed please tell me what to post.



Jul 26 13:50:48 jamma-desktop kernel: [   65.444165] ACPI: Sleep Button (CM) [SLPB]
Jul 26 13:50:48 jamma-desktop kernel: [   65.655193] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Jul 26 13:50:48 jamma-desktop kernel: [   65.655212] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Jul 26 13:50:48 jamma-desktop kernel: [   67.219016] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Jul 26 13:50:48 jamma-desktop kernel: [   69.238776] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Jul 26 13:50:48 jamma-desktop kernel: [   69.238793] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Jul 26 13:50:48 jamma-desktop kernel: [   73.927757] lp0: using parport0 (interrupt-driven).
Jul 26 13:50:48 jamma-desktop kernel: [   74.116288] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
Jul 26 13:50:48 jamma-desktop kernel: [   74.745657] EXT3 FS on sda1, internal journal
Jul 26 13:50:48 jamma-desktop kernel: [   76.516547] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 26 13:50:48 jamma-desktop kernel: [   77.788429] No dock devices found.
Jul 26 13:50:50 jamma-desktop kernel: [   80.720089] NET: Registered protocol family 10
Jul 26 13:50:50 jamma-desktop kernel: [   80.721328] lo: Disabled Privacy Extensions
Jul 26 13:50:50 jamma-desktop kernel: [   81.334372] ppdev: user-space parallel port driver
Jul 26 13:50:51 jamma-desktop kernel: [   81.786376] audit(1217098251.119:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4807 profile="/usr/sbin/cupsd" namespace="default"
Jul 26 13:50:51 jamma-desktop kernel: [   81.937779] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jul 26 13:50:51 jamma-desktop kernel: [   81.937795] apm: overridden by ACPI.
Jul 26 13:50:54 jamma-desktop dhcdbd: Started up.
Jul 26 13:50:55 jamma-desktop kernel: [   86.312621] eth0: link down
Jul 26 13:50:55 jamma-desktop kernel: [   86.313044] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 26 13:50:55 jamma-desktop kernel: [   86.504971] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 26 13:50:55 jamma-desktop kernel: [   86.561207] Bluetooth: Core ver 2.11
Jul 26 13:50:55 jamma-desktop kernel: [   86.566642] NET: Registered protocol family 31
Jul 26 13:50:55 jamma-desktop kernel: [   86.566658] Bluetooth: HCI device and connection manager initialized
Jul 26 13:50:55 jamma-desktop kernel: [   86.566669] Bluetooth: HCI socket layer initialized
Jul 26 13:50:55 jamma-desktop kernel: [   86.629966] Bluetooth: L2CAP ver 2.9
Jul 26 13:50:55 jamma-desktop kernel: [   86.629980] Bluetooth: L2CAP socket layer initialized
Jul 26 13:50:56 jamma-desktop kernel: [   86.684958] Bluetooth: RFCOMM socket layer initialized
Jul 26 13:50:56 jamma-desktop kernel: [   86.685531] Bluetooth: RFCOMM TTY layer initialized
Jul 26 13:50:56 jamma-desktop kernel: [   86.685542] Bluetooth: RFCOMM ver 1.8
Jul 26 13:51:28 jamma-desktop pulseaudio[5769]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 44099 Hz.
Jul 26 13:51:35 jamma-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jul 26 13:51:37 jamma-desktop kernel: [  128.503376] NET: Registered protocol family 17
Jul 26 13:51:38 jamma-desktop kernel: [  129.516853] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 26 13:51:43 jamma-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Jul 26 13:51:43 jamma-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jul 26 13:51:43 jamma-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jul 26 13:51:43 jamma-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Jul 26 14:41:24 jamma-desktop syslogd 1.5.0#1ubuntu1: restart.
Jul 26 14:41:24 jamma-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 26 14:41:24 jamma-desktop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Jul 26 14:41:24 jamma-desktop kernel: Symbols match kernel version 2.6.24.
Jul 26 14:41:24 jamma-desktop kernel: Loaded 15548 symbols from 88 modules.
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000] 511MB LOWMEM available.
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000]   Normal       4096 ->   131056
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000]   HighMem    131056 ->   131056
Jul 26 14:41:24 jamma-desktop kernel: [    0.000000] Movable zone start PFN for each node

thank you for your time.

---

### Post by Metralha on 2008-12-07
Bump...(Sorry for this but didn't see the point to create a new thread)

Hello there! I am a newbie in ubuntu and i have the same problem that it described by subgeneric. I have a Asus F3JP and sometimes the caps lock and num start blinking and ubuntu crashes. I am not doing anything special just programing in eclipse or so. And many other guys in my work have the some problem. Any thoughts on the matter?I have ubuntu 8.10 in real dual bot (not installed inside windows). Thanks anyway...;)

---

