---
title: "Wi-Fi stops working occasionally"
date: 2012-07-02
forum: Hardware
---

### Post by pouldney on 2012-07-02
My Wi-Fi stops working occasionally ,usually when downloading lots of data such
 as when viewing a video.
       The only way to get it back up is to Re-Boot
       I have an Acer Aspire 1551-3671  with Ubuntu 12.04 (Precise Pangolin)



     Here is some data on the problem 
   Note that phy0 is Hard Blocked 


  george@george-Aspire-1551:~$  sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

george@george-Aspire-1551:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: C0:83:0A:DF:79:E9
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"2WIRE263"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000872e55e181
                    Extra: Last beacon: 19760ms ago
                    IE: Unknown: 00083257495245323633
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 0706434120010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

  lspci -v
06:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e034
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d0300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

---

### Post by Redblade20XX on 2012-07-02
Once you've started a session, open a terminal and type
```
iwevent
```

( Maybe you'll need sudo... I'm starting to lose my memory, lol!)

This will monitor your wireless network for any events and once your wifi goes out an event will be logged in the terminal.

Post what is logged! Also see if you can look into your kernel log in directory /var/log at the time the event occurs.

- Red

---

