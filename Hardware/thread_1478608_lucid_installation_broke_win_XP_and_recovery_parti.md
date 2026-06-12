---
title: "lucid installation broke win XP and recovery partition"
date: 2010-05-09
forum: Hardware
---

### Post by paradox82 on 2010-05-09
Downloaded lucid final image and installed it on a brand new toshiba mini nb305. Lucid works ok (with a few tweaks in grub) however the process somehow broke the win xp and the recovery partition on the mini.

When booting XP in safe mode it gets to loading "mup.sys" and then flashes with BSOD and reboots (can't read the BSOD it goes by too fast). Any body with similar problems? Is this recoverable or i should assume something went wrong in the resizing of the partitions?

The windows partition reads fine in ubuntu, yet it doesn't boot. Ran programs recoving the MBS, but that didn't help.

I have installed dual-boot ubuntu on at least 5 systems in the past and never seen such predatory behavior.

---

### Post by fiddler616 on 2010-07-10
This exact same thing happened to me, except I installed Crunchbang 9.04 (Ubuntu with Openbox instead of GNOME).

I played around with the recovery partition for a while, and eventually it started working (I have no idea how), so I was able to reinstall XP. However, I really do want it to dualboot, so I was wondering if you'd figured anything out.

Thanks.

---

### Post by garvinrick4 on 2010-07-10
> **paradox82 said:**
> Downloaded lucid final image and installed it on a brand new toshiba mini nb305. Lucid works ok (with a few tweaks in grub) however the process somehow broke the win xp and the recovery partition on the mini.

When booting XP in safe mode it gets to loading "mup.sys" and then flashes with BSOD and reboots (can't read the BSOD it goes by too fast). Any body with similar problems? Is this recoverable or i should assume something went wrong in the resizing of the partitions?

The windows partition reads fine in ubuntu, yet it doesn't boot. Ran programs recoving the MBS, but that didn't help.

I have installed dual-boot ubuntu on at least 5 systems in the past and never seen such predatory behavior. Save this script to desktop and see what is happening to boot.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

