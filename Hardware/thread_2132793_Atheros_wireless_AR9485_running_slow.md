---
title: "Atheros wireless AR9485 running slow"
date: 2013-04-05
forum: Hardware
---

### Post by andyhelloween on 2013-04-05
Hello all,

Since two days ago I was struggling to get my wireless to a decent speed in my Server (Running Ubuntu Server 12.04). I just succeeded and wanted to share the solution given that I couldn't find it out there. Maybe you already knew about it but anyway, here it goes:

**_Issue_**: Constant transfer rate of 13.5 Mbps. From time to time I managed to get 40 Mbps, but later on dropped again.
**_Solution_**: Change the router to 802.11g only - Not "N", not "B", not "G+N+B". After this my transfer rate went straight up to 54 Mbps!

For my this is something I was able to do given I don't have any other device working at N-Speed. Pity though the Atheros wireless I bought is Wireless-N capable. I later found out my purchase wasn't the best I could have made.

I also switched off hardware encryption, but didn't notice any improvement - It worked for my wife's laptop though.
Tried to disable IPv6 with no change at all.

Here's the usual info for comparison against yours:

```

> dmesg | grep wlan0
[   12.304449] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.127840] wlan0: authenticate with 78:a0:51:0f:ec:37 (try 1)
[   14.129833] wlan0: authenticated
[   14.153579] wlan0: associate with 78:a0:51:0f:ec:37 (try 1)
[   14.156961] wlan0: RX AssocResp from 78:a0:51:0f:ec:37 (capab=0x411 status=0 aid=6)
[   14.156965] wlan0: associated
[   14.162009] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.128040] wlan0: no IPv6 routers present

```

```

> ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1288 (1.2 KB)  TX bytes:1288 (1.2 KB)


wlan0     Link encap:Ethernet  HWaddr 64:70:02:d3:7b:8f  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6670:2ff:fed3:7b8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:270283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:164809264 (164.8 MB)  TX bytes:347645721 (347.6 MB)

```

```

> lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Atheros Communications Inc. Device [168c:3118]
    Kernel driver in use: ath9k

```

```

> lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33719  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
ath9k                 132428  0 
mac80211              506862  1 ath9k
i915                  477626  1 
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
drm_kms_helper         46978  1 i915
drm                   241971  2 i915,drm_kms_helper
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd_timer              29990  1 snd_pcm
snd                    79041  7 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
mac_hid                13253  0 
shpchp                 37201  0 
i2c_algo_bit           13423  1 i915
cfg80211              205774  3 ath9k,mac80211,ath
mei                    41616  0 
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
video                  19651  1 i915
parport                46562  1 lp
mxm_wmi                13021  0 
wmi                    19256  1 mxm_wmi
pata_marvell           12912  0
``` 

```

> dmesg | grep ath
[   12.950075] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.950086] ath9k 0000:01:00.0: setting latency timer to 64
[   12.957820] ath: EEPROM regdomain: 0x21
[   12.957821] ath: EEPROM indicates we should expect a direct regpair map
[   12.957823] ath: Country alpha2 being used: AU
[   12.957824] ath: Regpair used: 0x21
[   13.009455] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.009817] Registered led device: ath9k-phy0

```

```

> rfkill list
    0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by george akulov on 2013-06-01
Set on router frequency 2.4GHz and channel bandwidth 40 MHz and only N standrd my AR9485 linked up to the speed of 135Mbs

---

