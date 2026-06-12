---
title: "[SOLVED] fujitsu amilo l1300 wlan problem hardy 8.04"
date: 2008-08-13
forum: Hardware
---

### Post by Eldis on 2008-08-13
Hey,

There is an old thread on this but unfortunately I'm stuck despite it.
[http://ubuntuforums.org/showthread.php?t=217141](http://ubuntuforums.org/showthread.php?t=217141)

I'm having some major headaches getting this wlan working. I can scan for APs, but it can't actually exchange any data with it.

I've mainly used gnome desktops network util to set ESSID etc but so far everytime I get access point: not-associated and no sensible ip address.

Any help would be appreciated

```

wlan0     IEEE 802.11g  ESSID:"Rupert"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```




If I should post more logs just tell me what and I'll do so. (i'm not very experienced so the command to produce that log would also help)

Edit: I've also disabled web encryption for testing reasons until I get a connection working.

Edit2:

lcpci```

01:01.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
```

---

### Post by phidia on 2008-08-13
I think you provided the make and model of your laptop-correct me if I'm wrong-I'm not sure what card you have though. "lspci -v" and/or "lshw -C network" should give the wireless card.

---

### Post by Eldis on 2008-08-14
lcpci```

01:01.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
```

I've also installed software called Wifi Radar I saw in a thread somewhere it might be useful, it does find the AP but also shows very low to no signal. It also fails to retrieve a IP address using dhcp. When inputting a manual IP address it appears to become connected but link quality remains 0 and I can't even ping the AP.

I'm testing this about 10m from the AP direct Line of Sight to the AP. about 4m from me is my Mythbuntu box with a usb wlan card in it that connects fine to the AP. Also my Windows machine about 50m from here without Line of Sight gets good signal.

I've also tried giving the wlan card manual ip address, subnetmask, gateway etc but the link quality remains 0 and nothing works.

I hope this information makes it easier to troubleshoot.

---

### Post by Eldis on 2008-08-14
A bit more info
lshw -C network
```
*-network:0             
       description: Wireless interface
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: wmaster0
       version: 01
       serial: 00:90:4b:d6:82:2d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=prism54pci latency=64 maxlatency=28 mingnt=10 module=p54pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 10
       serial: 00:40:d0:6f:de:83
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.6 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

---

### Post by phidia on 2008-08-14
There's a list [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") under the heading "By Manufacturer" I don't see that manufacturer name there. It could be a rebranding situation or the card may not be supported.

---

### Post by Eldis on 2008-08-15
I got this working yesterday using ndiswrapper, I tried it a few days ago but didn't work but now I found a better guide for using ndiswrapper and got it.

sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9
sudo apt-get install ndiswrapper-utils-ndisgtk
sudo rmmod p54pci
sudo rmmod p54common

Got XP drivers from Fujitsu pages for amilo l1300 and unpacked them into my home directory.
Then: System-Administrate-Windows Wireless drivers
Install new driver ja look for Prisma00.inf file and pressed ok

sudo /etc/inid.d/networking restart
Then I checked with the networking tool my wlan settings and it started working. Using Web encryption haven't tried the others.

---

### Post by matc on 2008-08-15
Funny thing. I have exactly the same laptop and also the Intersil Prism and for me it only worked with the p54pci driver but ndiswrapper refused connecting to a WPA secured network...

---

### Post by Eldis on 2008-08-17
> **matc said:**
> Funny thing. I have exactly the same laptop and also the Intersil Prism and for me it only worked with the p54pci driver but ndiswrapper refused connecting to a WPA secured network...

Thats really odd, but then again I didn't try WPA secured at all, just WEB.

---

