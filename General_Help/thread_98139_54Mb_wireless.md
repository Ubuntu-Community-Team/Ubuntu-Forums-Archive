---
title: "54Mb wireless"
date: 2005-12-02
forum: General Help
---

### Post by dajomu on 2005-12-02
As far as I know linux still dont support 54Mb wireless. Anyone know why not?

Dajomu

---

### Post by mlomker on 2005-12-02
[QUOTE=dajomu]As far as I know linux still dont support 54Mb wireless. Anyone know why not?[/QUOTE]

That's incorrect.

```

mlomker@mlomkernote:/$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"2409"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4B:19:C6:0F
          **Bit Rate=54 Mb/s**   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-31 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```

---

### Post by skyboy on 2005-12-03
I use 11mb and 54mb wifi at the same time.  where did you get that stupid info ?

```
wlan0     IEEE 802.11b  ESSID:"ConnectionPoint"  Nickname:"ConnectionPoint"
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:01:E3:04:XX:XX
          Bit Rate=11 Mb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-62 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:20   Missed beacon:0

ath0      IEEE 802.11g  ESSID:"ConnectionPoint"
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:01:E3:04:XX:XX
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/94  Signal level=-62 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

