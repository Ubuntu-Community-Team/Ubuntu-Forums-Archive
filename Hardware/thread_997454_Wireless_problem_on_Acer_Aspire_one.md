---
title: "Wireless problem on Acer Aspire one"
date: 2008-11-29
forum: Hardware
---

### Post by victorbrca on 2008-11-29
Hi all,


I had 8.04 installed and running ok on my new Acer Aspire One for a good two weeks. I started having problems with my wireless, up to the point were it would not connect. I was using ndiswrapper and decided to install madwifi; that also did not work.

Ran a clean install of 8.10, it worked for the first night and them it stopped. 

Anyone has any ideas??


- Driver:
5xxx series of Atheros 802.11 wireless lan cards


**Trying to bring card up**
```
$ sudo ifconfig -v -a wlan0 up
SIOCSIFFLAGS: Resource temporarily unavailable
WARNING: at least one error occured. (-1)
```


**List all devices**
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:68:c2:2b:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:803186508 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

pan0      Link encap:Ethernet  HWaddr e6:99:c0:97:21:69  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:69:3c:e5:a4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-69-3C-E5-A4-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

**iwconfig output**
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

**lshw output**
```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:c2:2b:65
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:69:3c:e5:a4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:99:c0:97:21:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```


**Output from modules**
```
$ tail -n 3 /etc/modules 
\fuse
lp
ath5k
```


**daemon.log**
```
daemon.log
daemon.log:Nov 29 20:47:39 columbus NetworkManager: <info>  (wlan0): supplicant manager is now in state 1 (from 0). 
daemon.log:Nov 29 20:47:43 columbus NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
daemon.log:Nov 29 20:47:43 columbus NetworkManager: <info>  (wlan0): bringing up device. 
daemon.log:Nov 29 20:47:43 columbus NetworkManager: <WARN>  nm_device_hw_bring_up(): (wlan0): device not up after timeout! 
daemon.log:Nov 29 20:47:43 columbus NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
daemon.log:Nov 29 20:47:44 columbus NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
daemon.log:Nov 29 20:47:44 columbus NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
```


**kern.log**
```
kern.log
kern.log:Nov 29 20:00:07 columbus kernel: [   37.260439] wlan0: associated
kern.log:Nov 29 20:00:07 columbus kernel: [   37.260957] wlan0: disassociating by local choice (reason=3)
kern.log:Nov 29 20:00:49 columbus kernel: [   79.695297] wlan0: Failed to config new BSSID to the low-level driver
kern.log:Nov 29 20:00:56 columbus kernel: [   86.456823] wlan0: authenticate with AP 00:14:bf:07:9f:d4
kern.log:Nov 29 20:00:56 columbus kernel: [   86.653116] wlan0: authenticate with AP 00:14:bf:07:9f:d4
kern.log:Nov 29 20:00:57 columbus kernel: [   87.414006] wlan0: authenticate with AP 00:14:bf:07:9f:d4
kern.log:Nov 29 20:00:57 columbus kernel: [   87.612115] wlan0: authentication with AP 00:14:bf:07:9f:d4 timed out
kern.log:Nov 29 20:02:02 columbus kernel: [  152.471381] wlan0: Failed to config new SSID to the low-level driver
kern.log:Nov 29 20:10:39 columbus kernel: [  669.695667] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```


**syslog**
```
syslog
syslog:Nov 29 20:24:52 columbus NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
syslog:Nov 29 20:24:52 columbus NetworkManager: <info>  (wlan0): bringing up device. 
syslog:Nov 29 20:24:52 columbus NetworkManager: <WARN>  nm_device_hw_bring_up(): (wlan0): device not up after timeout! 
syslog:Nov 29 20:24:52 columbus NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
syslog:Nov 29 20:24:52 columbus NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
syslog:Nov 29 20:24:53 columbus NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
syslog:Nov 29 20:47:39 columbus NetworkManager: <info>  wlan0: driver is 'ath5k_pci'. 
syslog:Nov 29 20:47:39 columbus NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
syslog:Nov 29 20:47:39 columbus NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
syslog:Nov 29 20:47:39 columbus NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_22_69_3c_e5_a4 
syslog:Nov 29 20:47:39 columbus nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_22_69_3c_e5_a4, iface: wlan0)
```

---

### Post by loligator on 2008-11-30
Just making sure but:
Did you add it to your modules? (Yours Doesn't look the same as mine, which is ath_pci)
otherwise when you restart it will no longer work.
I am now having this problem also.

---

