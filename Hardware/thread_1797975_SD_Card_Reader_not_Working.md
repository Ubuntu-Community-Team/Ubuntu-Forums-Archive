---
title: "SD Card Reader not Working?"
date: 2011-07-05
forum: Hardware
---

### Post by xandr55 on 2011-07-05
Hi I have a Asus EeePC 1005PE and Xubuntu 11.4 and cannot get an SD card in the internal reader to mount or show up at all even via fdisk -l. Any ideas to get it working?
Thanks

---

### Post by Toz on 2011-07-05
Insert the sd card into the drive. Open a terminal window (Accessories->Terminal Emulator), type in:```
dmesg
``` and post back the last 15-20 lines. Lets see what its picking up.

---

### Post by xandr55 on 2011-07-05
doesn't seem as though it is picking up anything:

```
[   55.050573] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   55.050582] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   55.050589] cfg80211: Disabling freq 2467 MHz
[   55.050594] cfg80211: Disabling freq 2472 MHz
[   55.050599] cfg80211: Disabling freq 2484 MHz
[   55.050614] cfg80211: Regulatory domain changed to country: US
[   55.050620] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   55.050630] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   55.050639] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   55.050648] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   55.050657] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   55.050667] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   55.050675] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   65.392032] wlan0: no IPv6 routers present
[  167.768697] exe (2522): /proc/2522/oom_adj is deprecated, please use /proc/2522/oom_score_adj instead.
```

Tried a couple of times, didn't get any different output.

---

### Post by Toz on 2011-07-05
It doesn't appear to be recognizing it. What do the following commands return:
```
lspci
```
```
lsmod
```

---

### Post by xandr55 on 2011-07-05
Thanks for your help everything seems to be working now, not sure what I did though, just a reboot, though I thought I had done that before. Thanks again.

---

