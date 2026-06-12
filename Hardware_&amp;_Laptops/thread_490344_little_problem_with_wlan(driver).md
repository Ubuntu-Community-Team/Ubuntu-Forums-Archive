---
title: "little problem with wlan(driver?)"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by feio on 2007-07-02
i've got a IBM Thinkpad R 31 2656.

and i'm trying to get wlan over a US Robotic wireless Router. 

somehow the wireless card "finds" a strong signal from the router, but i cant get access.
my first impression was that i may have the wrong driver installed. any ideas?

thx ahead for any help.


here are some infos that may be helpful:

> iwconfig

eth1      IEEE 802.11b  ESSID:"URS5451"  Nickname:"Prism  I"0000:01:05.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

          Mode:Managed  Frequency:2.417 GHz  Access Point: None
          Bit Rate:11 Mb/s   Sensitivity:1/3000:01:05.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

          Retry min limit: 8   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality = 84/92  Signal level = 5/153  Noise level = 116/153
          Rx invalid nwid: 0  Rx invalid crypt: 66  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0


iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: xx : xx : xx : xx : xx : xx
                    ESSID:"USR5451"
                    Mode:Master
                    Frequency: 2.462 GHz (Channel 11)
                    Signal level: 56/153  Noise level:16/153
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s

---

