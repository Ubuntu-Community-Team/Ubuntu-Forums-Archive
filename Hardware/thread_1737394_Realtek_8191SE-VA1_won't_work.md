---
title: "Realtek 8191SE-VA1 won't work"
date: 2011-04-23
forum: Hardware
---

### Post by TheExposedOne on 2011-04-23
A few days ago, above card was working flawlessly. Then I hibernated. After logging back in my card didn't work.
I tried reinstalling drivers and it didn't work.
After many attempts i reinst. ubuntu and still no

lspci:
```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev ff)
``` it used to say rev 10

iwconfig:
```
wlan0     802.11bgn  Nickname:"rtl8191SEVA1"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```I can't find drivers for this device
no radio light
i,ve tried fn+f4
rfkill doesn't work anymore

What do I do?

Edit: I reinstalled some drivers and now it says rev 10 rather than rev ff however, iwconfig shows no wlan0 and i can only use eth0
any help is appreciated

---

### Post by TheExposedOne on 2011-04-23
Please, can anyone help, this is urgent

---

