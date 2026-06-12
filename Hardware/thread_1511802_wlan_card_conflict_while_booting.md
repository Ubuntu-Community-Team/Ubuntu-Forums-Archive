---
title: "wlan card conflict while booting"
date: 2010-06-17
forum: Hardware
---

### Post by 2weird2die on 2010-06-17
Here is my problem: After I have turned on my notebook and chose OS, my ubuntu studio 10.04 started to boot, but after a while I got this error:

[28.410249] ACPI: I/0 rsource piix_smbus conflicts with ACPI region SMBO  [28.650662] Ath5k phy0: cant register ieee80211 hw

and

[28.204249]  ath5k phy0: cant register ieee80211 [hwxb07] conflicts with ACPI region  SMBO [0xb00-0xb0f] 

there was no update/major changes in settings during the last use.

I did turn of my atheros AR5007EG wlan card and other devices off in BIOS and it didnt help. I dont know how to solve this problem, everything was working fine for 5 months and there is no problem with my wlan under windows. :(
I have ASUS F5RL (budget notebook) with:
Intel Pentium T2390 1866MHz
Ati radeon xpress 1100
3GB DDR2 SDRAM
320 GB SATA 2 HDD
above mentioned Atheros AR5007EG wireless network adapter
bios version: Amibios 210

+ is there any command how to block wlan card before booting?
+ eventually - how can I make ext2 image from win before any attempts? (I don't wanna cause damage to data I have on my disk and my files are encrypted, so I don't know how to access them from win)

I will be very thankful for any suggestion and help.

---

### Post by 2weird2die on 2010-06-17
Every time I've tried to run recovery I got this:

udevd-work [3817]: exec of program '/sbin/blkid' failed
udevd-work [3818]: exec of program '/lib/dev/udisks-part-part-id' failed
init: Failed to spawn cryptdisks-enable main process: unable to execute: Permission denied
udevd-work [3820]: exec of program '/sbin/modprobe' failed
udevd-work [3824]: exec of program '/lib/udev/input_id' failed
udevd-work [3824]: exec of program '/lib/udev/input_id' failed
udevd-work [3824]: exec of program '/lib/udev/path_id' failed
udevd-work [3823]: exec of program '/lib/udev/path_id' failed
.
.
.
but I dont know where can I get full log and logs what you need to help me.

Please, need help with this problem. :(

---

