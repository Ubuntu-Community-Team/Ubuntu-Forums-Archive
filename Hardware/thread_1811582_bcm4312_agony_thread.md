---
title: "bcm4312 agony thread"
date: 2011-07-25
forum: Hardware
---

### Post by lessless on 2011-07-25
Just maybe somebody can help ? 
```
[  216.384025] eth0: no IPv6 routers present
[  292.180127] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  297.740887] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  301.090166] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  301.091833] wlan0: authenticated
[  301.092642] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  301.094845] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  301.094851] wlan0: associated
[  301.095843] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  304.008335] e100 0000:02:08.0: eth0: NIC Link is Down
[  305.109222] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  305.110123] cfg80211: All devices are disconnected, going to restore regulatory settings
[  305.110128] cfg80211: Restoring regulatory settings
[  305.110133] cfg80211: Calling CRDA to update world regulatory domain
[  305.260196] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  305.260201] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260204] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  305.260208] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260211] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  305.260214] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260217] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  305.260220] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260223] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  305.260226] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260229] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  305.260232] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260235] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  305.260238] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260241] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  305.260244] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260247] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  305.260251] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260253] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  305.260257] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260259] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  305.260263] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260266] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  305.260269] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260272] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  305.260275] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260278] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  305.260282] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  305.260285] cfg80211: World regulatory domain updated:
[  305.260288] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  305.260291] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  305.260295] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  305.260298] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  305.260302] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  305.260305] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  306.497019] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  306.498634] wlan0: authenticated
[  306.498656] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  306.501093] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  306.501097] wlan0: associated
[  310.511055] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  310.511952] cfg80211: All devices are disconnected, going to restore regulatory settings
[  310.511958] cfg80211: Restoring regulatory settings
[  310.511963] cfg80211: Calling CRDA to update world regulatory domain
[  310.518874] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  310.518880] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518883] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  310.518887] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518890] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  310.518893] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518896] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  310.518899] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518902] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  310.518905] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518908] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  310.518911] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518914] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  310.518917] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518920] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  310.518924] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518926] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  310.518930] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518932] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  310.518936] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518938] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  310.518942] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518945] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  310.518948] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518951] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  310.518954] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518957] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  310.518960] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  310.518964] cfg80211: World regulatory domain updated:
[  310.518966] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  310.518970] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  310.518973] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  310.518977] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  310.518980] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  310.518983] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  311.152042] wlan0: no IPv6 routers present
[  311.896963] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  311.898550] wlan0: authenticated
[  311.899075] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  311.902268] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  311.902273] wlan0: associated
[  315.921868] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  315.922763] cfg80211: All devices are disconnected, going to restore regulatory settings
[  315.922768] cfg80211: Restoring regulatory settings
[  315.922772] cfg80211: Calling CRDA to update world regulatory domain
[  315.929884] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  315.929890] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929894] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  315.929897] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929900] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  315.929904] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929906] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  315.929952] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929955] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  315.929958] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929961] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  315.929964] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929967] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  315.929971] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929974] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  315.929977] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929980] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  315.929983] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929986] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  315.929990] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929992] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  315.929996] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.929999] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  315.930002] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.930005] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  315.930008] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.930011] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  315.930015] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  315.930018] cfg80211: World regulatory domain updated:
[  315.930020] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  315.930024] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  315.930027] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  315.930031] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  315.930034] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  315.930037] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  317.305271] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  317.306845] wlan0: authenticated
[  317.307382] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  317.309434] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  317.309440] wlan0: associated
[  321.293430] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  321.294319] cfg80211: All devices are disconnected, going to restore regulatory settings
[  321.294324] cfg80211: Restoring regulatory settings
[  321.294329] cfg80211: Calling CRDA to update world regulatory domain
[  321.301529] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  321.301534] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301538] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  321.301541] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301544] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  321.301548] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301551] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  321.301554] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301557] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  321.301561] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301564] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  321.301567] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301570] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  321.301573] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301576] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  321.301580] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301583] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  321.301586] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301589] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  321.301592] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301595] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  321.301598] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301601] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  321.301605] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301607] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  321.301611] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301614] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  321.301617] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  321.301621] cfg80211: World regulatory domain updated:
[  321.301623] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  321.301627] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  321.301630] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  321.301633] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  321.301636] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  321.301639] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  322.677006] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  322.876160] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 2)
[  323.076056] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 3)
[  323.276064] wlan0: authentication with bc:ae:c5:c7:98:40 timed out
[  328.639669] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  340.240908] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  340.440065] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 2)
[  340.441545] wlan0: authenticated
[  340.448187] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  340.451427] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  340.451433] wlan0: associated
[  344.449159] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  344.449956] cfg80211: All devices are disconnected, going to restore regulatory settings
[  344.449961] cfg80211: Restoring regulatory settings
[  344.449966] cfg80211: Calling CRDA to update world regulatory domain
[  344.458250] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  344.458256] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458260] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  344.458263] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458266] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  344.458269] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458272] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  344.458276] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458278] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  344.458282] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458285] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  344.458288] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458291] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  344.458295] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458297] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  344.458301] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458304] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  344.458307] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458310] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  344.458313] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458316] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  344.458319] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458322] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  344.458326] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458329] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  344.458332] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458335] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  344.458339] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  344.458342] cfg80211: World regulatory domain updated:
[  344.458344] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  344.458348] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  344.458352] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  344.458355] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  344.458358] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  344.458362] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  345.836821] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  345.841128] wlan0: authenticated
[  345.841614] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  345.844766] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  345.844772] wlan0: associated
[  349.850532] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  349.851298] cfg80211: All devices are disconnected, going to restore regulatory settings
[  349.851302] cfg80211: Restoring regulatory settings
[  349.851307] cfg80211: Calling CRDA to update world regulatory domain
[  349.858494] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  349.858500] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858503] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  349.858507] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858510] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  349.858513] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858516] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  349.858520] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858522] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  349.858526] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858529] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  349.858532] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858535] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  349.858539] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858541] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  349.858545] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858548] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  349.858551] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858554] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  349.858558] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858561] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  349.858564] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858567] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  349.858570] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858573] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  349.858577] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858580] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  349.858584] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  349.858587] cfg80211: World regulatory domain updated:
[  349.858589] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  349.858593] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  349.858596] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  349.858600] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  349.858603] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  349.858606] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  351.232928] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  351.236564] wlan0: authenticated
[  351.237051] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  351.242035] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  351.242041] wlan0: associated
[  355.231694] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  355.232522] cfg80211: All devices are disconnected, going to restore regulatory settings
[  355.232526] cfg80211: Restoring regulatory settings
[  355.232532] cfg80211: Calling CRDA to update world regulatory domain
[  355.244629] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  355.244635] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244638] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  355.244642] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244645] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  355.244648] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244651] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  355.244654] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244657] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  355.244660] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244663] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  355.244666] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244669] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  355.244672] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244675] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  355.244678] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244681] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  355.244684] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244687] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  355.244691] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244693] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  355.244697] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244700] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  355.244703] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244706] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  355.244709] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244712] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  355.244716] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  355.244719] cfg80211: World regulatory domain updated:
[  355.244722] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  355.244761] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  355.244765] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  355.244769] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  355.244772] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  355.244775] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  356.616844] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  356.816065] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 2)
[  357.016053] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 3)
[  357.216063] wlan0: authentication with bc:ae:c5:c7:98:40 timed out
[  363.060791] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 1/3)
[  363.260062] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 2/3)
[  363.460065] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 3/3)
[  363.660060] wlan0: direct probe to bc:ae:c5:c7:98:40 timed out
[  374.345008] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 1/3)
[  374.351772] wlan0: direct probe responded
[  374.351790] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  374.353531] wlan0: authenticated
[  374.354015] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  374.359635] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  374.359641] wlan0: associated
[  378.367072] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  378.367881] cfg80211: All devices are disconnected, going to restore regulatory settings
[  378.367886] cfg80211: Restoring regulatory settings
[  378.367891] cfg80211: Calling CRDA to update world regulatory domain
[  378.377009] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  378.377014] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377018] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  378.377021] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377024] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  378.377028] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377031] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  378.377034] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377037] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  378.377041] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377043] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  378.377047] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377050] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  378.377053] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377056] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  378.377059] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377062] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  378.377066] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377068] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  378.377072] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377075] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  378.377078] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377081] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  378.377085] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377088] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  378.377091] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377094] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  378.377098] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  378.377101] cfg80211: World regulatory domain updated:
[  378.377104] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  378.377107] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  378.377110] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  378.377114] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  378.377117] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  378.377120] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  379.752801] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  379.758792] wlan0: authenticated
[  379.759280] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  379.764769] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  379.764774] wlan0: associated
[  383.768363] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  383.769187] cfg80211: All devices are disconnected, going to restore regulatory settings
[  383.769193] cfg80211: Restoring regulatory settings
[  383.769199] cfg80211: Calling CRDA to update world regulatory domain
[  383.776909] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  383.776915] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776919] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  383.776922] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776925] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  383.776929] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776932] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  383.776935] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776938] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  383.776941] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776944] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  383.776948] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776951] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  383.776954] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776957] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  383.776960] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776963] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  383.776967] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776969] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  383.776973] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776976] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  383.776980] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776982] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  383.776986] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776989] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  383.776992] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.776995] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  383.776999] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  383.777002] cfg80211: World regulatory domain updated:
[  383.777004] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  383.777008] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  383.777011] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  383.777023] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  383.777026] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  383.777030] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  385.156802] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  385.159237] wlan0: authenticated
[  385.159733] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  385.162566] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  385.162572] wlan0: associated
[  389.179633] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  389.180433] cfg80211: All devices are disconnected, going to restore regulatory settings
[  389.180438] cfg80211: Restoring regulatory settings
[  389.180443] cfg80211: Calling CRDA to update world regulatory domain
[  389.186921] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  389.186927] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186931] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  389.186934] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186937] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  389.186940] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186943] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  389.186947] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186949] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  389.186953] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186955] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  389.186959] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186961] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  389.186965] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186967] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  389.186971] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186973] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  389.186977] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186980] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  389.186983] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186986] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  389.186989] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186992] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  389.186996] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.186999] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  389.187002] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.187005] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  389.187009] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  389.187012] cfg80211: World regulatory domain updated:
[  389.187014] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  389.187018] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  389.187021] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  389.187025] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  389.187028] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  389.187031] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  390.564800] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  390.566285] wlan0: authenticated
[  390.566767] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  390.572942] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  390.572948] wlan0: associated
[  394.591050] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  394.591832] cfg80211: All devices are disconnected, going to restore regulatory settings
[  394.591837] cfg80211: Restoring regulatory settings
[  394.591842] cfg80211: Calling CRDA to update world regulatory domain
[  394.598505] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  394.598511] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598515] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  394.598518] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598521] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  394.598525] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598528] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  394.598531] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598534] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  394.598538] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598541] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  394.598544] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598547] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  394.598550] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598553] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  394.598557] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598560] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  394.598563] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598566] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  394.598569] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598573] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  394.598576] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598579] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  394.598583] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598586] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  394.598589] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598592] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  394.598596] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  394.598599] cfg80211: World regulatory domain updated:
[  394.598602] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  394.598605] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  394.598609] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  394.598612] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  394.598615] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  394.598618] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  395.976681] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  395.978158] wlan0: authenticated
[  395.978633] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  395.991446] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  395.991452] wlan0: associated
[  400.012361] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  400.013139] cfg80211: All devices are disconnected, going to restore regulatory settings
[  400.013143] cfg80211: Restoring regulatory settings
[  400.013148] cfg80211: Calling CRDA to update world regulatory domain
[  400.020453] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  400.020459] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020463] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  400.020466] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020469] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  400.020473] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020475] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  400.020478] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020481] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  400.020484] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020487] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  400.020490] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020493] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  400.020496] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020499] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  400.020502] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020505] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  400.020508] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020511] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  400.020514] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020517] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  400.020521] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020524] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  400.020527] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020530] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  400.020533] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020536] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  400.020539] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  400.020542] cfg80211: World regulatory domain updated:
[  400.020544] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  400.020548] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  400.020551] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  400.020554] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  400.020558] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  400.020561] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  401.396839] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  401.596069] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 2)
[  401.796074] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 3)
[  401.996067] wlan0: authentication with bc:ae:c5:c7:98:40 timed out
[  412.680798] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  412.682282] wlan0: authenticated
[  412.682776] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  412.684784] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  412.684790] wlan0: associated
[  416.686359] wlan0: deauthenticated from bc:ae:c5:c7:98:40 (Reason: 15)
[  416.687164] cfg80211: All devices are disconnected, going to restore regulatory settings
[  416.687169] cfg80211: Restoring regulatory settings
[  416.687175] cfg80211: Calling CRDA to update world regulatory domain
[  416.700464] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  416.700471] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700474] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  416.700477] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700480] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  416.700484] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700487] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  416.700490] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700493] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  416.700496] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700499] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  416.700503] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700505] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  416.700509] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700512] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  416.700515] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700518] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  416.700521] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700524] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  416.700528] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700531] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  416.700534] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700537] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  416.700540] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700543] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  416.700547] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700550] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  416.700553] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  416.700557] cfg80211: World regulatory domain updated:
[  416.700559] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  416.700563] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  416.700566] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  416.700570] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  416.700573] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  416.700576] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  418.069044] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  418.268029] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 2)
[  418.271947] wlan0: authenticated
[  418.272650] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  418.472056] wlan0: associate with bc:ae:c5:c7:98:40 (try 2)
[  418.475278] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  418.475283] wlan0: associated
[  422.006837] wlan0: deauthenticating from bc:ae:c5:c7:98:40 by local choice (reason=3)
[  422.020126] cfg80211: All devices are disconnected, going to restore regulatory settings
[  422.020134] cfg80211: Restoring regulatory settings
[  422.020410] cfg80211: Calling CRDA to update world regulatory domain
[  422.027879] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  422.027885] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027888] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  422.027891] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027894] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  422.027898] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027900] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  422.027904] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027906] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  422.027910] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027912] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  422.027916] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027918] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  422.027922] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027924] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  422.027928] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027930] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  422.027934] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027937] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  422.027940] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027943] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  422.027946] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027949] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  422.027952] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027955] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  422.027958] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027961] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  422.027964] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  422.027968] cfg80211: World regulatory domain updated:
[  422.027970] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  422.027973] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  422.027977] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  422.027980] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  422.027983] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  422.027986] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  432.031094] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  432.033405] wlan0: authenticated
[  432.033904] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  432.038674] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  432.038681] wlan0: associated
[  432.188473] Intel AES-NI instructions are not detected.
[  432.226200] padlock_aes: VIA PadLock not detected.
[  447.505057] ieee80211 phy0: wlan0: No probe response from AP bc:ae:c5:c7:98:40 after 500ms, disconnecting.
[  447.505770] cfg80211: All devices are disconnected, going to restore regulatory settings
[  447.505775] cfg80211: Restoring regulatory settings
[  447.505780] cfg80211: Calling CRDA to update world regulatory domain
[  447.513854] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  447.513859] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513863] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  447.513866] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513869] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  447.513873] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513875] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  447.513879] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513882] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  447.513885] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513888] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  447.513891] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513894] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  447.513898] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513900] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  447.513904] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513907] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  447.513911] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513913] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  447.513917] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513920] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  447.513923] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513926] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  447.513930] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513933] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  447.513936] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513939] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  447.513942] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  447.513946] cfg80211: World regulatory domain updated:
[  447.513948] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  447.513952] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  447.513955] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  447.513958] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  447.513962] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  447.513965] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  448.888839] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  449.088040] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 2)
[  449.288040] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 3)
[  449.488041] wlan0: authentication with bc:ae:c5:c7:98:40 timed out
[  460.176711] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 1/3)
[  460.376050] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 2/3)
[  460.576166] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 3/3)
[  460.776043] wlan0: direct probe to bc:ae:c5:c7:98:40 timed out
[  464.504756] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 1/3)
[  464.704322] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 2/3)
[  464.904041] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 3/3)
[  465.104050] wlan0: direct probe to bc:ae:c5:c7:98:40 timed out
[  475.792938] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 1/3)
[  475.992067] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 2/3)
[  476.192067] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 3/3)
[  476.392058] wlan0: direct probe to bc:ae:c5:c7:98:40 timed out
[  487.081022] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 1/3)
[  487.280062] wlan0: direct probe to bc:ae:c5:c7:98:40 (try 2/3)
[  487.283367] wlan0: direct probe responded
[  487.283379] wlan0: authenticate with bc:ae:c5:c7:98:40 (try 1)
[  487.285106] wlan0: authenticated
[  487.285599] wlan0: associate with bc:ae:c5:c7:98:40 (try 1)
[  487.287558] wlan0: RX AssocResp from bc:ae:c5:c7:98:40 (capab=0x411 status=0 aid=1)
[  487.287561] wlan0: associated

```

---

### Post by diesousil on 2012-07-17
Exactly same problem, my bcm4312 Wifi is installed, but doesn't work more than 5 seconds.... dmesg gives me the same messages

---

### Post by overdrank on 2012-07-18
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

