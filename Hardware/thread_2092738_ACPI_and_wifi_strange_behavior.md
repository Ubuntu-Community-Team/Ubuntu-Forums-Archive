---
title: "ACPI and wifi strange behavior"
date: 2012-12-08
forum: Hardware
---

### Post by editheraven on 2012-12-08
I am using ubuntu 12.10 on my laptop and dmesg shows quite strange things about acpi and wi fi hardware.

```
.........

[   14.423777] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   14.423779] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423781] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   14.423783] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423785] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   14.423787] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423789] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   14.423791] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423792] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   14.423794] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423796] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   14.423798] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423799] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   14.423801] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423803] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   14.423805] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423806] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   14.423808] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423810] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   14.423812] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423814] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   14.423816] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423817] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   14.423819] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423821] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   14.423823] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.423824] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   14.423826] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.634635] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   14.634641] cfg80211: World regulatory domain updated:
[   14.634642] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.634645] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.634647] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.634649] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.634651] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.634652] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.564207] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[   15.564216] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff88014924bfc8), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[   15.564228] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff88014924c870), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[   15.568042] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20120320/dsopcode-236)
[   15.568051] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff88014924bfc8), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[   15.568063] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff88014924c870), AE_AML_BUFFER_LIMIT (20120320/psparse-536)

```


Is the ACPI behavior normal? Why the wifi configs its range of frequencies at boot time?

Thanx.

---

### Post by editheraven on 2012-12-09
Anyone?

---

### Post by johnycsf on 2012-12-09
That is very strange. But if it is booting up fine and your wifi works I wouldn't worry about it.

---

### Post by editheraven on 2012-12-09
Well it works but i also want to know what those messages mean. That's why I use linux, because i wanna now whys and hows.

---

