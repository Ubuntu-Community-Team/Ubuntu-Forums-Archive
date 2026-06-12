---
title: "[SOLVED] my network manager doesnt recognize my wireless connection"
date: 2008-10-16
forum: General Help
---

### Post by guss606 on 2008-10-16
hi all.
i installed ubuntu 8.04, I'm using wireless connection.. when i press on network manager it displays many wireless connections of the neighbors but mine is not one of them.. the network manager cannot see my connection.. i tried to manually add it but didn't worked.. pleaseeeeeeeeeee help me ASAP... i need ubuntu.. I'm sick with windows

---

### Post by 3rdalbum on 2008-10-16
If your wireless network is "Wireless N" and the Linux driver for your wireless card only supports the more common "Wireless G", then you will only see the G networks and not your N network.

Try logging into your wireless router's web interface from another computer, or your Ubuntu computer when connected by wire, and change the setting to allow wireless G connections to your router.

---

### Post by guss606 on 2008-10-16
thanks for your reply, as you can see in the picture [ATTACH]88556[/ATTACH] i did try all the potions but the same problem still exist... any help please

---

### Post by kodalisrikanth on 2008-10-16
First you should post your network card details. Then only the people can understand your problem.

There are two possibilities to get this problem.

1.The operating system does not have support for your network card type.
2.You may disable the wireless network card.

      I guess ubuntu have lot of support for new type of hardware. Connect the system with wire. Then try to update the system. You may find the solution to the problem.

---

### Post by guss606 on 2008-10-16
hi,, 
i connected my ubuntu via cable and updated it, then i tried the wireless connection again but the same problem still exist..
anyway, i use BELKIN Wireless G Plus MIMO USB Network Adapter, Model number F5D9050
please guys i need help with this

---

### Post by Yellow Pasque on 2008-10-16
Please post the output of:
```
sudo lshw -C network
cat /etc/network/interfaces
iwconfig
```

---

### Post by guss606 on 2008-10-16
this is while connecting via cable
guss@guss-desktop:~$ sudo lshw -C network
sudo: unable to resolve host guss-desktop
[sudo] password for guss: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:ca:58:1a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.3 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:24:78:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

guss@guss-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback






guss@guss-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:3A:4F:4D   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and this when i unplugged the cable and plugged the USB wireless
guss@guss-desktop:~$ sudo lshw -C network
sudo: unable to resolve host guss-desktop
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:ca:58:1a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:24:78:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

guss@guss-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback






guss@guss-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Trevster on 2008-10-16
This may be a long shot but I wonder if your wireless card just doesn't support channel 13. Maybe try a lower channel on your router.

---

### Post by guss606 on 2008-10-17
Thanks Trevster, finally it worked... thanks alot.. BUT there is another problem, I'm only less than 1 meter away from the router and the connection speed 5 Mbps... look at the picture [ATTACH]88611[/ATTACH] and the signal strength is 52% -76% ... i guess it should be higher when I'm that close to the router

---

### Post by Trevster on 2008-10-17
Glad it is working.

Set your router to use 802.11g only and see if that increases the connection speed.

---

### Post by guss606 on 2008-10-18
i tried that, but sadly didn't work too... i donno whats happening here, hope you guys can help :(

---

