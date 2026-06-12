---
title: "My wireless network card does not work"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by erik_aslin on 2007-06-12
Hello! I am a novis both to ubuntu and network in general.  Right now I have manage to connect to the internet via my ethernet cable. But I have no clue how to solve the wireless situation. I have a build in network card into my compaq pressario 2500. (europe). with feisty Fawn 7.04, 

And this is the network info: (that to me is like reading greek)

erik@erik-laptop:~$ sudo lshw -C network
  *-network:0 DISABLED   
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 latency=64 link=no multicast=yes
       resources: iomemory:d0006000-d0006fff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:28:a5:4a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=83.250.195.216 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:2400-24ff iomemory:d0004000-d0004fff irq:10

no idea what I should do now, please help me someone!? 

All tips are welcome. I tried reading the guides but my english is not perfect and I dont understand. Thanks!
best regards Erik

---

### Post by stchman on 2007-06-12
> **erik_aslin said:**
> Hello! I am a novis both to ubuntu and network in general.  Right now I have manage to connect to the internet via my ethernet cable. But I have no clue how to solve the wireless situation. I have a build in network card into my compaq pressario 2500. (europe). with feisty Fawn 7.04, 

And this is the network info: (that to me is like reading greek)

erik@erik-laptop:~$ sudo lshw -C network
  *-network:0 DISABLED   
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 latency=64 link=no multicast=yes
       resources: iomemory:d0006000-d0006fff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:28:a5:4a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=83.250.195.216 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:2400-24ff iomemory:d0004000-d0004fff irq:10

no idea what I should do now, please help me someone!? 

All tips are welcome. I tried reading the guides but my english is not perfect and I dont understand. Thanks!
best regards Erik

Post the output of an lspci here.  We need to know the chipset of your wireless card.

---

### Post by erik_aslin on 2007-06-12
here is the ipsci

erik@erik-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
erik@erik-laptop:~$ 

regards!

---

### Post by dannyboy79 on 2007-06-12
> **erik_aslin said:**
> Hello! I am a novis both to ubuntu and network in general.  Right now I have manage to connect to the internet via my ethernet cable. But I have no clue how to solve the wireless situation. I have a build in network card into my compaq pressario 2500. (europe). with feisty Fawn 7.04, 

And this is the network info: (that to me is like reading greek)

erik@erik-laptop:~$ sudo lshw -C network
  *-network:0 DISABLED   
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 latency=64 link=no multicast=yes
       resources: iomemory:d0006000-d0006fff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:28:a5:4a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=83.250.195.216 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:2400-24ff iomemory:d0004000-d0004fff irq:10

no idea what I should do now, please help me someone!? 

All tips are welcome. I tried reading the guides but my english is not perfect and I dont understand. Thanks!
best regards Erik

please read post number 9 here: [http://ubuntuforums.org/showthread.php?t=454436&highlight=Prism+2.5+Wavelan+chipset](http://ubuntuforums.org/showthread.php?t=454436&highlight=Prism+2.5+Wavelan+chipset)

it's the same chipset that you have.

---

### Post by stchman on 2007-06-12
People have gotten the Prism card working.  Refer here.

[http://ubuntuforums.org/showthread.php?t=454436](http://ubuntuforums.org/showthread.php?t=454436)

---

### Post by erik_aslin on 2007-06-12
This was a disaster. I did as quoted below. But then when I rebooted my computer I loged in as usual but then the brown desktop screen was there and I could not do anything. 

I tried to go into the file to remove the strings via terminal in safe mode but it was impossible to open the blacklist file. when I entered gksudo gedit /etc/modprobe.d/blacklist   my computer hung up.    PLEASE HELP ME,   right now I am using the live-cd. 


blacklisted in /etc/modprobe.d/blacklist file
Code:

blacklist hostap 
blacklist hostap_pci
blacklist prism2
blacklist prism2pci
blacklist prism2_pci

2. added this to /etc/network/interfaces because only had eth0 and eth2
Code:

# wireless entry for the prism 2.5 card
auto wlan0 
iface wlan0 inet dhcp

---

### Post by erik_aslin on 2007-06-12
OK my computer is running fine again. I managed to delete the strings i entered into both 
/etc/modprobe.d/blacklist
 and 
etc/network/interfaces 

What should I do now?   

I really need to get the wireless card to work soon.

Best regards

---

### Post by dannyboy79 on 2007-06-12
well if you followed it to the "T" than I am sorry and I can't help anymore as I don't have that card. try it again and notice that he states lower down that it's appearing as eth1 and not wlan0 so try the eth1 instead, just a shot in the dark but worth it.

---

### Post by erik_aslin on 2007-06-13
Hey! Its working now!

thanks a lot. I still am having problems with connecting to the wireless networks (FON) but i suppose that is an issue for another thread!

big thanks!

---

### Post by dannyboy79 on 2007-06-13
glad you got it working. do some searching around and I am sure you'll find a solution to your new issue.

---

