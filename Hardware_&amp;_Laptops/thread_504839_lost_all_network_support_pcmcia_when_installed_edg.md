---
title: "lost all network support pcmcia when installed edgy 6.10"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by bscook on 2007-07-19
i just installed ubuntu 6.10 on an old compaq armada e500.  no build in network support, but i have 2 pcmcia network cards for it, a MS MN-120 10/100 card and a D-Link DWL-G630 wireless.  During installation, the DLink card was recognized as Atheros AR5005G 802.11abc NIC.  fine.

But, now I have no network.  at terminal entering  sudo lshw gives:
```
38ff irq:11
 *-network UNCLAIMED
        description: Ethernet controller
        product: AR5005G 802.11abg NIC
        vendor: Atheros Communications, Inc.
        physical id: 3
        bus info: pci@02:00.0
        version: 01
        width: 32 bits
        clock: 33MHz
        capabilities: cap_list
        resources: iomemory: 22000000-2200ffff irq:11

```

my /etc/network/interfaces looks like this:
```
iface ath0 inet dhcp
wireless-essid HOME
auto ath0
```

if i enter "sudo pccardctl ident" I get:
Socket 0:
   no product info available
Socket 1:
   no product info available

if i try restart networking it spits out an error (beginning with copyright, then):
```
 
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Failed to bring up ath0.
                                                     [ok]

```

Right now, I'm toast with no network, no CDrom, no usb.  i have a floppy and a serial port for moving stuff into the notebook.  

how can i get the card working?  it doesn't appear to be recognized...

---

