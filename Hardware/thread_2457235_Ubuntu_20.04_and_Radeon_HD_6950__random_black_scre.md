---
title: "Ubuntu 20.04 and Radeon HD 6950 : random black screens forcing me to force reboot"
date: 2021-01-28
forum: Hardware
---

### Post by oasisforever on 2021-01-28
Hi everyone,

Since a few days I experience random black screens, forcing me to reboot the computer with the power button.
I suspect the video driver to be responsible, but I'm not sure. I hope you could help me out here.

First some details about my system (Ubuntu 20.04, fresh install) and the video card:

```

tom@tom-desktop-linux:~$ uname -r
5.8.0-40-generic
tom@tom-desktop-linux:~$ lspci -k | grep -EA3 'VGA|3D|Display' 
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cayman PRO [Radeon HD 6950]
	Subsystem: PC Partner Limited / Sapphire Technology Cayman PRO [Radeon HD 6950]
	Kernel driver in use: radeon
	Kernel modules: radeon
tom@tom-desktop-linux:~$ sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: Cayman PRO [Radeon HD 6950]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:48 memory:d0000000-dfffffff memory:fe620000-fe63ffff ioport:e000(size=256) memory:c0000-dffff
```

And here is the journalctl output minutes before the event:

```

linux kernel: audit: type=1400 audit(1611841291.961:1464): apparmor="DENIED" operation="open" profile="snap.kate.kate" name="/proc/sys/kernel/core_pattern" pid=4899 comm="kate" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jan 28 14:41:32 tom-desktop-linux org.gnome.Nautilus[4899]: Qt: Session management error: Could not open network socket
Jan 28 14:41:32 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:41:32 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:41:32 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:41:32 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:41:42 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:42:05 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:42:11 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:42:11 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:42:11 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:42:50 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:42:57 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:43:15 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:43:26 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:43:42 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:44:23 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:44:23 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:44:23 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:44:31 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:46:03 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:47:11 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:47:11 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:47:11 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:47:25 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:47:59 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:48:39 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:49:23 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:49:23 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:49:23 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:51:23 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:51:59 tom-desktop-linux audit[5008]: AVC apparmor="DENIED" operation="open" profile="snap.kate.kate" name="/proc/sys/kernel/core_pattern" pid=5008 comm="kate" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jan 28 14:51:59 tom-desktop-linux kernel: audit: type=1400 audit(1611841919.574:1465): apparmor="DENIED" operation="open" profile="snap.kate.kate" name="/proc/sys/kernel/core_pattern" pid=5008 comm="kate" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jan 28 14:51:59 tom-desktop-linux org.gnome.Nautilus[5008]: Qt: Session management error: Could not open network socket
Jan 28 14:51:59 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:51:59 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:51:59 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:52:00 tom-desktop-linux org.gnome.Nautilus[3915]: sonnet.core: No language dictionaries for the language: "en_US"
Jan 28 14:52:11 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:52:11 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:52:12 tom-desktop-linux systemd-resolved[365]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jan 28 14:53:14 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 10244msec
Jan 28 14:53:14 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015663 on ring 0)
Jan 28 14:53:14 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 10240msec
Jan 28 14:53:14 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:14 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 10752msec
Jan 28 14:53:14 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:14 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 10756msec
Jan 28 14:53:14 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015664 on ring 0)
Jan 28 14:53:15 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 11268msec
Jan 28 14:53:15 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015665 on ring 0)
Jan 28 14:53:15 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 11264msec
Jan 28 14:53:15 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:16 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 11776msec
Jan 28 14:53:16 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:16 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 11780msec
Jan 28 14:53:16 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015666 on ring 0)
Jan 28 14:53:16 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 12292msec
Jan 28 14:53:16 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015667 on ring 0)
Jan 28 14:53:16 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 12288msec
Jan 28 14:53:16 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:17 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 12804msec
Jan 28 14:53:17 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015668 on ring 0)
Jan 28 14:53:17 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 12800msec
Jan 28 14:53:17 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:17 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 13316msec
Jan 28 14:53:17 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015669 on ring 0)
Jan 28 14:53:17 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 13312msec
Jan 28 14:53:17 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:18 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 13828msec
Jan 28 14:53:18 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001566a on ring 0)
Jan 28 14:53:18 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 13824msec
Jan 28 14:53:18 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:18 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 14340msec
Jan 28 14:53:18 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001566b on ring 0)
Jan 28 14:53:18 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 14336msec
Jan 28 14:53:18 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:19 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 14848msec
Jan 28 14:53:19 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:19 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 14852msec
Jan 28 14:53:19 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001566c on ring 0)
Jan 28 14:53:19 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 15364msec
Jan 28 14:53:19 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001566d on ring 0)
Jan 28 14:53:19 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 15360msec
Jan 28 14:53:19 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:20 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 15872msec
Jan 28 14:53:20 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:20 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 15876msec
Jan 28 14:53:20 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001566e on ring 0)
Jan 28 14:53:20 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 16388msec
Jan 28 14:53:20 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001566f on ring 0)
Jan 28 14:53:20 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 16384msec
Jan 28 14:53:20 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:21 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 16896msec
Jan 28 14:53:21 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:21 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 16900msec
Jan 28 14:53:21 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015670 on ring 0)
Jan 28 14:53:21 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 17408msec
Jan 28 14:53:21 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:21 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 17412msec
Jan 28 14:53:21 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015671 on ring 0)
Jan 28 14:53:22 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 17920msec
Jan 28 14:53:22 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 17924msec
Jan 28 14:53:22 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015672 on ring 0)
Jan 28 14:53:22 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:22 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 18436msec
Jan 28 14:53:22 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015673 on ring 0)
Jan 28 14:53:22 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 18432msec
Jan 28 14:53:22 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:23 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 18948msec
Jan 28 14:53:23 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015674 on ring 0)
Jan 28 14:53:23 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 18944msec
Jan 28 14:53:23 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:23 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 19460msec
Jan 28 14:53:23 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 19456msec
Jan 28 14:53:23 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:23 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015675 on ring 0)
Jan 28 14:53:24 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 19968msec
Jan 28 14:53:24 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:24 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 19972msec
Jan 28 14:53:24 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015676 on ring 0)
Jan 28 14:53:24 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 20484msec
Jan 28 14:53:24 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015677 on ring 0)
Jan 28 14:53:24 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 20480msec
Jan 28 14:53:24 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:25 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 20992msec
Jan 28 14:53:25 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:25 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 20996msec
Jan 28 14:53:25 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015678 on ring 0)
Jan 28 14:53:25 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 21508msec
Jan 28 14:53:25 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015679 on ring 0)
Jan 28 14:53:25 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 21504msec
Jan 28 14:53:25 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:26 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 22020msec
Jan 28 14:53:26 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001567a on ring 0)
Jan 28 14:53:26 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 22016msec
Jan 28 14:53:26 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:26 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 22532msec
Jan 28 14:53:26 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001567b on ring 0)
Jan 28 14:53:26 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 22528msec
Jan 28 14:53:26 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:27 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 23044msec
Jan 28 14:53:27 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 23040msec
Jan 28 14:53:27 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:27 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001567c on ring 0)
Jan 28 14:53:27 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 23556msec
Jan 28 14:53:27 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001567d on ring 0)
Jan 28 14:53:27 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 23552msec
Jan 28 14:53:27 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:28 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 24068msec
Jan 28 14:53:28 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001567e on ring 0)
Jan 28 14:53:28 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 24064msec
Jan 28 14:53:28 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:28 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 24580msec
Jan 28 14:53:28 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001567f on ring 0)
Jan 28 14:53:28 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 24576msec
Jan 28 14:53:28 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:29 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 25088msec
Jan 28 14:53:29 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:29 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 25092msec
Jan 28 14:53:29 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015680 on ring 0)
Jan 28 14:53:29 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 25604msec
Jan 28 14:53:29 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015681 on ring 0)
Jan 28 14:53:29 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 25600msec
Jan 28 14:53:29 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:30 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 26116msec
Jan 28 14:53:30 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015682 on ring 0)
Jan 28 14:53:30 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 26112msec
Jan 28 14:53:30 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:30 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 26628msec
Jan 28 14:53:30 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015683 on ring 0)
Jan 28 14:53:30 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 26624msec
Jan 28 14:53:30 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:31 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 27140msec
Jan 28 14:53:31 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015684 on ring 0)
Jan 28 14:53:31 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 27136msec
Jan 28 14:53:31 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:31 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 27648msec
Jan 28 14:53:31 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:31 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 27652msec
Jan 28 14:53:31 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015698 on ring 0)
Jan 28 14:53:32 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 28164msec
Jan 28 14:53:32 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x0000000000015699 on ring 0)
Jan 28 14:53:32 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 28160msec
Jan 28 14:53:32 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:32 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 28672msec
Jan 28 14:53:32 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:32 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 28676msec
Jan 28 14:53:32 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001569a on ring 0)
Jan 28 14:53:33 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 29188msec
Jan 28 14:53:33 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001569b on ring 0)
Jan 28 14:53:33 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 29184msec
Jan 28 14:53:33 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:33 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 29700msec
Jan 28 14:53:33 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001569c on ring 0)
Jan 28 14:53:33 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 29696msec
Jan 28 14:53:33 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:34 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 30208msec
Jan 28 14:53:34 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:34 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 30216msec
Jan 28 14:53:34 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x000000000001569d on ring 0)
Jan 28 14:53:34 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 4 stalled for more than 30720msec
Jan 28 14:53:34 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000006eb4 last fence id 0x0000000000006eb5 on ring 4)
Jan 28 14:53:34 tom-desktop-linux kernel: radeon 0000:01:00.0: ring 0 stalled for more than 30724msec
Jan 28 14:53:34 tom-desktop-linux kernel: radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000015638 last fence id 0x00000000000156a0 on ring 0)
Jan 28 14:53:35 tom-desktop-linux kernel: BUG: unable to handle page fault for address: ffffaa3140890ffc
Jan 28 14:53:35 tom-desktop-linux kernel: #PF: supervisor read access in kernel mode
Jan 28 14:53:35 tom-desktop-linux kernel: #PF: error_code(0x0000) - not-present page
Jan 28 14:53:35 tom-desktop-linux kernel: PGD 32195e067 P4D 32195e067 PUD 0 
Jan 28 14:53:35 tom-desktop-linux kernel: Oops: 0000 [#1] SMP PTI
Jan 28 14:53:35 tom-desktop-linux kernel: CPU: 1 PID: 1680 Comm: gnome-shell Not tainted 5.8.0-40-generic #45~20.04.1-Ubuntu
Jan 28 14:53:35 tom-desktop-linux kernel: Hardware name: System manufacturer System Product Name/P8Z68-V PRO, BIOS 0801 08/15/2011
Jan 28 14:53:35 tom-desktop-linux kernel: RIP: 0010:radeon_ring_backup+0xc9/0x140 [radeon]
Jan 28 14:53:35 tom-desktop-linux kernel: Code: ed 49 89 07 48 85 c0 74 7d 41 8d 7d ff 31 d2 48 c1 e7 02 eb 07 49 8b 07 48 83 c2 04 49 8b 74 24 08 8d 4b 01 89 db 48 8d 34 9e <8b> 36 89 34 10 41 23 4c 24 54 89 cb 48 39 d7 75 da 4c 89 f7 e8 ee
Jan 28 14:53:35 tom-desktop-linux kernel: RSP: 0018:ffffaa2d429abc50 EFLAGS: 00010202
Jan 28 14:53:35 tom-desktop-linux kernel: RAX: ffff9ce6b20e0000 RBX: 00000000ffffffff RCX: 0000000000000000
Jan 28 14:53:35 tom-desktop-linux kernel: RDX: 0000000000000000 RSI: ffffaa3140890ffc RDI: 000000000001aa40
Jan 28 14:53:35 tom-desktop-linux kernel: RBP: ffffaa2d429abc78 R08: 00000000000321e7 R09: 0000000000000000
Jan 28 14:53:35 tom-desktop-linux kernel: R10: ffff9ce6b20e0000 R11: 0000000000000020 R12: ffff9ce81bb613d8
Jan 28 14:53:35 tom-desktop-linux kernel: R13: 0000000000006a91 R14: ffff9ce81bb613b8 R15: ffffaa2d429abcb8
Jan 28 14:53:35 tom-desktop-linux kernel: FS:  00007f1a82072cc0(0000) GS:ffff9ce823480000(0000) knlGS:0000000000000000
Jan 28 14:53:35 tom-desktop-linux kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jan 28 14:53:35 tom-desktop-linux kernel: CR2: ffffaa3140890ffc CR3: 00000002e1d54002 CR4: 00000000000606e0
Jan 28 14:53:35 tom-desktop-linux kernel: Call Trace:
Jan 28 14:53:35 tom-desktop-linux kernel:  radeon_gpu_reset+0xc3/0x2f0 [radeon]
Jan 28 14:53:35 tom-desktop-linux kernel:  ? dma_resv_wait_timeout_rcu+0x153/0x3a0
Jan 28 14:53:35 tom-desktop-linux kernel:  ? radeon_gem_busy_ioctl+0x80/0x80 [radeon]
Jan 28 14:53:35 tom-desktop-linux kernel:  radeon_gem_handle_lockup.part.0+0xe/0x20 [radeon]
Jan 28 14:53:35 tom-desktop-linux kernel:  radeon_gem_wait_idle_ioctl+0xd6/0x110 [radeon]
Jan 28 14:53:35 tom-desktop-linux kernel:  ? radeon_gem_busy_ioctl+0x80/0x80 [radeon]
Jan 28 14:53:35 tom-desktop-linux kernel:  drm_ioctl_kernel+0xae/0xf0 [drm]
Jan 28 14:53:35 tom-desktop-linux kernel:  drm_ioctl+0x234/0x3d0 [drm]
Jan 28 14:53:35 tom-desktop-linux kernel:  ? radeon_gem_busy_ioctl+0x80/0x80 [radeon]
Jan 28 14:53:35 tom-desktop-linux kernel:  ? do_futex+0x14d/0x890
Jan 28 14:53:35 tom-desktop-linux kernel:  ? vm_area_free+0x18/0x20
Jan 28 14:53:35 tom-desktop-linux kernel:  radeon_drm_ioctl+0x4e/0x80 [radeon]
Jan 28 14:53:35 tom-desktop-linux kernel:  ksys_ioctl+0x9d/0xd0
Jan 28 14:53:35 tom-desktop-linux kernel:  __x64_sys_ioctl+0x1a/0x20
Jan 28 14:53:35 tom-desktop-linux kernel:  do_syscall_64+0x49/0xc0
Jan 28 14:53:35 tom-desktop-linux kernel:  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jan 28 14:53:35 tom-desktop-linux kernel: RIP: 0033:0x7f1a874c637b
Jan 28 14:53:35 tom-desktop-linux kernel: Code: 0f 1e fa 48 8b 05 15 3b 0d 00 64 c7 00 26 00 00 00 48 c7 c0 ff ff ff ff c3 66 0f 1f 44 00 00 f3 0f 1e fa b8 10 00 00 00 0f 05 <48> 3d 01 f0 ff ff 73 01 c3 48 8b 0d e5 3a 0d 00 f7 d8 64 89 01 48
Jan 28 14:53:35 tom-desktop-linux kernel: RSP: 002b:00007ffeda5ba1b8 EFLAGS: 00000246 ORIG_RAX: 0000000000000010
Jan 28 14:53:35 tom-desktop-linux kernel: RAX: ffffffffffffffda RBX: 00007ffeda5ba200 RCX: 00007f1a874c637b
Jan 28 14:53:35 tom-desktop-linux kernel: RDX: 00007ffeda5ba200 RSI: 0000000040086464 RDI: 000000000000000c
Jan 28 14:53:35 tom-desktop-linux kernel: RBP: 0000000040086464 R08: 00000000000edc2a R09: 0000000000000bb9
Jan 28 14:53:35 tom-desktop-linux kernel: R10: 0000000000000000 R11: 0000000000000246 R12: 0000000000000001
Jan 28 14:53:35 tom-desktop-linux kernel: R13: 000000000000000c R14: 0000558b19c484e0 R15: 0000558b1a94d1d0
Jan 28 14:53:35 tom-desktop-linux kernel: Modules linked in: rfcomm bnep intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp btusb btrtl coretemp btbcm btintel crct10dif_pclmul snd_hda_codec_realtek ghash_clmulni_intel snd_hda_codec_generic bluetooth aesni_intel ledtrig_audio ecdh_generic crypto_simd cryptd ecc input_leds snd_hda_codec_hdmi radeon snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi glue_helper ttm snd_seq_midi_event snd_rawmidi drm_kms_helper snd_seq cec rc_core i2c_algo_bit fb_sys_fops rapl syscopyarea intel_cstate sysfillrect sysimgblt snd_seq_device snd_timer snd soundcore eeepc_wmi asus_wmi sparse_keymap at24 mei_me mei wmi_bmof mac_hid mxm_wmi sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_generic usbhid hid crc32_pclmul i2c_i801 i2c_smbus firewire_ohci lpc_ich firewire_core crc_itu_t ahci libahci xhci_pci e1000e xhci_pci_renesas video wmi
Jan 28 14:53:35 tom-desktop-linux kernel: CR2: ffffaa3140890ffc
Jan 28 14:53:35 tom-desktop-linux kernel: ---[ end trace df2121f8f4442186 ]---
Jan 28 14:53:35 tom-desktop-linux kernel: RIP: 0010:radeon_ring_backup+0xc9/0x140 [radeon]
Jan 28 14:53:35 tom-desktop-linux kernel: Code: ed 49 89 07 48 85 c0 74 7d 41 8d 7d ff 31 d2 48 c1 e7 02 eb 07 49 8b 07 48 83 c2 04 49 8b 74 24 08 8d 4b 01 89 db 48 8d 34 9e <8b> 36 89 34 10 41 23 4c 24 54 89 cb 48 39 d7 75 da 4c 89 f7 e8 ee
Jan 28 14:53:35 tom-desktop-linux kernel: RSP: 0018:ffffaa2d429abc50 EFLAGS: 00010202
Jan 28 14:53:35 tom-desktop-linux kernel: RAX: ffff9ce6b20e0000 RBX: 00000000ffffffff RCX: 0000000000000000
Jan 28 14:53:35 tom-desktop-linux kernel: RDX: 0000000000000000 RSI: ffffaa3140890ffc RDI: 000000000001aa40
Jan 28 14:53:35 tom-desktop-linux kernel: RBP: ffffaa2d429abc78 R08: 00000000000321e7 R09: 0000000000000000
Jan 28 14:53:35 tom-desktop-linux kernel: R10: ffff9ce6b20e0000 R11: 0000000000000020 R12: ffff9ce81bb613d8
Jan 28 14:53:35 tom-desktop-linux kernel: R13: 0000000000006a91 R14: ffff9ce81bb613b8 R15: ffffaa2d429abcb8
Jan 28 14:53:35 tom-desktop-linux kernel: FS:  00007f1a82072cc0(0000) GS:ffff9ce823480000(0000) knlGS:0000000000000000
Jan 28 14:53:35 tom-desktop-linux kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jan 28 14:53:35 tom-desktop-linux kernel: CR2: ffffaa3140890ffc CR3: 00000002e1d54002 CR4: 00000000000606e0
```

-- **Reboot** --

---

### Post by bcschmerker on 2021-01-28
[@oasisforever](https://ubuntuforums.org/member.php?u=632943)  **Some years back, the LinUX Kernel Organization ran into enough trouble with certain GPUs in the Advance Micro Devices® Radeon® HD&#8482; 6000 series to blacklist them;** don't know if that's still the case.  Should I land an ASUS® M3A78-EM to replace a GIGABYTE® GA-MA78GM-S2HP v2.0 that lost the i8042 port on the super-I/O (see "[Hot Rod gPC down, need motherboard](https://ubuntuforums.org/showthread.php?t=2456551)"), I'm fixing to transfer the EAH6850DC/2DIS/1GD5 (Advance Micro Devices Inc. BARTS PRO GPU, 1 GiB GDDR5 VRAM) from the CM1630 as soon as I land a TURBO series VDA for the CM1630 (as the nVIDIA® GM206, GP106, and TU106 are better supported in Microsoft® Windows® 10.0.19043.*nnn* than in LinUX 5.8.0), knowing that I might have to fix what ye've hit.

---

### Post by QIII on 2021-01-29
oasisforever --

Please use the default font and color unless there is something specific or noteworthy in your post to which you want to draw attention.

Also, please enclose all terminal commands and their results in code tags:  

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by mastablasta on 2021-01-29
try stressing it with phroronix test suite. could be a hardware issue. SW or HW - the issue can be on GPU or on motherboard.

edit: measure temp with pasensor and check other logs as well.


Does this chip use radeon or doe sit have AMDGPU drivers available?

radeon switches and kernel options: [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

---

### Post by bcschmerker on 2021-02-18
**Advance Micro Devices' Northern Islands GPU's** (e.g. the BARTS on the EAH6850DC, the CAYMAN PRO on oasisforever's R6950) **use X.org radeon.**  AMDGPU is for the Sea Islands and newer.

---

