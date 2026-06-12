---
title: "Wireless on LL/10.04, HP Pavillion"
date: 2011-05-22
forum: Hardware
---

### Post by randomsusers on 2011-05-22
I have two Pavilions, one a DV-8000 and the other a DV-7. I can post the exact model if needed.

I loaded 10.04, but have been unable to establish a wireless connection with either one. I have checked for a hardware driver (System -> Administration -> Hardware Drivers) but the only one listed is for my ATI graphics card. I have a wired connection which works fine - I'm on it now. But I travel and I need to access wireless from the hotels. 

tom@Owl:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:5a:b7:b0:4d  
          inet addr:192.168.100.97  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::223:5aff:feb7:b04d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5672731 (5.6 MB)  TX bytes:577116 (577.1 KB)
          Interrupt:28 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:2d:20:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tom@Owl:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management:off
          
tom@Owl:~$ sudo lshw -C network
[sudo] password for tom: 
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:5e:2d:20:6c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d1100000-d110ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:b7:b0:4d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.100.97 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d103ffff(prefetchable)

Oddly enough, everything worked fine when I was running 8.04, 64-bit. I did downgrade back to 32-bit after trying the 64 and first running into this problem. Of course, both machine have AMD processors, or I wouldn't have tried 64-bit in the first place.

I know the network information, name, password and security. WPA2 PSK. I enter the data, select connect and get nothing. If anyone can suggest a command to print something that will help me out, I'd appreciate it.

---

### Post by randomsusers on 2011-05-24
Can someone suggest a command which might get me closer to a solution? I can't help but feel that I'm missing something easy and that some command with either fix it, or at least give me a better idea of what is wrong.

---

