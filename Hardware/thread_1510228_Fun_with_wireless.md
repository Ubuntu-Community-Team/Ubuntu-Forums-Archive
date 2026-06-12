---
title: "Fun with wireless"
date: 2010-06-15
forum: Hardware
---

### Post by Humphreybas on 2010-06-15
Hello
I own a Toshiba U400 With a Intel Wifi link 5100. It runs on ubuntu 9.04 jaunty 64bit.
I installed the compat-wireless with the backport package.

-At home with a 802.11n network there is no problem connection is allways quick and stable
-At university I am sitting under the acces point, the "eduroam" network shows up in my list with 100% strength. But when I connect it just keeps trying to connect, after a while of trying it shows me my login settings (WPA& WPA2 enterprise, PEAP, MSCHAPv2) and then I can choose to repeat the whole trying story.
In some buildings on some days I do get connection (1 out of 10) (so no, it's not my loginname or password or something)

My output of iwevent:
```

14:25:45.361853   wlan0    Scan request completed
14:25:45.362415   wlan0    Set Mode:Managed
14:25:45.364213   wlan0    Set Frequency:5.18 GHz (Channel 36)
14:25:45.570938   wlan0    Custom driver event:ASSOCRESPIE=01088c1218243048606c2d1a6e181bffff0000000000000000000000000000000000000000003d1624050700000000000000000000000000000000000000dd180050f2020101800003a4000027a4000042435e0062322f00
14:25:45.571814   wlan0    New Access Point/Cell address:00:23:04:C8:A5:4D
14:25:48.615834   wlan0    New Access Point/Cell address:Not-Associated
14:25:48.626865   wlan0    Scan request completed
14:25:48.639900   wlan0    Set Mode:Managed
14:25:48.643065   wlan0    Set Frequency:2.432 GHz (Channel 5)
14:25:49.301627   wlan0    New Access Point/Cell address:Not-Associated

Etc. Etc. Etc.

```Output of iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```lshw:
```
*-network
                description: Wireless interface
                product: Wireless WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wmaster0
                version: 00
                serial: 00:21:6b:65:fb:96
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```I have read trough many forumposts/wifidocs/other sources and now I give up. I will try to get some happy responses here :)  Again a wlan wifi problem, yeaah! :)

---

### Post by Humphreybas on 2010-06-15
Oh forgot to mention, is a windows XP dualboot. Works fine under winXP.

---

### Post by Humphreybas on 2010-06-17
Apparently WPA2 has since some time been an issue with network-manager in certain versions. And even when I switched to the PPA ( [https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa) ) to be able to update to the newest version I just got into more trouble. After update I could setup the connection but had no connection (couldn't ping/visit anything). I changed to the karmic PPA (because I read people who got it solved when changing to karmic and run into **** again when going to lucid..) which didn't solve it either.
By then I decided to give up all my configured networks (passwords etc.) in network-manager and just try WICD. And now I have no troubles at all.

This really got down my happy feelings about being a ubuntu user, it costed me so much extra time.

---

