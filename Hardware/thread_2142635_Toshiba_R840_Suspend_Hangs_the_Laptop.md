---
title: "Toshiba R840 Suspend Hangs the Laptop"
date: 2013-05-06
forum: Hardware
---

### Post by peshko-lnx on 2013-05-06
Fresh install on Toshiba R840. No other software installed. I put the laptop to suspend or the laptops goes to suspend mode after 10 minutes of inactivity. Coming back from suspend, Ubuntu tries to wake up the laptop, but the screen never comes on, and the laptop hangs. The only solution is hard reset.

How to diagnose and fix the problem? Windows 7 works great when sleeping the laptop.

Thanks!

---

### Post by peshko-lnx on 2013-05-06
For some reason it put a tag of gobuntu. This is NOT gobuntu. It is plain Ubuntu

---

### Post by Toz on 2013-05-06
> **peshko-lnx said:**
> For some reason it put a tag of gobuntu. This is NOT gobuntu. It is plain Ubuntu

To change the prefix, click on the "Edit" button in your first post, then click "Go Advanced", then change the Prefix and click on "Save"

---

### Post by Toz on 2013-05-06
> **peshko-lnx said:**
> Fresh install on Toshiba R840. No other software installed. I put the laptop to suspend or the laptops goes to suspend mode after 10 minutes of inactivity. Coming back from suspend, Ubuntu tries to wake up the laptop, but the screen never comes on, and the laptop hangs. The only solution is hard reset.

How to diagnose and fix the problem? Windows 7 works great when sleeping the laptop.

Thanks!

Can you provide some more information? Specifically:

1. The contents of your /var/log/pm-suspend.log file like this:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

2. The results of the following command:
```
cat /var/log/syslog | grep PM:
```

3. Your current kernel boot line:
```
cat /proc/cmdline
```

4. Information about your video card and drivers:
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by peshko-lnx on 2013-05-06
1. The contents of your /var/log/pm-suspend.log file like this:
```
pastebinit /var/log/pm-suspend.log

[http://paste.ubuntu.com/5638804/](http://paste.ubuntu.com/5638804/)
```

2. The results of the following command:
```
cat /var/log/syslog | grep PM:

peter@laptop-lnx:~$ cat /var/log/syslog | grep PM:
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000aa5d0000 - 00000000aa5d1000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000aa5d1000 - 00000000aa5d3000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000aa5d3000 - 00000000aa6d0000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000aa6d0000 - 00000000aa6f0000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000aa6f0000 - 00000000afa00000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000afa00000 - 00000000f8000000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
May  6 08:19:14 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
May  6 08:19:14 laptop-lnx kernel: [    0.109301] PM: Registering ACPI NVS region [mem 0xaa5d0000-0xaa5d01ff] (512 bytes)
May  6 08:19:14 laptop-lnx kernel: [    0.109302] PM: Registering ACPI NVS region [mem 0xaa5d3000-0xaa6cffff] (1036288 bytes)
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000aa5d0000 - 00000000aa5d1000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000aa5d1000 - 00000000aa5d3000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000aa5d3000 - 00000000aa6d0000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000aa6d0000 - 00000000aa6f0000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000aa6f0000 - 00000000afa00000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000afa00000 - 00000000f8000000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
May  6 08:21:01 laptop-lnx kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
May  6 08:21:01 laptop-lnx kernel: [    0.109294] PM: Registering ACPI NVS region [mem 0xaa5d0000-0xaa5d01ff] (512 bytes)
May  6 08:21:01 laptop-lnx kernel: [    0.109296] PM: Registering ACPI NVS region [mem 0xaa5d3000-0xaa6cffff] (1036288 bytes)
```

3. Your current kernel boot line:
```
cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=e7e41ef0-0fbc-47b4-937a-8a30665a404e ro quiet splash vt.handoff=7
```

4. Information about your video card and drivers:
```
sudo lspci -vnn | grep -A12 VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:0004]
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
```

Thank you very much for looking into this!

---

### Post by Toz on 2013-05-06
Nothing in your log files. Found this upstream bug report ([https://bugzilla.kernel.org/show_bug.cgi?id=42977]("https://bugzilla.kernel.org/show_bug.cgi?id=42977")). A reported workaround is to use the **acpi_sleep=s3_beep** kernel boot parameter (feel free to read about the rationale for this parameter and the progress in fixing the bug, in the bug report).

To use the parameter, have a look at the "Kernel Boot Parameters" link in my signature.

---

### Post by peshko-lnx on 2013-05-06
> **Toz said:**
> Nothing in your log files. Found this upstream bug report ([https://bugzilla.kernel.org/show_bug.cgi?id=42977](https://bugzilla.kernel.org/show_bug.cgi?id=42977)). A reported workaround is to use the **acpi_sleep=s3_beep** kernel boot parameter (feel free to read about the rationale for this parameter and the progress in fixing the bug, in the bug report).

To use the parameter, have a look at the "Kernel Boot Parameters" link in my signature.

I implemented the acpi_sleep=s3_beep, but that did not help. Still the same issue. The moment I try to bring it from suspend, the display never comes up, and in a couple of seconds the fan starts spinning like crazy. Also, there is a failure detection and the crash report generates apport with a title Sorry, Ubuntu 13.04 experienced an internal error...

Should I file a bug?

Thanks!

---

### Post by Toz on 2013-05-06
With acpi_sleep=s3_beep enabled, can you post back:
```
cat /proc/cmdline
```
...and the contents of /var/log/pm-suspend.log via:
```
pastebinit /var/log/pm-suspend.log
```

Looks like a bug already exists: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/962142]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/962142").

---

### Post by peshko-lnx on 2013-05-06
I am attacing the crash report from the resume.[ATTACH]242264[/ATTACH] I am not sure if that would be helpful...

---

### Post by peshko-lnx on 2013-05-06
[QUOTE=Toz;12636214]With acpi_sleep=s3_beep enabled, can you post back:
```
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=e7e41ef0-0fbc-47b4-937a-8a30665a404e ro quiet splash acpi_sleep=s3_beep vt.handoff=7
```

```
pastebinit /var/log/pm-suspend.log
http://paste.ubuntu.com/5639217/
```

---

### Post by Toz on 2013-05-06
Upon further reivew of [https://bugzilla.kernel.org/show_bug.cgi?id=42977]("https://bugzilla.kernel.org/show_bug.cgi?id=42977"), it appears that the problem exists only on the 64-bit kernels (which you are using). There is some mention of the built-in udelay in acpi_sleep=s3-beep being a valid workaround, that doesn't appear to work for you.

Your best course of action may be to follow/subscribe/comment in that bug report.

An "out in left field" suggestion would be to try the "acpi_osi=\"!Windows 2012\" kernel boot parameter (like this in /etc/default/grub):
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```
...to explicitly tell the bios that you are not Windows 8 to see if it loads a different set of acpi tables that __may__ affect suspend functionality.

---

### Post by peshko-lnx on 2013-05-06
I tried the last straw and it didn't work...Oh well. I will wait for the fix to the upstream bug...

---

