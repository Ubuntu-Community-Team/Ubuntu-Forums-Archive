---
title: "Freeze when inserting pcmcia card - how to debug"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by Fabratas on 2006-11-29
Hello,

I have installed Edgy Xubuntu on an old Fujitsu Lifebook 690tx (P233, 96Mo). 

I have a problem with a PCMCIA (16bit) Prism-based 802.11b wifi card - when I put it into the slot, the pc freezes. 

The only indication (with tail -f syslog) before the freeze:
"registering new device pcmcia0.0"

and the PC is locked.

The same happens if the card is present during boot.

Any other PCCard I tried (ethernet, USB, Firewire, ATA IDE, either 16 or 32bit card) have been working fine so I suspect something wrong with the actual driver for this card.

Due to the lack of meaningful trace logs, I tried some changes based on reading the forums here and there:
-adding nohdcp and noacpi to the boot options in menu.lst
-adding irq exclusions in pcmcia/config.opts

Then I read about blacklisting the orinoco driver and moving to hostap_cs, however it seems there is a bug that would that prevent from actually working - see [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62685](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62685)

Ideally, I'd like to know how to investigate further -is there any way to pinpoint the source of the freeze - short of recompiling the drivers and removing code step by step  ?

Thanks in advance.

Fab

---

### Post by siucdude on 2007-02-13
I actually have the same thing, my friend wanted me to setup his old dell latitude laptop with xubuntu and it boots up fine with out the pcmcia card.  But as soon as I put it in I can't log into xfce,  It freezes all the time.  I tried to go to recover mode but I can't run any sudo or commands they all freeze.

Please help, M$ runs like crap on this laptop.

Thanks

TJ

---

