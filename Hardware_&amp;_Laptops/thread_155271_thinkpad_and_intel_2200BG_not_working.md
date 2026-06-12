---
title: "thinkpad and intel 2200BG not working"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by pretndr on 2006-04-04
Hi all,

Downloaded Ubuntu on a dual boot thinkpad T42 laptop this week and everything works great. I can't live without wireless though:

Q - I cant get my wireless to work on WEP or WPA. I have a netgear wgt624 with a test ssid and 64 bit key. I can activate the card and enter the key just fine and nothing. I can see all the networks around me, just cant connect.  Any ideas?

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[4294700.234000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294700.234000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294700.237000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

---

### Post by pretndr on 2006-04-04
I got it. The security settings on my router was the problem. Thanks...

---

