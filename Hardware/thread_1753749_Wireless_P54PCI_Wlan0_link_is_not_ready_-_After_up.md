---
title: "Wireless P54PCI: Wlan0: link is not ready - After upgrade to 11.04"
date: 2011-05-09
forum: Hardware
---

### Post by gcmelzi on 2011-05-09
Hello team. 
The card was working on 10.10, after installation of the linux-firmware-nonfree package. 
After upgrade to 11.04 (fresh install because of other problems) I'm not able to get it working. 
From dmesg: 
```

[   30.496781] cfg80211: World regulatory domain updated:
[   30.496793] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   30.496798] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   30.496804] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   30.496808] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   30.496813] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   30.496818] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   30.570797] usbcore: registered new interface driver uas
[   30.851736] p54pci 0000:02:02.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19

[   30.983204] ieee80211 phy0: p54 detected a LM86 firmware
[   30.983214] p54: rx_mtu reduced from 3240 to 2376
[   30.983218] ieee80211 phy0: FW rev 2.13.12.0 - Softmac protocol 5.9
[   30.983224] ieee80211 phy0: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES

[   31.935506] ieee80211 phy0: hwaddr 00:60:b3:08:0e:03, MAC:isl3890 RF:Frisbee
[   31.938356] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   31.938364] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938368] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   31.938373] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938378] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   31.938383] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938387] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   31.938392] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938396] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   31.938401] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938405] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   31.938410] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938414] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   31.938419] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938424] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   31.938429] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938433] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   31.938438] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938442] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   31.938447] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938453] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   31.938458] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938462] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   31.938467] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938471] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   31.938476] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   31.938480] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   31.938485] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)

[   32.107524] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   32.115329] Registered led device: p54-phy0::assoc
[   32.115669] Registered led device: p54-phy0::tx
[   32.115943] Registered led device: p54-phy0::rx
[   32.117017] Registered led device: p54-phy0::radio
[   32.117049] p54pci 0000:02:02.0: is registered as 'phy0'
[   32.597233] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```
Card doesn't appear on network Manager, while it's visible if I code ```
ifconfig
``` or ```
iwconfig
```
I don't have any idea on what I should do now.

---

### Post by gcmelzi on 2011-05-10
It didn't work at all: I was able to get the SSID recognized, but very low level and never connected. It seems to be a driver problem. 
As there were other problems I gave up and turned back to 10.10: it works perfectly.

---

### Post by bginard on 2011-05-21
I had the same problem and it seems to be the driver p54pci. I replaced by the old one and it's working now.

Just edit /etc/modprobe.d/blacklist.conf and comment the line that blacklists prism54 and blacklist p54pci:
```

# replaced byp54pci
# blacklist prism54
blacklist p54pci

```Regards

---

