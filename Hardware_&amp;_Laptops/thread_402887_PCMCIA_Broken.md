---
title: "PCMCIA Broken?"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by oceanhippie on 2007-04-06
recon my self far from incompetant at thunmping PCMCIA into working....normally.

However I cannot get ANY PCMCIA or CF card to work on edgy or Dapper. and I've got heaps of the things. Cardbus works fine, so do the cards under windows.
The nub of the problem is that to os never identifiys the card there for cant loadadriver for it.

The output of pccardctl always says:
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

What ever card is in it...

Dmesg notice's the card going in but, nowt else.
[17181248.556000] pccard: PCMCIA card inserted into slot 0
[17181246.288000] pccard: card ejected from slot 0

That was an orinoco Gold(ahem flashed silver) going in, and out (I have loaded the right modules).
[17181248.556000] pccard: PCMCIA card inserted into slot 0
[17181246.288000] pccard: card ejected from slot 0
That was PRSMII going in and out.

and a CF card in a converter....
[17181248.556000] pccard: PCMCIA card inserted into slot 0
[17181246.288000] pccard: card ejected from slot 0 

The CF adapter, cf cards (the CF prism 2 wifi card of my zaurus and mem do the same), modem/10/100 netcard/ Aronet 240/50's don't work either.

My Cisco atheros works fine, as a does an Edimax ralink - but they are cardbus and i NEED the orinoco's anntenna socket and the WDS meshing of the Prism 2 cards.... I Run a wide area WiFi net on Brighton Beach.

I't could be and  IBM thing, but a mate (also grade A one linux wifi geek) has same trouble on a Dell.

here's the relavent output of stuff

Socket 0:
  no product info available
Socket 1:
  no product info available
some potential dmesg stuff:
[17179571.664000] ACPI: bus type pci registered
[17179571.708000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179593.360000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179595.116000] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[17179595.116000] orinoco_pci: Detected device 0000:01:02.0, mem:0xf8000000-0xf8000fff, irq 11
[17179596.216000] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[17180445.152000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179594.832000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[17179594.832000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xdfffffff
[17179594.832000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf80fffff
[17179594.960000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[17179594.960000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xdfffffff
[17179594.960000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf80fffff
[17179594.704000] Yenta: CardBus bridge found at 0000:01:00.0 [1014:0185]
[17179594.832000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179594.832000] Yenta: CardBus bridge found at 0000:01:00.1 [1014:0185]
[17179594.960000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179594.960000] Yenta: Raising subordinate bus# of parent bus (#01) from #07 to #09
/etc/pcmcia/config.opts
include memory 0xc0000-0xfffff
include memory 0xa0000000-0xa0ffffff
include memory 0x60000000-0x60ffffff
relavent lspci stuff
0000:01:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
0000:01:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
        Bus: primary=00, secondary=01, subordinate=09, sec-latency=64
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Bus: primary=01, secondary=06, subordinate=09, sec-latency=176

---

