---
title: "Wireless card suggestions. What works?"
date: 2005-01-15
forum: Hardware &amp; Laptops
---

### Post by Lynx on 2005-01-15
Hey guys, I need to purchase a wireless card and router. It would greatly help to get some advice on what brands would work best with my Ubuntu latptop (I run on a Dell 5150). Anything you can suggest would be great, thank a bunch.

---

### Post by Shaggy on 2005-01-15
Using Ndiswrapper you should be able to get a lot cards to work that don't have native linux support.  I got even my broadcom card to install using that.  

Aside from that cards with native linux support.  Some Cisco Aironet cards, Lucent Ornico cards, and mostly anything with a Prism or Prism2 chipset.

---

### Post by Dan on 2005-01-15
aironet 350 card, I don't think you can get a better one.

---

### Post by Lynx on 2005-01-15
Thanks guys, I'll check those out, would I need to buy online or are there stores that carry them? How much might I expect to shell out for them.

---

### Post by Krash1201 on 2005-01-15
orinoco cards have linux support.  lynksis routers should to.  ndis wrapper can be a pain in the butt, but it will make windows drivers work for anything if you install it right.

---

### Post by HankB on 2005-01-16
I've had real good luck with a Netgear WG511T card and Netgear WGT624 router. I downloaded and compiled the drivers myself, but I understand they're may be available as an Ubuntu package.

You can get these bundled together for a semi-reasonable price.

---

### Post by jerome bettis on 2005-01-17
i'm using the intel pro 2200 on my laptop here.  the driver is under active development right now.  when i first got it (v0.02) it sucked ass in just about every way possible.  3 months later, (v0.19) and it's acceptable - not perfect though.  

the connection is usually pretty fast, but every now and then it cuts off and the module has to be reloaded and the interface restarted.  it also seems to have difficulty connecting to routers that are semi far away.  the signal reports 100%, i can sometimes get connected but i won't be able to receive any data.

---

### Post by nocturn on 2005-01-17
Generally, everything with a prism54 driver works out of the box (kernel support).

I have an SMC -g PCMCIA card and it does very well.

---

### Post by byourg on 2005-01-18
I have a Blitzz 712 super G wireless card and it worked no probelm. :smile:

---

### Post by mmuller on 2005-01-18
[QUOTE=nocturn]Generally, everything with a prism54 driver works out of the box (kernel support).

I have an SMC -g PCMCIA card and it does very well.[/QUOTE]

WG511 works without problem, best implementation of support for this card that I have found so far. Beats Mandrake10.1 and FC3 into a cocked hat...

---

### Post by node on 2005-01-18
My notebook uses a 3com office connect 802.11g card, works out of the box.

---

### Post by sharingan on 2005-02-12
[QUOTE=node]My notebook uses a 3com office connect 802.11g card, works out of the box.[/QUOTE]

hi

i've bought a 3COM OfficeConnect Wireless 11g PC Card (3CRWE154G72) but i cannot make it work. 

how did you do to make it work out of the box?

thnx for any info!

---

### Post by pg133 on 2005-04-16
[QUOTE=sharingan]hi

i've bought a 3COM OfficeConnect Wireless 11g PC Card (3CRWE154G72) but i cannot make it work. aptic

how did you do to make it work out of the box?

thnx for any info![/QUOTE]

I got this card to work using the ndiswrapper:

make sure that ndiswapper is installed with the synaptic package manager

You will also need a copy of the windows driver, which you can get from the 3com web site, you will need to install the driver with ndiswapper.

(my copy was held on /mnt/3com/extract3)
ndiswrapper -i /mnt/3com/extract3/disk1/Driver/3c154g72.inf

To get it to work:
rmmod prism54 (remove prism54, as i think this stops ndiswrapper working)
rmmod ndiswrapper (just incase)

modprobe ndiswrapper

I used the gui to system->administration->networking to configure the card
and set the ESSID via the properties button andto active the card.

some other useful commands are:
dmesg    (for error messages)
iwconfig
iwlist wlan0 scan
ifconfig wlan0 up

I am running Linux ubuntu 2.6.10-5-686
with 3com hardware given by
 lspci | grep 3com

0000:02:00.0 Network controller: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] (rev 01)

lspci -n
0000:02:00.0 0280: 10b7:6001 (rev 01)

---

### Post by sharingan on 2005-04-17
hi

i also finally managed to make my 3Com card to work using ndiswrapper.
instead of removing the prism54 module i added it to the [FONT=Courier New]/etc/hotplug/blacklist[/FONT]

anyway, i still don't fully understand why this card is not working out of the box. it's supposed to work with prism54 module, but it doesn't...

i have upgraded today to hoary, removed ndiswrapper in order to give the prism54 module another try, and still doesn't work!!!

this is what i got in the syslog (maybe someone can provide further info about this issue):

```
Apr 17 17:48:03 localhost dhclient: sit0: unknown hardware address type 776
Apr 17 17:48:03 localhost kernel: eth1: resetting device...
Apr 17 17:48:03 localhost kernel: eth1: uploading firmware...
Apr 17 17:48:03 localhost kernel: eth1: firmware version: 1.0.4.3
Apr 17 17:48:03 localhost kernel: eth1: firmware upload complete
Apr 17 17:48:04 localhost kernel: eth1: no 'reset complete' IRQ seen - retrying
Apr 17 17:48:05 localhost kernel: eth1: no 'reset complete' IRQ seen - retrying
Apr 17 17:48:05 localhost kernel: eth1: interface reset failure
Apr 17 17:48:05 localhost kernel: prism54: Your card/socket may be faulty, or IRQ line too busy :(
Apr 17 17:48:05 localhost kernel: eth1: resetting device...
Apr 17 17:48:05 localhost kernel: eth1: uploading firmware...
Apr 17 17:48:05 localhost kernel: eth1: firmware version: 1.0.4.3
Apr 17 17:48:05 localhost kernel: eth1: firmware upload complete
Apr 17 17:48:06 localhost kernel: eth1: no 'reset complete' IRQ seen - retrying
Apr 17 17:48:07 localhost kernel: eth1: no 'reset complete' IRQ seen - retrying
Apr 17 17:48:07 localhost kernel: eth1: interface reset failure
Apr 17 17:48:07 localhost kernel: prism54: Your card/socket may be faulty, or IRQ line too busy :(
Apr 17 17:48:08 localhost dhclient: sit0: unknown hardware address type 776
Apr 17 17:48:08 localhost dhclient: Listening on LPF/eth1/00:30:b4:00:00:00
Apr 17 17:48:08 localhost dhclient: Sending on   LPF/eth1/00:30:b4:00:00:00
Apr 17 17:48:08 localhost dhclient: Sending on   Socket/fallback
Apr 17 17:48:08 localhost dhclient: receive_packet failed on eth1: Network is down
Apr 17 17:48:12 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 17 17:48:12 localhost dhclient: send_packet: Network is down
Apr 17 17:48:17 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 17 17:48:17 localhost dhclient: send_packet: Network is down
Apr 17 17:48:30 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
Apr 17 17:48:30 localhost dhclient: send_packet: Network is down
Apr 17 17:48:48 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 17 17:48:48 localhost dhclient: send_packet: Network is down
Apr 17 17:49:01 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr 17 17:49:01 localhost dhclient: send_packet: Network is down
Apr 17 17:49:13 localhost dhclient: No DHCPOFFERS received.
Apr 17 17:49:13 localhost dhclient: No working leases in persistent database - sleeping.
Apr 17 17:56:32 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr 17 17:56:32 localhost dhclient: send_packet: Network is down
Apr 17 17:56:36 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr 17 17:56:36 localhost dhclient: send_packet: Network is down
Apr 17 17:56:45 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr 17 17:56:45 localhost dhclient: send_packet: Network is down
Apr 17 17:57:00 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr 17 17:57:00 localhost dhclient: send_packet: Network is down
Apr 17 17:57:11 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 17 17:57:11 localhost dhclient: send_packet: Network is down
Apr 17 17:57:18 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 17 17:57:18 localhost dhclient: send_packet: Network is down
Apr 17 17:57:26 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 17 17:57:26 localhost dhclient: send_packet: Network is down
Apr 17 17:57:33 localhost dhclient: No DHCPOFFERS received.
Apr 17 17:57:33 localhost dhclient: No working leases in persistent database - sleeping.
Apr 17 18:02:39 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 17 18:02:39 localhost dhclient: send_packet: Network is down
Apr 17 18:02:46 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr 17 18:02:46 localhost dhclient: send_packet: Network is down
Apr 17 18:02:55 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 17 18:02:55 localhost dhclient: send_packet: Network is down
Apr 17 18:03:03 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Apr 17 18:03:03 localhost dhclient: send_packet: Network is down
Apr 17 18:03:20 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
```

i'm starting to think that this card is not really supported by the prism54 module...

cheers!!

---

### Post by nautilus on 2005-04-17
i don't think it is... is it this one:

Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)

because it may be the "macless" version of the card, which the prism54 driver can't do.  this looks very similar to what i saw with my card.

if it is the same one, on the ndiswrapper wiki, under drivers, look for the "smc2835w" driver.

and back on-topic, i have heard excellent reviews on the D-Link ExtremeG PCI card, which has full Linux support and it's extremely easy to find (and cheap to boot :))

---

### Post by sharingan on 2005-04-17
i guess i have a "macless" 3Com pc-card...

i found this with google:
[URL=http://news.tiker.net/node/205]
The State of 802.11g Wireless Networking in Linux[/URL] 

*The Intersil PrismGT was a hopeful contender, until the card manufacturers discovered that they can save a few cents on each card if they stick the MAC-layer processing into the host driver instead of the card’s firmware. (This cheaper type of card is called SoftMAC and will make the prism54 driver complain about “no 'reset complete' IRQ seen - retrying” and “prism54: Your card/socket may be faulty, or IRQ line too busy”). The driver is complete, functional and open, but it doesn’t support the SoftMAC cards, and the earlier hardware versions that aren’t SoftMAC are nowhere to be found, not even on ebay.*

i think **ndiswrapper** is my only chance  :mrgreen:

---

