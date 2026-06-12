---
title: "ahteros problem?"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by sambuls on 2007-06-19
hello,

I'm using a T60p lenovo from IBM. It has an atheros wifi card.

lspci: 03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

In Ubuntu feisty the networkmanager applet can use this chipset but, it can only reach up to 30 % of signal quality.

iwconfig:

ath0      IEEE 802.11g  ESSID:"buls.be"  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:12:BF:23:ED:F0   
          Bit Rate:6 Mb/s   Tx-Power:8 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=35/94  Signal level=-63 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can somebody tell me what's wrong?

---

### Post by frigaut on 2007-06-19
may be networkmanager reports a signal level which is uncalibrated. This doesn't necessarily affect your ability to receive good signal. 
I have a T60 too and have noticed that the reception was slightly worse than on an older T40 I was using. I assume it's how and where the antenna is located within the laptop frame.

anyway. Did you also try a "iwlist scanning" ?

---

### Post by sambuls on 2007-06-19
this is the output of iwlist scanning

ath0      Scan completed :
          Cell 01 - Address: 00:13:92:03:42:D7
                    ESSID:""
                    Mode:Master
                    Frequency:2.472 GHz (Channel 13)
                    Quality=30/94  Signal level=-65 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:12:BF:23:ED:F0
                    ESSID:"buls.be"
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

As you can see the Qualitiy is 31/94, this is nog good. So I don't think that the problem is the networkmanager applet.

---

### Post by marx2k on 2007-07-31
Yep same here..

02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

ath0      Scan completed :
          Cell 01 - Address: 00:07:40:C4:3B:5E
                    ESSID:"ghostdog"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/94  Signal level=-59 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

```

---

### Post by ugm6hr on 2007-07-31
> **sambuls said:**
> Can somebody tell me what's wrong?

Probably nothing.  If it works, that is.

The reported signal strength is irrelevant.  My Atheros 5005G wifi (ath_pci driver) never gets above about 35% signal strength either (even right next to access point) but it works everywhere, with a range as good as I could expect (and same as Windows XP driver).

Don't worry about it.

---

