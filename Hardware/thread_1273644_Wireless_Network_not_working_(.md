---
title: "Wireless Network not working :("
date: 2009-09-23
forum: Hardware
---

### Post by charlitos on 2009-09-23
My adapter is a Wireless LAN 802.11 b/g, I just recently installed Ubuntu and have no clue how to work it. It displays a wireless network icon on the top right corner but it doesnt detect any network at all...could this be a compatibility issue with the router in question? Or do I have to find drivers for this adapter maybe?


thanks a lot in advance

---

### Post by theDaveTheRave on 2009-09-23
charlitos.

first off we need a little more information, but I'll try to help out a bit also.

We will need to know if your wireless card is functioning & or recognised.

```

iwlist scan

```
will tell us if your card is turned on, if you get a report similar to this one below (my output) that is great, as the card is obviously working...

```

davem@Dartagnon:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1F:9F:E6:1F:75
                    ESSID:"Bbox-70F2F8"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=11/70  Signal level=-84 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101880003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:23:08:2C:F6:B0
                    ESSID:"DartyBox_50F7"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-62 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101050003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010000ff7f
          Cell 03 - Address: 06:23:08:2C:F6:B0
                    ESSID:"Mousquetaires"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-60 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101050003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010000ff7f
          Cell 04 - Address: 3A:7B:C0:33:29:EF
                    ESSID:"freephonie"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 05 - Address: 3A:7B:C0:33:29:ED
                    ESSID:""
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 06 - Address: 00:16:B6:B8:0F:EB
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 07 - Address: EA:75:6A:DC:37:54
                    ESSID:""
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 08 - Address: 02:00:4F:CA:C5:94
                    ESSID:"hpsetup"
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 09 - Address: 3A:7B:C0:33:29:EE
                    ESSID:"FreeWifi"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 10 - Address: 00:1D:19:AD:C8:B1
                    ESSID:"TELE2BOX_8CE4"
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101820003a4000027a4000042435e0062322f00
          Cell 11 - Address: 3A:7B:C0:33:29:EC
                    ESSID:""
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 00:1A:6B:C9:9A:EB
                    ESSID:"Livebox-1ef6"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00

pan0      Interface doesn't support scanning.

davem@Dartagnon:~$ 

```

If you get that, is should just be a matter of using network manager to locate and add your wireless network / password details, and you should be set to go.

open the network manager from the System -> Preferences -> Network Configuration option in the menu. There is also a network manager applet that I have in my panel, but I can't find how I added it! sorry not very helpfull... :confused:

So now if you didn't have any luck with the above stuff, we need to know if your wireless card is going to work with ubuntu, again here is the code and then following the output from my system...

```

davem@Dartagnon:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:c8:51:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       [COLOR="Red"]product: AR2413 802.11bg NIC[/COLOR]
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wifi0
       version: 01
       serial: 00:19:7d:40:b8:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.135 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:49:bd:f7:8b:57
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
davem@Dartagnon:~$ 

```

I have highlighted part of my output, this is the details of the network card, if you take your output result for this same detail and use it as a search term in the forums I am certain that you will find someone else out there who has had (and solved) problems with their card.

Good luck, wireless can be a chalenge to get going in linux, but the feeling of pleasure and the learning experience you get from it will help you in a thousand ways with future problems that you will no doubt have. Especially as linux users have a nasty habit of "Breaking" their systems :lolflag:

David

---

### Post by charlitos on 2009-09-24
thakns a lot for your help :)

well I tried that...and the output doesnt really look promising at all. 

```

charlitos@Charlitos-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

charlitos@Charlitos-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:c6:89:de:08
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:44:18:bc:59
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 5e:03:64:ec:34:a0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

it doesnt display product for my wireless network adapters which according to your comment was very important. So I really dont know what should I look for.

---

### Post by skatinjj on 2009-09-24
**Run:**
```
lspci
```
Post output here please.

---

### Post by charlitos on 2009-09-24
this is it :confused:

```
charlitos@Charlitos-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 0f)
05:00.0 VGA compatible controller: nVidia Corporation Device 06e0 (rev a1)
```

---

### Post by skatinjj on 2009-09-24
That is showing you have an ethernet adapter

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

but not a wireless card.

You are going to have to find drivers for your card.  If you tell me the company that made your adapter I can help you a little more with this.

---

### Post by charlitos on 2009-09-24
Well, according to HP Windows Vista Drivers, the drivers for my adapter is called Lite-On USB Wireless LAN. But in any case this is my current PC in which I just installed Ubuntu.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01492765&cc=ca&dlc=en&lc=en&jumpid=reg_R1002_CAEN]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01492765&cc=ca&dlc=en&lc=en&jumpid=reg_R1002_CAEN")

and this is my wireless driver install for Windows Vista
[URL="http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-60704-1&lc=en&dlc=en&cc=ca&lang=en&os=2100&product=3752867"]
http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-60704-1&lc=en&dlc=en&cc=ca&lang=en&os=2100&product=3752867[/URL]

thanks a lot man

---

### Post by tkoco on 2009-09-24
Try reading this thread:
[http://www.linuxquestions.org/questions/slackware-14/realtek-semiconductor-co.-ltd.-rtl81118168b-pci-express-gigabit-ethernet-controller-683656/](http://www.linuxquestions.org/questions/slackware-14/realtek-semiconductor-co.-ltd.-rtl81118168b-pci-express-gigabit-ethernet-controller-683656/)

---

### Post by charlitos on 2009-09-25
> **tkoco said:**
> Try reading this thread:
[http://www.linuxquestions.org/questions/slackware-14/realtek-semiconductor-co.-ltd.-rtl81118168b-pci-express-gigabit-ethernet-controller-683656/](http://www.linuxquestions.org/questions/slackware-14/realtek-semiconductor-co.-ltd.-rtl81118168b-pci-express-gigabit-ethernet-controller-683656/)

that thread doesnt seem to talk about wireless adapters, so Im not really sure what I should be looking for :confused:

I can only use wireless to connect to the internet, thats the only thing that's keeping me away from using Ubuntu, no internet not fun :(

---

