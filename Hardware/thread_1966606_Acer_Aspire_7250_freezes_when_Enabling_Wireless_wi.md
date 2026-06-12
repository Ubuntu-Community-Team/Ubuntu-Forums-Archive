---
title: "Acer Aspire 7250 freezes when Enabling Wireless with Atheros AR9485"
date: 2012-04-27
forum: Hardware
---

### Post by janmartin on 2012-04-27
Hi all,

I have this new Laptop:

Acer Aspire 7250
AMD Dual-Core-Processor E300
17.3 " HD + LED LCD
AMD Radeon HD 6310
8 GB DDR3 Memory
500 GB HDD
DVD-Super Multi DL drive
Acer Nplify 802.11 b/g/n
6-cell Li-ion battery

Running 64bit Ubuntu 12.04:
kernel: 3.2.0-24-generic

When ever I am clicking "Enable Wireless" the laptop freezes immediately.
I then need to press the ON/OFF button to restart.

Someone please help.
In older threads it is suggested that "Turn on Network boot in BIOS" might help, but it does not change anything.

lspci -k:

06:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
	Subsystem: Lite-On Communications Inc Device 6617
	Kernel driver in use: ath9k
	Kernel modules: ath9k

dmesg:

[   12.279014] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.279072] ath9k 0000:06:00.0: setting latency timer to 64
[   12.290070] ath: EEPROM regdomain: 0x65
[   12.290078] ath: EEPROM indicates we should expect a direct regpair map
[   12.290087] ath: Country alpha2 being used: 00
[   12.290091] ath: Regpair used: 0x65
[   12.290731] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.290742] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290747] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.290753] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290758] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.290764] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290769] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.290775] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290780] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.290786] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290790] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.290796] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290801] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.290806] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290811] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.290817] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290821] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.290827] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290832] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.290838] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290842] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.290848] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290853] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   12.290858] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290863] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   12.290869] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.290874] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   12.295031] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   12.314656] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.316637] Registered led device: ath9k-phy0
[   12.316669] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90005a80000, irq=17
[   12.612571] init: failsafe main process (779) killed by TERM signal
[   12.747420] type=1400 audit(1335515214.867:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=868 comm="apparmor_parser"
[   12.755276] type=1400 audit(1335515214.875:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=868 comm="apparmor_parser"
[   12.755772] type=1400 audit(1335515214.875:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=868 comm="apparmor_parser"
[   12.757052] type=1400 audit(1335515214.879:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=867 comm="apparmor_parser"
[   12.777234] type=1400 audit(1335515214.899:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=871 comm="apparmor_parser"

---

### Post by Benno von Archimboldi on 2012-05-05
I have the same problem... help please

---

### Post by janmartin on 2012-05-05
Workaround by disabling the Ethernet controller for wired connection:

[http://ubuntuforums.org/showpost.php?p=11886778&postcount=7](http://ubuntuforums.org/showpost.php?p=11886778&postcount=7)

---

### Post by UbiracyMafra on 2012-07-03
Thank you, solved issue.

---

