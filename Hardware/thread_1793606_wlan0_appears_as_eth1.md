---
title: "wlan0 appears as eth1"
date: 2011-06-29
forum: Hardware
---

### Post by fatoddsun on 2011-06-29
Hi there!
I have an ASUS 1015PEM netPC and I'm experiencing a problem with the last release of Ubuntu and my wireless card.

Everything have worked fine so far, but if I try to run sw like airodump or wireshark I get a lot of problems 'cause my wifi card is recognised as an ethernet card for wired connections.

I have no problem surfing the internet using wireless connections, but when I try to use those kind of software, they just don't work because the interface appears as "eth1" instead of "wlan0" or whatever.

Could you help me, please?

Here's my iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

and my card, from lspci:
```

01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

```

thanks,
bye!

---

### Post by mikewhatever on 2011-06-29
The name of the interface is irrelevant, just replace the one in the tutorial with what you have. If it doesn't work, it's probably because of the driver. For example, if you use Broadcom's STA driver, then putting the card into the monitor mode shouldn't work, and you may need to patch the driver or use another one.

---

### Post by fatoddsun on 2011-06-30
I see. How can I know which driver I am currently using and what should I install in order to replace it with a better one?

Thank you very much,
bye

---

### Post by mikewhatever on 2011-06-30
Whether your card is compatible with aircrack-ng, and what driver to use are usually the hard things to figure out.
Check out the two links below, or simply google and see what luck others had had with the same card.

[http://www.aircrack-ng.org/doku.php?id=compatible_cards&DokuWiki=cd24941b6492af922c84dc4a4bbfa95f](http://www.aircrack-ng.org/doku.php?id=compatible_cards&DokuWiki=cd24941b6492af922c84dc4a4bbfa95f)
[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=cd24941b6492af922c84dc4a4bbfa95f](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=cd24941b6492af922c84dc4a4bbfa95f)

---

