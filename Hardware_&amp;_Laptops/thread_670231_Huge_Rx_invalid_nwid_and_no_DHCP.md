---
title: "Huge Rx invalid nwid and no DHCP"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by stevelinton on 2008-01-17
I have a Thinkpad T41p with Atheros wireless chipset. Mostly it works fine. I'm using Gutsy and NetworkManager (under gnome).

Occasionally it will refuse to complete a connection to a network.   iwconfig will show regsitration, but the "Rx invalid nwid" field increases by a few per second" and no DHCP responses are received, so I never get an IP level connection. Usually, a reboot fixes this.

I have one site where it always seems to happen. iwlist ath0 scan gives me:



ath0      Scan completed :
          Cell 01 - Address: 00:17:5A:5D:0B:E0
                    ESSID:"eduroam"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=15/70  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : 802.1x
                    Extra:wme_ie=dd180050f2020101830003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:14:F2:FC:87:10
                    ESSID:"eduroam"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : 802.1x
                    Extra:wme_ie=dd180050f2020101830003a4000027a4000042435e0062322f00
          Cell 03 - Address: 00:18:F8:AE:79:46
                    ESSID:"CIRCA"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-49 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:14:7F:4B:6A:E3
                    ESSID:"BTHomeHub-2C3D"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101880003a4000027a4000042435e0062322f00


I can connect to "eduroam"  on channel 1, but I'd rather connect to CIRCA. When I do, I get the excessive invalid nwid problem.

Anyone know what is going on?

Steve

---

### Post by BrendanM on 2008-01-18
Hey, I have the exact same problem. Also with an atheros chipset, although mine is in a desktop. Anyone have any ideas?

---

### Post by BrendanM on 2008-01-18
It seems like lots of people are having this issue: [http://madwifi.org/ticket/1081](http://madwifi.org/ticket/1081)

Stevelinton, do you only get this problem on a WPA access point? Or do you get in on WEP/unsecured APs as well?

---

