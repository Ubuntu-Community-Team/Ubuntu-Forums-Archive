---
title: "Slow resume after harddisk upgrade (Seagate Momentus 7200.3)"
date: 2008-08-21
forum: Hardware
---

### Post by KMK_ECS on 2008-08-21
Hi,

since I upgraded the hard disk of my Thinkpad T61 to a Seagate Momentus 7200.3 the system needs a long time to resume after suspending. The message 

[COLOR="Red"]COMRESET failed [/COLOR]

is displayed after several seconds of inactivity. Thereafter, resuming continues normally. Dmesg displays the following error message: 

[COLOR="Red"]kernel: [ 3.647374] ata3: port is slow to respond, please be patient (Status 0x80)[/COLOR]. 

Resuming in Windows Vista works fine without delay. The problem does also not occur in Ubuntu when the SATA controller is set to "Compatibility Mode" (BIOS).

I had a similar problem some time ago with the old hard disk when resuming with activated SATA power management, However, the current problem also occurs when SATA power management is disabled.

I suspect that the hard drive might not be properly recognized by the kernel as dmesg shows only SATA I speed (1.5 GB/s) although to my knowledge both T61 and the Seagate hard disk should support SATA II. NCQ seems to be properly activated. Deactivating it by "echo 1 > /sys/block/sda/device/queue_depth" did not help.

I already reported the problem here: 

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/258736](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/258736) 

but it does not seem to have a high priority :(. Therefore, I am hoping to get help here.

Does anybody have a similar problem and know a workaround? Should the hard disk not be connected with 3 GB/s? Would it be an issue to just change the SATA mode in BIOS to "Compatibility"? 

Many thanks in advance!

Karl Martin

---

