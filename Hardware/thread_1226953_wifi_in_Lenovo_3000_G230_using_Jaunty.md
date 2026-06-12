---
title: "wifi in Lenovo 3000 G230 using Jaunty"
date: 2009-07-30
forum: Hardware
---

### Post by arc sol on 2009-07-30
so i've been reading the so many threads here on wifi setup and i don't know where to start.

situation: i can connect to my home network with no problem but i always get dropped out while using the office network e.g. it runs, then the connection randomly dies. running sudo iwlist eth1 scan on both networks yield the following:

Home network: 
```

eth1      Scan completed :
          Cell 01 - Address: 00:1D:7E:F6:AE:64
                    ESSID:[home network]
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

```

Office network:
```

eth1      Scan completed :
          Cell 01 - Address: 00:1E:58:E9:48:DD
                    ESSID:"Office network"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-43 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7F0050F204104A0001101044000102103B0001031047001055F30CEEECE73323A9D2D4D73D0970921021000E442D4C696E6B2053797374656D73102300074449522D363535102400024133104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

```

lspci yields the following

```

1:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

i'm using the proprietary drivers from broadcom. also, i am not at liberty to monkey around with either wifi routers - a lot of people will get hit if ever.

thank you for your input.

---

