---
title: "USB flash drive freezes Xubuntu 14.04"
date: 2014-10-03
forum: Hardware
---

### Post by Samppa_Linna on 2014-10-03
I have a ThinkPad W530 which I recently updated from Xubuntu 12.04 (which worked fine) to 14.04. Now accessing a USB flash drive tends to freeze the computer. It's a complete freeze - keyboard is dead and screen does not update. It will not resolve by itself; only thing to do is to keep the power button pressed long enough to reboot the computer. The last relevant things (and often the last things in general) logged in kernel.log and syslog before the reboot are the following:

Oct  3 13:07:42 COMPNAME kernel: [  711.507243] scsi 7:0:0:0: Direct-Access     PNY      USB 2.0 FD       8192 PQ: 0 ANSI: 4
Oct  3 13:07:42 COMPNAME kernel: [  711.507607] sd 7:0:0:0: Attached scsi generic sg2 type 0
Oct  3 13:07:42 COMPNAME kernel: [  711.508419] sd 7:0:0:0: [sdb] 15826944 512-byte logical blocks: (8.10 GB/7.54 GiB)
Oct  3 13:07:42 COMPNAME kernel: [  711.509339] sd 7:0:0:0: [sdb] Write Protect is off
Oct  3 13:07:42 COMPNAME kernel: [  711.509347] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
Oct  3 13:07:42 COMPNAME kernel: [  711.510335] sd 7:0:0:0: [sdb] No Caching mode page found
Oct  3 13:07:42 COMPNAME kernel: [  711.510341] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Oct  3 13:07:42 COMPNAME kernel: [  711.514712] sd 7:0:0:0: [sdb] No Caching mode page found
Oct  3 13:07:42 COMPNAME kernel: [  711.514716] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Oct  3 13:07:42 COMPNAME kernel: [  711.515816]  sdb: sdb1
Oct  3 13:07:42 COMPNAME kernel: [  711.519332] sd 7:0:0:0: [sdb] No Caching mode page found
Oct  3 13:07:42 COMPNAME kernel: [  711.519337] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Oct  3 13:07:42 COMPNAME kernel: [  711.519341] sd 7:0:0:0: [sdb] Attached SCSI removable disk

Thus, I don't have an idea what could be wrong. This seems to happen with all the USB connectors, including those on the monitor. Furthermore, this has happened with multiple USB flash drives but not with a USB hard disk. Just in case it is relevant, video driver package is nvidia-331-updates.
Any ideas?

---

### Post by Thpn on 2015-02-28
In my experience, upgrades are fraught with peril. I always transfer my files and do a fresh install of the latest LTS release every two years, with a complete storage reformat. Something else that's fraught with peril is binary drivers. I hope sharing my experience is helpful.

---

