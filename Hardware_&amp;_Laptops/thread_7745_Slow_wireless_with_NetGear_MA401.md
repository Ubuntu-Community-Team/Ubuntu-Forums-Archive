---
title: "Slow wireless with NetGear MA401"
date: 2004-12-10
forum: Hardware &amp; Laptops
---

### Post by theantix on 2004-12-10
I am having multiple problems with my Netgear MA401 Wireless PCMCIA card in
Ubuntu Linux 4.10 warty that I have not had in other Linux distributions or in
Windows.  I am not sure if they are related or not, so I will list them all here
in detail.

* Scanning does not work, the command "iwlist eth1 scan" returns the message
"eth1      Failed to read scan data : Operation not supported" instead of the
list of access points that are normally provided with the iwlist command.  Other
tools like NetworkManager and netapplet also fail to scan for access points.
* Browsing is exceptionally slow, and download speeds range from 10-20kB/s
instead of the 200-300kB/s that I get when connected to a wired network
* iwconfig reports numbers of "Rx invalid crypt" numbers which increment while
browsing or downloading across many types of protocols.

The netgear MA401 was automatically detected by Ubuntu, and as best as I can
determine it is using the orinoco_cs driver which is the same other Linux
distributions use to correctly configure the card.  The problems occur with both
the stock Ubuntu -386 and -686 kernels.  It also occurs with both WEP and
unsecured access points.  I tried to upgrade to hoary, refreshed back to stock
warty, neither solved the problems.

Sample output from "iwconfig eth1":
--------------------
eth1      IEEE 802.11-DS  ESSID:"linksys"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437GHz  Access Point: 00:06:25:A2:02:7C
          Bit Rate:11Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/92  Signal level=5/153  Noise level=112/153
          Rx invalid nwid:0  Rx invalid crypt:268  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
--------------------

If any further information is required, let me know and I would be happy to
provide it in a further comment.

---

### Post by radhaz on 2005-05-16
Did you ever figure out what was causing your invalid crypt issue?  Im having the same problem after I switched the the 686 kernel but using an ipw2200.

---

