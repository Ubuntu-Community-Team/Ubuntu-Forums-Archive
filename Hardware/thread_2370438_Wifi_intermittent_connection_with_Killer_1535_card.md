---
title: "Wifi intermittent connection with Killer 1535 card"
date: 2017-09-03
forum: Hardware
---

### Post by andrea103 on 2017-09-03
I am running Ubuntu 16.04 on a Dell XPS13 9360 with Killer 1535 wireless card and, although connection to wifi works perfectly when signal strength is good, I get intermittent connectivity when sitting relatively far from routers (all my other devices work totally OK). This wireless card seems to have given headaches to a bunch of other users and especially in this thread

[HTML]https://ubuntuforums.org/showthread.php?t=2358669[/HTML]

similar issues are described. The solution in that case ended up being a replacement of the wireless card which I would like to avoid. Here some useful info:

```
sudo lshw -c network  *-network               
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:3a:00.0
       logical name: wlp58s0
       version: 32
       serial: 9c:b6:d0:e0:8c:33
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.10.0-33-generic firmware=WLAN.RM.2.0-00180-QCARMSWPZ-1 ip=192.168.43.98 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:286 memory:dc000000-dc1fffff

```

```
dmesg | grep ath10k[    3.310010] ath10k_pci 0000:3a:00.0: enabling device (0000 -> 0002)
[    3.313176] ath10k_pci 0000:3a:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    3.602417] ath10k_pci 0000:3a:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:3a:00.0.bin failed with error -2
[    3.602423] ath10k_pci 0000:3a:00.0: Direct firmware load for ath10k/cal-pci-0000:3a:00.0.bin failed with error -2
[    3.602545] ath10k_pci 0000:3a:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    3.602546] ath10k_pci 0000:3a:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    3.603446] ath10k_pci 0000:3a:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:1535
[    3.603447] ath10k_pci 0000:3a:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    3.603802] ath10k_pci 0000:3a:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[    3.667182] ath10k_pci 0000:3a:00.0: board_file api 2 bmi_id N/A crc32 07ee144e
[    5.796346] ath10k_pci 0000:3a:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    5.886517] ath10k_pci 0000:3a:00.0 wlp58s0: renamed from wlan0
[ 3193.416691] ath10k_pci 0000:3a:00.0: failed to flush transmit queue (skip 0 ar-state 1): 0



```

Has anyone managed to get this card running or has an idea how to fix this? Dell ships some of the Developer Edition XPS13s with this card so there seems to be a way.

---

### Post by andrea103 on 2017-09-04
I collected some more information. When able to connect the output of 

```
 sudo iwlist scanning
```

reads

```
wlp58s0   Scan completed :          Cell 01 - Address: 00:0B:86:86:42:E0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001b434417a
                    Extra: Last beacon: 28476ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01078C18243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:24:6C:3B:F5:70
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=63/70  Signal level=-47 dBm
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000053d12ca38
                    Extra: Last beacon: 2804ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01078C18243048606C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000



```

When not (notice same ESSID "eduroam") instead:

```
lo        Interface doesn't support scanning.

wlp58s0   Scan completed :
          Cell 01 - Address: 00:0B:86:86:5D:80
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=60/70  Signal level=-50 dBm
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000077150415
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01078C18243048606C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 00:0B:86:86:43:21
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=32/70  Signal level=-78 dBm
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000201aaed46
                    Extra: Last beacon: 6496ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01078C18243048606C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:0B:86:86:5C:21
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=49/70  Signal level=-61 dBm
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000092212b31
                    Extra: Last beacon: 5860ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01078C18243048606C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000



```

The same issue seems to affect another laptop with the same specs in the office. Any idea/useful pointer? Thanks!

---

