---
title: "partition uuid loss after resume failure"
date: 2009-08-01
forum: Hardware
---

### Post by jabley on 2009-08-01
I tried to suspend and resume my laptop (Dell Latitude D820) to see if a [problem I've reported with it]("https://bugs.launchpad.net/ubuntu/+bug/390392") has started working recently. Instead, pain.

Resume didn't work, as before. I left it 10 minutes then hard reset and booted up. This went into initramfs with a message about /dev/disk/by-uuid/275d2407-f5a0-49f0-8bcd-3547cd1d78ea not existing.

I looked at /dev/disk/by-uuid. There were symlinks for /boot on /dev/sda1, /homne on /dev/sda2 and swap on /dev/sda4, but / on /dev/sda2 was missing.

$ cd /dev/disk/by-uuid
$ ln -s ../../sda2 275d2407-f5a0-49f0-8bcd-3547cd1d78ea
$ exit

This then booted up normally.

When I shutdown and start or reboot, I get the same thing happening. I can boot up using the process above each time, but it's annoying. So, how to fix that?

$ sudo vol_id /dev/sda1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=aceb35ce-0750-4330-abe3-9bcfe1dc083b
ID_FS_UUID_ENC=aceb35ce-0750-4330-abe3-9bcfe1dc083b
ID_FS_LABEL=
ID_FS_LABEL_ENC=

$ sudo vol_id /dev/sda2
ID_FS_USAGE=raid
ID_FS_TYPE=jmicron_raid_member
ID_FS_VERSION=112.20
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=
ID_FS_LABEL_ENC=

I don't know why that says raid; it should be ext3 with uuid set, etc.

I've tried reinstalling the kernel via aptitude in the hope that would run all of the necessary post-install hooks to generate the right settings, but get the same result when booting up. Presumably, I just need to fix it so that the uuid is correctly associated with /dev/sda2, but I haven't figured out how to do that?

---

