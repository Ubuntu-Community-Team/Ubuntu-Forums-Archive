---
title: "WiFi Adapter strange behavior"
date: 2016-03-19
forum: Hardware
---

### Post by grayscale2 on 2016-03-19
Hi guys!
What the hell with my Wireless network adapter?  
I have Atheros AR9485, Ubuntu 15.10 installed on ASUS K46CB laptop with kernel 4.2.0-34, router Cisco Linksys EA3500 with default firmware (the latest version)
This is what I observe in journalctl from time to time (5 times in a last hour):
```

&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB [COLOR=#ff0000]kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000028 AR_DIAG_SW=0x02000020 DMADBG_7=0x0000a400[/COLOR]&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB [COLOR=#ff0000]kernel: ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up[/COLOR]
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB [COLOR=#ff0000]kernel: ath: phy0: Failed to stop TX DMA, queues=0x00a![/COLOR]
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB wpa_supplicant[852]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=20:aa:4b:65:4a:a6 reason=4 locally_generated=1
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB NetworkManager[796]: <warn>  Connection disconnected (reason -4)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB wpa_supplicant[852]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211: World regulatory domain updated:
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211:  DFS Master region: unset
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB kernel: cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: completed -> disconnected
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:26 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: disconnected -> scanning
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:27 grayscale-K46CB wpa_supplicant[852]: wlp3s0: SME: Trying to authenticate with 20:aa:4b:65:4a:a6 (SSID='Potato' freq=2457 MHz)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:27 grayscale-K46CB kernel: wlp3s0: authenticate with 20:aa:4b:65:4a:a6
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:27 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: scanning -> authenticating
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:27 grayscale-K46CB kernel: wlp3s0: send auth to 20:aa:4b:65:4a:a6 (try 1/3)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:27 grayscale-K46CB kernel: wlp3s0: send auth to 20:aa:4b:65:4a:a6 (try 2/3)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:28 grayscale-K46CB kernel: wlp3s0: send auth to 20:aa:4b:65:4a:a6 (try 3/3)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:28 grayscale-K46CB kernel: wlp3s0: authentication with 20:aa:4b:65:4a:a6 timed out
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:28 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: authenticating -> disconnected
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:28 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: disconnected -> scanning
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:29 grayscale-K46CB wpa_supplicant[852]: wlp3s0: SME: Trying to authenticate with 20:aa:4b:65:4a:a6 (SSID='Potato' freq=2457 MHz)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:29 grayscale-K46CB kernel: wlp3s0: authenticate with 20:aa:4b:65:4a:a6
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:29 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: scanning -> authenticating
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:29 grayscale-K46CB kernel: wlp3s0: direct probe to 20:aa:4b:65:4a:a6 (try 1/3)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:29 grayscale-K46CB wpa_supplicant[852]: wlp3s0: Trying to associate with 20:aa:4b:65:4a:a6 (SSID='Potato' freq=2457 MHz)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:29 grayscale-K46CB kernel: wlp3s0: send auth to 20:aa:4b:65:4a:a6 (try 2/3)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:29 grayscale-K46CB kernel: wlp3s0: authenticated
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:29 grayscale-K46CB kernel: wlp3s0: associate with 20:aa:4b:65:4a:a6 (try 1/3)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:29 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: authenticating -> associating
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:29 grayscale-K46CB kernel: wlp3s0: associate with 20:aa:4b:65:4a:a6 (try 2/3)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:30 grayscale-K46CB kernel: wlp3s0: associate with 20:aa:4b:65:4a:a6 (try 3/3)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:30 grayscale-K46CB kernel: wlp3s0: association with 20:aa:4b:65:4a:a6 timed out
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:30 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: associating -> disconnected
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:31 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: disconnected -> scanning
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB wpa_supplicant[852]: wlp3s0: SME: Trying to authenticate with 20:aa:4b:65:4a:a6 (SSID='Potato' freq=2457 MHz)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB kernel: wlp3s0: authenticate with 20:aa:4b:65:4a:a6
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: scanning -> authenticating
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB kernel: wlp3s0: send auth to 20:aa:4b:65:4a:a6 (try 1/3)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB wpa_supplicant[852]: wlp3s0: Trying to associate with 20:aa:4b:65:4a:a6 (SSID='Potato' freq=2457 MHz)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB kernel: wlp3s0: authenticated
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB kernel: wlp3s0: associate with 20:aa:4b:65:4a:a6 (try 1/3)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: authenticating -> associating
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB wpa_supplicant[852]: wlp3s0: Associated with 20:aa:4b:65:4a:a6
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB kernel: wlp3s0: RX AssocResp from 20:aa:4b:65:4a:a6 (capab=0x411 status=0 aid=2)
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB kernel: wlp3s0: associated
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: associating -> 4-way handshake
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB wpa_supplicant[852]: wlp3s0: WPA: Key negotiation completed with 20:aa:4b:65:4a:a6 [PTK=CCMP GTK=CCMP]
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB wpa_supplicant[852]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to 20:aa:4b:65:4a:a6 completed [id=0 id_str=]
&#1084;&#1072;&#1088;&#1090;&#1072; 19 15:39:32 grayscale-K46CB NetworkManager[796]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed

```

iwconfig:
```

wlp3s0    IEEE 802.11bgn  ESSID:"Potato"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 20:AA:4B:65:4A:A6   
          Bit Rate=57.8 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:9   Missed beacon:0

```
 
cat /etc/modprobe.d/ath9k.conf 
```

options ath9k nohwcrypt=1

```

I use Ubuntu starting from 13.10 on this laptop and the same behavior was not observed earlier.
I also have laptop with Win 10 installed and it seeems ok (yes, it also has other wireles adapter)
Unfortunately, I don't know when the problem appeared, because I don't notice it during web surfing. But when I started to play online games it brought ping lags an latency..

---

### Post by grayscale2 on 2016-03-19
I have performed some tests, run speedtest, ping to my router.
under high load I see the same in dmesg:
ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x0002ad00
[ 7518.493441] wlp3s0: authenticate with 20:aa:4b:65:4a:a6
[ 7518.514290] wlp3s0: send auth to 20:aa:4b:65:4a:a6 (try 1/3)
[ 7518.518586] wlp3s0: authenticated
[ 7518.519909] wlp3s0: associate with 20:aa:4b:65:4a:a6 (try 1/3)
[ 7518.548979] wlp3s0: RX AssocResp from 20:aa:4b:65:4a:a6 (capab=0x411 status=0 aid=3)
[ 7518.549092] wlp3s0: associated

Also packet losses occured during the ping..

---

