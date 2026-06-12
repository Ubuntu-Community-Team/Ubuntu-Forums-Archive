---
title: "Internal WiFi driver problems"
date: 2008-07-12
forum: General Help
---

### Post by carl99fan on 2008-07-12
I just installed Ubuntu on this Acer aspire 7525-5071
has an amd Athlon 64 X2 1.8GHz 
my problem is getting ubuntu to "see" the internal 802.11b/g WLAN

I don't know what I need to do. I have installed restricted extras.
This is my first attempt at installing the 64 bit version, also my first laptop attempt.

---

### Post by carl99fan on 2008-07-12
OK I now know I have what they call Acer® InviLink

Here is my output.

john@john-laptop:~$ sudo lshw -class network
[sudo] password for john: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:77:ba:ca
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.2.4 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
If someone could steer me in the right direction, this is all I know how to do.:confused:

---

### Post by carl99fan on 2008-07-13
Still working on this one....

Thought I would post a comment, in hopes it would catch the eye of an informed laptop Ubuntu user.

---

### Post by ghost_ryder35 on 2008-07-13
this is a bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201180](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201180)

i think one user posted a workaround in the report

---

### Post by neilevan814 on 2008-07-13
Hi, if you have Broadcom WLAN drivers b43 drivers...do a lookup here for installing wireless b43.  You will find many helpful posts, of which I just got through using myself about an hour ago, for using ndiswrapper and blacklisting b43.  There seems to be some problem using the restricted drivers here...Good Luck!   I hope this helps...not very often I can be helpful.
Neil

---

### Post by carl99fan on 2008-07-18
Sorry guys this Info is over my head.

I have read a lot and I just am not grasping it.

It seems that this Acer is a little harder to make work than others.

Would it be easier to put a card in the side of it like the old laptops? Would I get that to work?

---

### Post by cybrsaylr on 2008-07-19
Wireless networks seem to be a bit tricky with linux.
I just got my new Tosiba laptop wireless working after a couple days using the 'Networking & Wireless' forums here. The guys were helpful and by going through those threads I found one the matched right up with my problem and helped to get it running. You may want to look over there.

---

### Post by carl99fan on 2008-07-19
> **cybrsaylr said:**
> Wireless networks seem to be a bit tricky with linux.
I just got my new Tosiba laptop wireless working after a couple days using the 'Networking & Wireless' forums here. The guys were helpful and by going through those threads I found one the matched right up with my problem and helped to get it running. You may want to look over there.

wow...I am in the wrong forum... Wow.. I guess it would also help if I was smart enough to read the forums.. lol

---

