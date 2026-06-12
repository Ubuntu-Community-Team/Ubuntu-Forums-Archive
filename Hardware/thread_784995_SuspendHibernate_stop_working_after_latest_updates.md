---
title: "Suspend/Hibernate stop working after latest updates on hardy"
date: 2008-05-07
forum: Hardware
---

### Post by drolyk on 2008-05-07
Hi All!

I`ve got hardy installed on hp pavilion dv6720er and everything was perfect before latest updates. For now suspend/hibernate doesn`t work - there is blank screeen when wakes up everetime.

I`ve got enabled all ubuntu repos: updates, proposed, security.

any advice ?

thanks

---

### Post by goldsniper on 2008-05-07
for my lappy, suspend does work and hibernate never worked since gutsy. Its no different for hardy. Hibernate still doesn't work. 

Im using HP Compaq Presario V3000

---

### Post by publicskill on 2008-05-07
> **drolyk said:**
> suspend/hibernate doesn`t work - there is blank screeen when wakes up everetime

I have similar effect but only sometimes. Different time I got WHITE screen, and another my system hangs, and only hard reset helps :(

But the funniest thing is that if I write my password when have black/white screen, system resume :)

Try this, just write your pw when you have black screen. 
This isn't a solution, but maybe this can help in diagnosing a problem...

---

### Post by pajatopmr on 2008-05-07
I suffer from this issue as well, sort of.  It first happened after I screwed up the machine name (removed it unwittingly from /etc/hosts).  After restoring the name correctly, suspend/resume started working again.  Then I added some networks to /etc/networks and saw that my USB sub-system was disconnecting (my external keyboard/mouse stopped working) after a suspend/resume cycle.  I have yet to understand this issue or find any magic that restores correctly functioning suspend/resume.  The messages log does have a complaint about dhcdbd:

May  7 03:56:14 lilly dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name

but I think this is a red herring since the following occurs first:

May  6 17:20:50 lilly kernel: [    8.800129] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
May  6 17:20:50 lilly kernel: [    8.963095] usb 1-1: configuration #1 chosen from 1 choice
May  6 17:20:50 lilly kernel: [    8.971335] usb 1-2: USB disconnect, address 5
May  6 17:20:50 lilly kernel: [    9.039522] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  6 17:20:50 lilly kernel: [    9.361456] usb 5-7: USB disconnect, address 4
May  6 17:20:50 lilly kernel: [    9.361461] usb 5-7.3: USB disconnect, address 5
May  6 17:20:51 lilly kernel: [    9.466791] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  6 17:20:51 lilly kernel: [    9.693830] usb 5-7.4: USB disconnect, address 6
May  6 17:20:51 lilly kernel: [    9.693838] usb 5-7.4.1: USB disconnect, address 7
May  6 17:20:51 lilly kernel: [    9.693842] usb 5-7.4.1.1: USB disconnect, address 8
May  6 17:20:51 lilly kernel: [   10.087835] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  6 17:20:54 lilly kernel: [   12.535013] tg3: eth0: Link is up at 1000 Mbps, full duplex.
May  6 17:20:54 lilly kernel: [   12.535018] tg3: eth0: Flow control is on for TX and on for RX.

---

