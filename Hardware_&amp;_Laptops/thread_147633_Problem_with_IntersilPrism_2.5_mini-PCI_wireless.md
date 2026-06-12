---
title: "Problem with Intersil/Prism 2.5 mini-PCI wireless"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by Ensnared on 2006-03-20
Hello,

I'm having huge problems getting my wireless-card on my laptop working. I've pretty much tried everything I've found on the subject, both with the kernel orinoco_pci/orinoco/hermes drivers (which are put up for the card as default after installation), ndiswrapper and hostap, as well as upgrading the card firmware. Either I'm doing something terribly wrong, or my card simply isn't supported at all in Linux. All the documentation I've read indicates it should be supported, but those docs usually involve PCMCIA-cards or USB-cards with the Prism 2.5 chipset.

Anyway, what I'm wondering is if anyone's got the same card I do, and have it working under Linux (specifically Ubuntu 5.10, though I've also tried other distros but logically that shouldn't matter as the kernel and drivers are pretty much the same). My card is listed as such from lspci -v:
```
0000:00:05.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
Subsystem: Actiontec Electronics Inc: Unknown device 1406
Flags: medium devsel, IRQ11
Memory at e8006000 (32-bit prefetchable) [size=4k]
Capabilities: [dc] Power Management version 2
```

What happens is I can't connect to my wireless router in any way. The output from iwconfig is as such:
```
eth1    IEEE 802.11-DS  ESSID:"HOME"  Nickname:"Prism I"
        Mode:Managed  Frequency:2.467GHz  Access Point: 44:44:44:44:44:44
        Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
        Retry min limit:8   RTS thr:off   Fragment thr:off
        Power Management:off
        Link Quality=0/92  Signal level=-68 dBm Noise level=-122dBm
        Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The key and ESSID (as defined in /etc/network/interfaces) are correct - they're the same values used in Windows XP, where eveything works nicely. When I run ifup eth1 it doesn't get the IP from my DHCP-server, and if I try to provide a static IP in the proper address-space I can't ping the wireless router.

I'm not quite sure which information could be helpfull in tracking down the problem, but if anyone are able to help, just ask and I'll provide any information requested - I'd really like to get this working as that means I can remove Windows XP from that computer entirely.

As for the laptop itself, it's an Elite Group Green732, and in Windows the wireless card is identified as "Accton WN3101A Mini-PCI Wireless Adapter" (which is what I used to find the drivers I needed to try ndiswrapper) if that makes any difference. Firmware versions are 1.1.1 (Primary) and 1.7.4 (Station). I've also tried Station versions 1.4.9 and 1.5.6 and 1.8.4 but neither made any difference.

If anyone could help me out with this I'd really appreciate it :)

---

### Post by Ensnared on 2006-03-24
Just in case anyone else are having the same problem, I'll post an update. I didn't really expect to get any help in this - this isn't the first time I try, but apparently not a lot of people using Linux have this wireless-card.

After picking apart my laptop and looking at the card, it seems it's an "Actiontec 802MIP", and some quick and dirty google-voodoo indicates that it's not possible to get this card working under Linux.

I did stumble upon some Windows drivers from one of IBM's laptops which ship with that card, and using them with ndiswrapper atleast gives the expected output in dmesg - with the original Windows-drivers, dmesg only listed that ndiswrapper was loaded, but atleast now I get confirmation that the card is activated, and it shows up in iwconfig. It does not however communicate in any way - the AP is listed as 00:00:00:00:00 while all the other info (WEP-key, ESSID, channel/frequency, etc) is correct and the signal strength is 92/92. It does not get any IP-address from my DHCP-server, and setting a static one does not help in any way.

So I guess it's a lost cause. This card refuses to work under Linux no matter what I do, and since it's now an old and outdated card I doubt there'll ever be made any driver for it either. One used to be able to count on Linux supporting all kinds of old hardware, but times change, even in that respect ;)

Luckily it's possible to switch the card for another one, so I'm gonna see about finding one that fits and make sure it's supported in Linux, and replace the damn thing. Heck, on the bright side I'll be able to get more than 11Mbps this way :)

---

