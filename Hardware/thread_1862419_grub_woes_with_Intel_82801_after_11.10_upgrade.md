---
title: "grub woes with Intel 82801 after 11.10 upgrade"
date: 2011-10-16
forum: Hardware
---

### Post by akos.maroy on 2011-10-16
I just upgraded my laptop from ubuntu 11.04 to 11.10, and now, it won't boot. when booting, I'm dropped to the boot rescue prompt, with the message that it cannot find the drive - and then the UUID of the drive it is trying to find.

the same system worked fine with earlier versions of Ubuntu.

the only strange part of the laptop is that it uses an Intel Corporation Mobile 82801 SATA RAID Controller, and that the hard drives are accessible through the raid controller, using the following devices:

[LIST]
[*]/dev/mapper/isw_cdfcbdcfed_RAID-0 - for the whole drive
[*]/dev/mapper/isw_cdfcbdcfed_RAID-0pX - for partition X
[/LIST]

to mitigate the issue, I've tried the following:

boot with the install CD, chroot into the hard drive (works fine), then purge & re-install grub-pc

use the Boot-Repair CD, and try to re-install grub with that. from this, I have the following boot info recorded: [http://paste.debian.net/137168](http://paste.debian.net/137168)

in both cases, the results are the same :(




I wonder what could be wrong here? might it be that grub with ubuntu 11.10 doesn't work with this controller, even though the old version did?

---

