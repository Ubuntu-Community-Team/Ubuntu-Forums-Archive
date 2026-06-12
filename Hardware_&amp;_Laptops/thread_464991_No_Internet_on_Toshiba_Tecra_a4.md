---
title: "No Internet on Toshiba Tecra a4"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by lucien2000 on 2007-06-05
I am struggling with my internet on my Tecra A4. 
I have 7.04 installed with the latest updates. Kernel: 2.6.20-16-generic
Both built in Wireless and Wired are recognized but I had no success so far connecting to the net.  
I am able to connect to the internet with an old pcmcia cisco card but would like to use Wired and the build in wireless. 

lspci
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

For the wireless I installed the latest ipw2200 drivers and firmware, but no luck. 
The network manager and ifconfig don't recognize the intel wireless. 

I also commented out all the interfaces in /etc/network/interfaces except LO.
auto lo
iface lo inet loopback

sudo tcpdump 
tcpdump: WARNING: eth1: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes

0 packets captured
0 packets received by filter
0 packets dropped by kernel

Any suggestions 

Thanks
L

---

