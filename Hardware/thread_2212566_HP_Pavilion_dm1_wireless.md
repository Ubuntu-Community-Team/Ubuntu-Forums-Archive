---
title: "HP Pavilion dm1 wireless"
date: 2014-03-21
forum: Hardware
---

### Post by 1DoLittle on 2014-03-21
My dual boot HP laptop Pavilion dm1 has wireless and audio that can be turned on/off from the keyboard when using Windows 7.
Both the wireless and audio work with windows 7.
When in lubuntu I cannot find a way to turn on either of these items. I have tried rfkill and it did not give me the fix.
rfkill list all will show a hard block, but removing the hard block does not permit the wireless to work (grayed out)
rfkill unblock all did not help

I have tries several possible solutions found in the forum, but they did not work.

Does anyone have a solution?

---

### Post by varunendra on 2014-03-21
Were you able to remove the "hard block" from the wireless? How?

If both hard and soft blocks were set to "no", and the "Enable Wireless" option in Network Manager menu was still grayed out, then it probably doesn't have the required driver installed.

Please post back the outputs of -
```
lspci -nnk | grep -iA2 net
uname -mr
lsb_release -d
```

---

### Post by 1DoLittle on 2014-03-21
The keyboard will remove the hard block from the wireless. (The bluetooth sees my cell phone)
rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lspci -nnk | grep -iA2 net
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7 [1022:1719]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: brcmsmac
    Kernel modules: bcma, brcmsmac
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3387]
    Kernel driver in use: r8169

uname -mr
3.2.0-60-generic x86_64

lsb_release -d
Description:    Ubuntu 12.04.4 LTS

---

### Post by varunendra on 2014-03-22
Please try -
```
sudo modprobe -v brcmsmac
```
Does this enable wireless? If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

Command outputs should always be posted within 'Code' tags. You should edit your above post too to do so now.

---

### Post by 1DoLittle on 2014-03-22
The following code did not help
```

sudo modprobe -v brcmsmac

```

Wireless information
```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux HP-Laptop 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: brcmsmac

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3387]
    Kernel driver in use: r8169

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:d217 Suyin Corp. 
Bus 006 Device 002: ID 0a5c:21e3 Broadcom Corp. 

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.165
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             204.194.232.200
    DNS:             204.194.234.200

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

wlan0     No scan results

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### lsmod #####

bcma                   26696  0 
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     DB27B1DE461446E6FBADCFE
depends:        
intree:         Y
vermagic:       3.2.0-60-generic SMP mod_unload modversions 

##### modules #####

lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   16.138154] brcmsmac 0000:03:00.0: bus 3 slot 0 func 0 irq 3
[   16.138254] brcmsmac 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.138265] brcmsmac 0000:03:00.0: setting latency timer to 64
[   16.541971] Bluetooth: can't load firmware, may not work correctly
[   19.850113] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   19.850124] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   19.851090] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   19.852087] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.853554] ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

---

### Post by varunendra on 2014-03-22
Did you try without the Ethernet cable plugged? Network Manager, and even some BIOS may not let wifi work when a cable connection is detected. So unplug the cable, reboot and try connecting to wifi.

If there is still no success, please try installing the sta driver *(usually we strictly instruct to keep away from it with this card, but I personally believe the native one on kernel version lower than 3.8 was not good enough, so..)*. While being connected to internet via cable, please do -
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
Closely observe the installation messages in the terminal and post back if you see any errors. If it installed smoothly, reboot and try to connect. Does it connect now?

If not, please run the wireless_script again and post back the fresh report, with the sta driver installed this time.

---

### Post by 1DoLittle on 2014-03-22
The good news is the wireless is working.
I made several steps that did not help - including making a MD5SUM check on the ISO and reinstalling the operating system. Not the problem.
What did fix the problem was to use additional drivers and install a different driver from ubuntu.

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux HP-Laptop 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: wl

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3387]
    Kernel driver in use: r8169

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:d217 Suyin Corp. 
Bus 006 Device 002: ID 0a5c:21e3 Broadcom Corp. 

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.165
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             204.194.232.200
    DNS:             204.194.234.200

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    dlink:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Guest:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    Key1202:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    jason dill:      Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA2
    home:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

##### iwlist #####

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00054775657374
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
                    IE: Unknown: 3D1601080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
                    IE: Unknown: 3D1601080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD270050F204104A0001101044000102104700100000000000001000000014D64D28E11E103C000103
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Key1202"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00074B657931323032
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"belkin.732"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 000A62656C6B696E2E373332
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010008
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603050000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 05 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00094E4554474541523432
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050400020012
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409080800000000000000000000000000000000000000
                    IE: Unknown: 3D1609080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000

##### iwlist channel #####

eth1      26 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### lsmod #####

wl                   3074895  0 
cfg80211              205774  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl

##### modinfo #####

filename:       /lib/modules/3.2.0-60-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     CBEDDD2D4888AAD1517D3C9
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.2.0-60-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

##### modules #####

lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.1/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x050d:0x2103 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   15.657436] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.692885] wl 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.692898] wl 0000:03:00.0: setting latency timer to 64
[   15.751079] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   16.052437] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   16.068946] Bluetooth: can't load firmware, may not work correctly
[   30.752174] eth1: no IPv6 routers present
[  151.301650] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  151.301667] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  151.301692] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  151.301703] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  151.301725] ERROR @wl_dev_intvar_get : error (-1)
[  151.301733] ERROR @wl_cfg80211_get_tx_power : error (-1)
[12402.605308] ERROR @wl_dev_intvar_get : error (-1)
[12402.605324] ERROR @wl_cfg80211_get_tx_power : error (-1)

########## wireless info END ############



```

Thanks for your help - great service.

---

### Post by varunendra on 2014-03-22
Glad you got it working!

Keep in mind that when (if) you upgraded to kernel 3.8 or above, you'll probably need to purge the current sta driver -
```
sudo apt-get purge bcmwl-kernel-source
```
..to let the native "brcmsmac" work again. It works much better than the sta driver in kernel versions 3.8 and above.

If you decided to upgrade to Ubuntu 14.04 when it comes out in April, it will come with kernel 3.13 by default.

---

