---
title: "Ubuntu 5.10 &amp; wlan &amp; IBM TP 600"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by Jackal82 on 2006-02-02
Hello everyone!

I have huge problems getting my A-Link WL54PC working with Breezy. The card is supported by Ubuntu (Ralink 2500) and I am sometimes(?) able to scan available access points but the lights of my card are not blinking and I cannot get an IP address with DHCP or static IP.

The card worked fine with winXP before so it's not a hardware conflict.

My kernel is 2.6.12-10.26

lspci says: Network controller: Ralink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

/boot/grub/menu.lst has "acpi=off pnpbios=off" and quickboot is off. I also tried "pci=noacpi pci=usepirqmask vga=790" but no help.

iwconfig finds my card but I do not receive or transfer any data.
dmesg says ra0: no IPv6 routers present

The biggest problem really is to get my card "waking up".

I also installed Ralink wlan drivers but no help.

So I am more than greatful if someone could help me with this. 
And I have used Linux for three weeks now so... :)

---

### Post by djroadrash on 2006-02-02
hi jackal82
have u tried using the terminal to turn it on? do this first:
```
sudo iwconfig 
```
you should see a lo and something else
if you see something called eth0 or something like it (ra0, wireless0 etc..)
do this next
```
sudo ifconfig eth0 up
```
your card should turn on
now if you use wep do this
```
sudo iwconfig eth0 essid (put your network id here) mode managed key s:(put password)
```
then do this to get ip address
```
sudo dhclient eth0
```

hope this helps
good luck
djroadrash:)

---

### Post by Jackal82 on 2006-02-03
[QUOTE=djroadrash]hi jackal82
have u tried using the terminal to turn it on? do this first:
```
sudo iwconfig 
```
you should see a lo and something else
if you see something called eth0 or something like it (ra0, wireless0 etc..)
do this next
```
sudo ifconfig eth0 up
```
your card should turn on
now if you use wep do this
```
sudo iwconfig eth0 essid (put your network id here) mode managed key s:(put password)
```
then do this to get ip address
```
sudo dhclient eth0
```

hope this helps
good luck
djroadrash:)[/QUOTE]

iwconfig:
eth0      RT2500 Wireless  ESSID:"wlan"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power=- 1
          RTS thr: off   Fragment thr: off
          Encryption key: off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-214 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo ifconfig eth0 up:
lights are off. Card is activited but it "sleeps"

sudo iwconfig eth0 essid...:
nothing happens

sudo dhclient eth0:
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:08:a1:87:a0:0a
Sending on   LPF/eth0/00:08:a1:87:a0:0a
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
Trying recorded lease 10.31.0.214
PING 10.31.0.1 (10.31.0.1) 56(84) bytes of data.

--- 10.31.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.945/1.945/1.945/0.000 ms
bound: renewal in 274228 seconds.


so.. any ideas..?

---

### Post by Jackal82 on 2006-02-06
Problem solved with this:

[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig?highlight=%28ralink%29](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig?highlight=%28ralink%29)

---

### Post by djroadrash on 2006-02-10
glad to hear.

---

