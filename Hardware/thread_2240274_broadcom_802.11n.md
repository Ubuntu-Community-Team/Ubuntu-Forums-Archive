---
title: "broadcom 802.11n"
date: 2014-08-19
forum: Hardware
---

### Post by bbullett on 2014-08-19
I have a problem with speed. I installed bcmwl-kernel-source and output of iwconfig is:

```
wlan0     IEEE 802.11bgn  ESSID:"BBuLLeTT_WiFI"            Mode:Managed  Frequency:2.437 GHz  Access Point: F8:D1:11:4D:4D:E0   
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=0 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2752  Invalid misc:1012   Missed beacon:0



```
Connection information says 72 Mb/s
But my max download/upload speed is 4-5MB/s.
When connecting through wired network my download/upload speed is 10MB/s

---

### Post by weatherman2 on 2014-08-19
5MB/s is completely normal for a typical 802.11n wireless network.  Unfortunately, advertised speeds for WiFi are often far less than what you really get.

You can try some tricks to improve your speed a little.  Check for other WiFi radios broadcasting on the same channel that your router uses and if there are other nearby routers on your channel, try switching to another channel.

Also, experiment with a 40MHZ wide channel (two channels, really).  Typically that will improve your download/upload speeds a little.

Also, make sure you are using WPA2 + AES encryption if you are using any kind of encryption.

---

