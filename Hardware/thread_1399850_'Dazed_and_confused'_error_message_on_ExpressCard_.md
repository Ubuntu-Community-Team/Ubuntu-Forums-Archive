---
title: "'Dazed and confused' error message on ExpressCard insertion"
date: 2010-02-06
forum: Hardware
---

### Post by mango42 on 2010-02-06
Should I take this Syslog error message at face value?

```
yenta_cardbus 0000:04:00.0: ISA IRQ mask 0x0c30, PCI irq 18
yenta_cardbus 0000:04:00.0: Socket status: 30000006
pci_bus 0000:05: Upper limit for fixing this bridge's parent bridge: #04
yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x7fff
pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x7fff: clean.
yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge Memory window: 0xb0300000 - 0xbfffffff
yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd7ffffff
Uhhuh. NMI received for unknown reason b1 on CPU 0.
You have some hardware problem, likely on the PCI bus.
Dazed and confused, but trying to continue
```

...which it does, but no ExpressCard (in this case a Lindy #51500 Firewire interface) recognised. I suspect it *is* a hardware problem on this 2nd-hand T43 Thinkpad but would appreciate some further confirmation.

Thanks,

mango

---

### Post by mango42 on 2010-02-07
Bump

Am I the only one here to have come across this message?

Is this a hardware incompatibility issue or physical damage?

---

### Post by trulan on 2010-02-09
> **mango42 said:**
> ```
Dazed and confused, but trying to continue
```
If my computer were telling me it is dazed and confused, I'd take it at face value...;)

I came here in response to your post in the UbuntuStudio section.  I am indeed a firewire enthusiast, but I have had little or no success at using any express cards in my Dell E1505.  My card is recognized, but I have never been able to get Jack/ffado to communicate withe my audio interface.  Thankfully mine has an internal firewire chip that works very well.

---

### Post by mango42 on 2010-02-09
Many thanks for following this up, trulan. When my 64bit machine comes back from repair, I guess I'll be sending this T43 down the same route (involves two countries - big sketch!)

Yes, I was surprised & amused to get a 'plain English' error msg in syslog, of all places. My only reason for suspecting its apparent meaning was a comment on one of the ffado pages about Ricoh controllers. My **lspci** output shows:-

04:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)

Hey ho - maybe one day I'll get to use my fancy Saffire i/f ;-)

---

