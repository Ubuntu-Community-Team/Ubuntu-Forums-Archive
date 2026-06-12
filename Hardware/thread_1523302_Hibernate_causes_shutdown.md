---
title: "Hibernate causes shutdown"
date: 2010-07-03
forum: Hardware
---

### Post by brianjhu on 2010-07-03
I just cloned the hard drive on my Dell 600m running Ubuntu 8.04 to a   larger one and everything works great - except for hibernation. Now when   I try to hibernate, it appears to work, but when I try to resume, the   system does a cold boot. Hibernate used to work just fine when I was   using the old hard drive.

As far as I can tell, the swap partition (2 G for 1.5 G of RAM) is fine   (free -m shows 1937 for total and free for swap). The following are the  4  lines from /var/log/messages right after telling the system to   hibernate and the first line after hitting the power button to resume:

```

Jul  3 11:02:50 BGPC kernel: [   95.024397] ACPI: PCI interrupt for   device 0000:02:00.0 disabled
Jul  3 11:02:50 BGPC kernel: [   95.060022] ACPI: PCI interrupt for   device 0000:02:03.0 disabled
Jul  3 11:02:51 BGPC kernel: [   95.965945] swsusp: Marking nosave   pages: 000000000009f000 - 0000000000100000
Jul  3 11:02:51 BGPC kernel: [   95.965951] swsusp: Basic memory bitmaps   created
Jul  3 11:04:12 BGPC syslogd 1.5.0#1ubuntu1: restart.

```Perhaps those ACPI messages are the problem?

I have tried to hibernate by closing the lid, selecting it from the   power menu, and running /etc/acpi/hibernate.sh all the the same effect.   Suspend still works fine, but I really need hibernate to work properly.

Thanks for any help.

EDIT:

I was able to fix it. It was one of two things, both of which were based  getting UUIDs up to date after the hard drive swap. First, I edited  /etc/initramfs-tools/conf.d/resume to read the correct UUID for swap  (obtained by doing ls /dev/disk/by-uuid/ -l). I don't think that this  was the fix.

What I think fixed it was to edit the appropriate line in  /boot/grub/menu.lst to read:

```

# defoptions=quiet splash resume=UUID=[new UUID for swap]

```I also added resume=UUID=[new UUID for swap] to the kernel line for the  current kernel and did sudo update-grub. It all works now.

---

