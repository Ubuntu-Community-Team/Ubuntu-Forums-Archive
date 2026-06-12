---
title: "Configuring D-Link and/or Netgear"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by TopKnot on 2005-02-09
I have an old Toshiba 2675DVD notebook that does not have built in ethernet. I have 2 notebook cards one is a D-Link DFE-690TXD and the other is a Netgear FA411. In the past I have had the netgear working with Suse 9.1 but after switching to Ubuntu I could no longer connect. With the D-Link connected the following lines are in dmesg 

"8139too Fast Ethernet driver 0.9.27"
"eth0: RealTek RTL8139 at 0x4000, 00:0d:88:44:b8:4e, IRQ 11"
"eth0: Identified 8139 chip type 'RTL-8139C'"

After booting I can enter network configuration and the card is recognized but when I try to activate the eth0 it turns itself of after a few seconds. If I run ifconfig at this point it shows a IPv6 address. Not sure why. The card is also found in hardware config identified the same as above.

This card does come with linux drivers, but since I have only dabbled in linux over the years (making the full switch now, with the notable exception of work) I am not sure on how to go ahead and install the new drivers/module.


Pretty much the same with the Netgear card, but no drivers seem to be available.

Thanks in advance for any help.

---

### Post by alastair on 2005-02-09
After booting - before net config :

What is output of : 

grep eth /var/log/dmesg
ifconfig -a
route -n

Then set up your network (GUI?) and repeat the ifconfig and route commands - output?

In use - to track what happens - run a different shell window and "tail -f" your syslog - you will see immediately anything odd happening i.e.

shell : sudo tail -f /var/log/syslog

... do your thing ...

Is anything printed in syslog when/if the network card stops working?

---

### Post by TopKnot on 2005-02-09
Will do.

---

