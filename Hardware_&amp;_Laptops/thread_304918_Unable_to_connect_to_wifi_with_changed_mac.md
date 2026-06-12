---
title: "Unable to connect to wifi with changed mac"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by mastico on 2006-11-22
I have problem to view new networks after I change my mac I have broadcom 4318. I have installed bcm43xx drivers.

Mastico

---

### Post by mastico on 2006-11-22
root@mastico:~# modprobe bcm43xx
root@mastico:~# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:16:CF:45:0E:1A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:27 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xc000
root@mastico:~# /sbin/iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:11:2F:2F:6D:C7
                    ESSID:"ik-wifief1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-162 dBm
                    Extra: Last beacon: 332ms ago
          Cell 02 - Address: 00:11:2F:A6:DC:2D
                    ESSID:"ik-wifief2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:2
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-187 dBm
                    Extra: Last beacon: 396ms ago

root@mastico:~# ifconfig eth1 down
root@mastico:~# ifconfig eth1 hw ether AA:AA:AA:AA:AA:AA
root@mastico:~# ifconfig eth1 up
root@mastico:~# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr AA:AA:AA:AA:AA:AA
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:55 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1176 (1.1 KiB)
          Interrupt:10 Base address:0xc000

root@mastico:~# /sbin/iwlist eth1 scan
eth1      No scan results
root@mastico:~#

---

