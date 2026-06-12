---
title: "PCMCIA nic problems"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by lazerdave on 2006-01-05
I'm trying to use a Sohoware ND5120-E in Ubuntu Breezy on a Compaq Presario 1690 laptop.

cardctl info gives me

PRODID_1="PCMCIA"
PRODID_2="Ethernet"
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=6

cardctl ident gives me

Socket 0:
   product info: "PCMCIA", "Ethernet", "", ""
   function: 6 (network)

cardctl status gives me

Socket 0:
   5V 16-bit PC Card
   function 0: [ready]

When I insert the card, I get 2 high beeps, and then ifconfig eth0 returns

eth0     Link encap: Ethernet  HWaddr 00:80:C6:F6:B5:FE
         BROADCAST  MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
         Interrupt:3 Base address 0x300

Device Manager shows it under the PCI1211 > Unknown Device > Networking Interface

Vendor: Unknown
Device: Unknown
Status: Status
Bus Type: Unknown
Device Type: net.80203
Capabilities: ['net','net.80203']


I know from research and other threads that I need to bind it to "pcnet_cs" but every other example has a card that shows up with a  semi-valid looking MANFID and PRODID's

looking in lsmod, I can see that pcnet_cs is there and used by 1 but more than that I cannot say....

I'm pretty green, but I can't come up with anything particularly helpful so far in all my reading.

Thanks in advance!

---

