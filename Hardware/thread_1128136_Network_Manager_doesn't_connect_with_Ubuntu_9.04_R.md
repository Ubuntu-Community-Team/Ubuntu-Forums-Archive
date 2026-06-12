---
title: "Network Manager doesn't connect with Ubuntu 9.04 RC Netbook Remix, in a Asus EEE 901"
date: 2009-04-17
forum: Hardware
---

### Post by eastir on 2009-04-17
Hi. I think this is a bug, but i don't know how solve it.

I have an Asus EEE 901 (Linux edition) and I have tested Ubuntu 9.04 Netbook Remix since alpha 6. Wifi has worked often well. Yesterday, Ubuntu released the Release Candidate and i tested it. 

My surprise was which wifi doesn't work. It search network, found it, but when I put network pass (WPA / WPA2 Personal + TKIP / AES with Tomato firmware) it doesn't connect, the lights of network manager are one green and the other gray and a line around both, all of time. Then, network manager asks me the pass again.

What do you think?

Thanks

---

### Post by HankB on 2009-04-17
If you look at the output of dmesg, it will show some information on the negotiation of the connection. Posting that here might help someone more knowledgeable than me to solve it.

If I renegotiate the connection on my T500 (Intrepid) I get:

```
[313469.139364] wlan0: disassociating by local choice (reason=3)
[313469.217125] wlan0: authenticate with AP 00:1e:e5:xx:xx:xx
[313469.219334] wlan0: authenticated
[313469.219344] wlan0: associate with AP 00:1e:e5:xx:xx:xx
[313469.223310] wlan0: RX AssocResp from 00:1e:e5:xx:xx:xx (capab=0x411 status=0 aid=3)
[313469.223319] wlan0: associated
[313469.223409] wlan0 (WE) : Wireless Event too big (342)

``` (some information obfuscated) 

I don't know where the official place to report problems with the RC is, but it seems like it would be a good idea to report this. (Particularly since I have a 901 inbound and plan to put Jaunty on it! :D )

Please keep us posted since WiFi is important to me. (I suppose I could run a live USB to see if I get different results.)

-hank

---

### Post by eastir on 2009-04-17
Thanks for your response. This is from dmesg when i try to connect to the wifi.

```

[  498.069398] RX DESC f6030000  size = 2048
[  498.070174] <-- RTMPAllocTxRxRingMemory, Status=0
[  498.073964] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[  498.073976] 1. Phy Mode = 0
[  498.073983] 2. Phy Mode = 0
[  498.102054] 3. Phy Mode = 0
[  498.106738] MCS Set = 00 00 00 00 00
[  498.108402] <==== RTMPInitialize, Status=0
[  498.108485] 0x1300 = 00073200
[  503.148607] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 837
[  508.804188] ra0: no IPv6 routers present
[  523.418214] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 636
[  523.418945] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=10)
[  538.435729] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 717
[  538.438580] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=10)
[  553.449266] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 800
[  553.465906] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=10)
[  568.481116] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 717
[  568.481578] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=10)
[  603.416226] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 837
[  673.415277] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 925

```

greetings

---

### Post by HankB on 2009-04-17
Most of that is unintelligible to me. The one thing that I would follow up on is:
```
[  498.073964] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
```

Do you have older log files from when this worked? (I'm pretty sure that most, if not all, of what shows up in dmesg also gets written to one of the log files in /var/log.) I'm guessing that the file is something that gets downloaded to the WiFi adapter. I don't honestly know if it is required or not, but it seems worth following up.

---

