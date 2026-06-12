---
title: "PCMCIA does not see Merlin U740 3G card?"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by KingE on 2006-07-15
Im trying to get my Novatel 3G data card working. Urgh!!! ] (*,) 

pccardctl say slot 0 is empty, and there is absolutely nothing logged in /var/log/messages. The lights on the card seem to be happy.

Using Ubuntu 6.06 on a Lenovo 3000 N100 notebook.

uname -a
Linux mwe-laptop 2.6.15-26-686 #1 SMP PREEMPT Fri Jul 7 19:48:22 UTC 2006 i686 GNU/Linux

If I look under the synaptic package manager, the 'pcmciautils' is installed and 'pcmcia-cs' is not installed. They seem to be mutually exclusive.

dmesg | grep pcmcia
[17179590.184000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179590.188000] pcmcia: parent PCI bridge Memory window: 0xb3100000 - 0xb31fffff
[17179590.188000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff

I have had a look at this link
[http://mybroadband.co.za/vb/showthread.php?t=21726](http://mybroadband.co.za/vb/showthread.php?t=21726)
but this is only helpful if pcmcia can actually see the card.

Can anyone give me some debugging direction to take?

---

### Post by tturrisi on 2006-07-16
> Can anyone give me some debugging direction to take?
[http://mybroadband.co.za/vb/showthread.php?t=21726&page=17](http://mybroadband.co.za/vb/showthread.php?t=21726&page=17)

---

### Post by arthur on 2006-07-25
Do let us know if you manage to make it work!
;)

---

