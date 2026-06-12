---
title: "Asus K56CB - WiFi periodically disconnects"
date: 2015-04-26
forum: Hardware
---

### Post by adk on 2015-04-26
Hello,
I'm currently running up-to-date Kubuntu 14.04 x64 on my Asus K56CB laptop. The thing, that I cannot solve and is really driving me insane are intermittent WiFi connection drops.
The laptop card is 
```
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
```
driven by the module iwlwifi + iwldvm.

When disconnections happen, dmesg says:
```
wlan0: deauthenticated from xx:xx:xx:xx:xx:xx (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
```

I googled a lot for this issue, but I could not find any working solution for this.
What I have tried:
- upgrading the kernel (currently 3.16.0-34-generic)
- upgrading the linux-firmware package from newer Ubuntu version (currently 1.143)
- downloading firmware from linuxwireless and upgrading it manually
- adding these lines to /etc/modprobe.d/iwlwifi.conf as suggested somewhere in the net:
```
options iwlwifi 11n_disable=1
options iwlwifi power_save=0
```
    Looking at /sys/module/iwlwifi/parameters/* it states, that options are applied, but this does not help at all
- trying to run ndiswrapper, but I cannot find a suitable driver (inf file from Windows CD from this laptop does not work).

The laptop is dual-booting with Windows 7, and connection on the second system is stable.

Do you have any suggestions what else could I try?

---

### Post by adk on 2015-05-03
Update: the module option:
bt_coex_active=0
does not help too.
I have also tried various settings in the router (like channel, channel width) but no avail.

---

### Post by adk on 2015-05-27
After some of the latest updates the problem seems to be gone (or significantly reduced).

The current setup, that works for me is:
- kernel 3.19.0-15 x64 (from newer Ubuntu release, manually downloaded)
- firmware (manual download from linux-wireless): iwlwifi-2030-ucode-18.168.6.1
- file /etc/modprobe.d/iwlwifi.conf: do not enable anything, keep settings at their defaults, including 802.11n mode and so
- in the router, if you have some other WiFis around you:
 -> use 20MHz channel width, not 40 to avoid interferences
 -> use channel 1, 6 or 11 (or auto-select if your router does it correctly). Selecting something between may make interference worse (read more in the net)
Above setup currently seems very stable.

---

### Post by weatherman2 on 2015-05-27
I'm glad you got something more reliable to work.

If you live in an area with a lot of other 2.4GHZ WiFi radios, then using a 20MHZ channel can help reduce interference.  But that will also reduce possible bandwidth.  If you don't have many WiFi radios near you, it should be better/faster to use a 40MHZ channel (really two channels adjacent) for better throughput.

There's nothing magical about channels 1, 6, or 11.  If you have neighbors with their routers/WiFi radios using those channels but say channel 3 or 9 are not used, you would be better off using them to avoid interference.

---

### Post by adk on 2015-05-31
The common misunderstanding about WiFi is, that one network occupies one channel. Actually, 1 channel = 5MHz, and to perform a transmission, 20MHz is used as said above. This means, that 1 network actually occupies 4 adjacent channels. That's why 1-6-11 is the common setup to provide frequency separation. If your router and client are using 40Mhz channel width, you are actually using 8 channels (out of 13 possible), effectively jamming the whole air around.
I have also tried channels between (like 3 or 9) but this had no effect as there is actually no free air space around me, and many people are sending at 40Mhz, because it's the default setup for routers and few people are doing some configurations beside SSID and password.
There are some visualization programs - like LinSSID for Linux, InSSIDer for Windows or some software for Android. These programs are graphically presenting band usage around you and may help to find a free air space (if possible).

---

