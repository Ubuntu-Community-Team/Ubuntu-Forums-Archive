---
title: "Wireless adapter (RTL8191SU chipset): device not ready"
date: 2010-07-03
forum: Hardware
---

### Post by Parsa86 on 2010-07-03
Hi,

I have a USB wireless adapter (Sumvision 300Mbps Wireless N USB Adapter), which has the RTL8191SU chipset. I have been following this guide: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Which seems to be awesome but I have had little luck. Can someone please help?!

1- I have no LAN connection

2- I have loaded up the XP driver through ndiswrapper 1.56 for the chipset (no driver for this adapter is available at the moment).

3- below is the relevant part of the response to the **nm-tool **:

> NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:21:85:72:33:0D

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 -----------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xU
  State:             unavailable
  Default:           no
  HW Address:        08:10:74:8D:20:D3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

4- And also for list hardware (**lshw**) command:

          >  *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 01
                serial: 00:21:85:72:33:0d
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
                resources: irq:28 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:cc00(size=32)
      
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 08:10:74:8d:20:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

5- And also below is the response to the **iwconfig** command:

> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

6- And also for "iwlist scan"

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

7- Also for:  "**lshw -C network**":

>   *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:21:85:72:33:0d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 08:10:74:8d:20:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

Many thanks,

---

### Post by IcarusR on 2010-07-04
Driver available from Realtek website...

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU")

Or older version here

[http://download504.mediafire.com/netmxw3yaybg/zxgmyniz2hd/rtl8192su_linux_2.6.0002.0708.2009.tar.gz]("http://download504.mediafire.com/netmxw3yaybg/zxgmyniz2hd/rtl8192su_linux_2.6.0002.0708.2009.tar.gz")

---

### Post by Parsa86 on 2010-07-05
Thanks - the new one didn't work but older worked great, read me file was great!

---

### Post by RyuzakiTenseiga on 2010-07-06
So I such a N00b . Could you help me understand the read me and give me the step by step please.

---

