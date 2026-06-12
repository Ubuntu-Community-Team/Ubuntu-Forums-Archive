---
title: "PCMCIA slots inactive"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by frisket on 2007-03-11
I installed Edgy on an Inspiron 2500 and lspci says there are two otherwise idental CardBus bridge entries 01:03.0 and 01:03.1. And ps says there are two [pccardd] processes (whatever they are) but no cardmgr.

But when I insert a card (any card...modem, ethernet, wireless, memory, etc) there is no reaction: nothing happens, nothing sees it, nothing is mounted, it's as if nothing is even looking at the slots. lshw says they're O2 Micro devices and they've been configured to use yenta.

Is there some missing component here which didn't get installed?

---

### Post by fishymark27 on 2007-03-15
I dunno if this will be any help, but my PCMCIA slot wasn't working and it was because the appropriate module wasn't loaded. If you do lsmod you should be able to see if the pcmcia module you need is loaded. otherwise you can use modprobe to load it.

---

