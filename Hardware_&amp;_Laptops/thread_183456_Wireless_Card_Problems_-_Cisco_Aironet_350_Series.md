---
title: "Wireless Card Problems - Cisco Aironet 350 Series"
date: 2006-05-28
forum: Hardware &amp; Laptops
---

### Post by Spidylicious on 2006-05-28
I have already searched through the forums to find solutions for this, but the answers either didn't help, were over my head, or were old and the links were broken.  

I'm using Ubuntu 5.10 (the latest release) on a Dell Lattitude C610.  My wireless card is a Aironet 350 series, specifically a AIR-PCM352.  According to previous posts that I have found about this card, it is fully compatible with this version of Linux and there should be no drivers needed.

The basic problem is that I can't get online using this card.  

_Here's what I know so far:_

This is a picture of my Network Settings.  I have no idea why it has two wireless connections listed, I only have one wireless card.  

[IMG]http://www.osuweb.com/36/00086535.jpg[/IMG]


I've tried different combinations of enabling one, and disabling the other.  None of that has helped.




A friend of mine told me to go into the terminal and type this:
> 
ifconfig eth0 essid yournetworknamehere key yourencryptionkeyhereifyouhaveoneotherwisejusttypeoff

And this is what I got:
> "erik@Superman:~$ ifconfig eth1 Eriks place key 5137030643
Eriks: Host name lookup failure
ifconfig: '--help' gives usage information."

I realize that it's having problems with a 2-word network name, and I've tried it with a 1-word network as well.  I got the same error.




Here's what my ifconfig looks like:
> erik@Superman:~$ ifconfig
eth0 Link encap:UNSPEC HWaddr 00-08-E3-E1-79-79-00-69-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:2312 Metric:1
RX packets:0 errors:1161 dropped:0 overruns:0 frame:1161
TX packets:10 errors:21 dropped:0 overruns:0 carrier:21
collisions:0 txqueuelen:100
RX bytes:0 (0.0 b) TX bytes:5466 (5.3 KiB)
Interrupt:3 Base address:0x100

eth1 Link encap:Ethernet HWaddr 00:08:E3:E1:79:79
inet6 addr: fe80::208:e3ff:fee1:7979/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:1161 dropped:0 overruns:0 frame:1161
TX packets:10 errors:21 dropped:0 overruns:0 carrier:21
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:5466 (5.3 KiB)
Interrupt:3 Base address:0x100

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1291 errors:0 dropped:0 overruns:0 frame:0
TX packets:1291 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:115857 (113.1 KiB) TX bytes:115857 (113.1 KiB)

(The MAC address of the card I'm using is 0008E3E17979.)  As you can see, I'm not getting an IP.  However, when I click "properties" on eth0 (active), and I click on the SSID block, it picks up all of the networks in the area, including my own (Eriks place).  Obviously the network card is working, but I can't make it connect to anything.

Does anyone have any other ideas?

---

### Post by brain.g on 2006-05-31
I am also having troubles with my Cisco wireless card in a similar Dell laptop.  So far I haven't found a solution either.  Maybe it will be resolved in Dapper?

---

### Post by Spidylicious on 2006-06-04
What's Dapper?

---

