---
title: "PCMCIA: NEtgear WG511 card not recognized"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by coogor on 2005-08-05
Kubuntu standard installation on a ThinkPad 770. 
A 3Com 3c589 Network card is configured and works fine. 
But when I insert a Netgear WG511 (prism54-Chipset), the card is not even detected. No entry in /var/log/messages, cardctl gives the following: 
 
root@tp770:/home/axel # cardctl status 
Socket 0: 
  3.3V CardBus card 
  function 0: [ready] 
 
(Means the card itself is available) 
 
root@tp770:/home/axel # cardctl info 
PRODID_1="" 
PRODID_2="" 
PRODID_3="" 
PRODID_4="" 
MANFID=0000,0000 
FUNCID=255 
 
(...but not recognized) 
The same card works fine with SuSE 9.3 on a ThinkPad A30, and also under w98 on the same machine. 

Any ideas how to solve this?

TIA!

---

### Post by s_p_a_r_k_y on 2005-08-05
try loading the prism54 module.

```
 sudo modprobe prism54
```
and see what dmesg outputs

---

### Post by coogor on 2005-08-06
Hm, the prism module is not the issue:

Loaded prism54 driver, version 1.2

But the message after inserting the card looks strange (means: never seen before) :???:

PCI: device 0000:05:00.0 has unknown header type 7f, ignoring.

How can this be fixed??

---

### Post by s_p_a_r_k_y on 2005-08-06
if you boot up under knoppix do you have access to it? If so try looking at the kernel version

```
 uname -a
```
Maybe you need a newer kernel? also take a look at lsmod and see which modules it has loaded which could be controlling the device... I usually mount my root partition and lsmod > /mnt/hda1/somewhere/lsmod.knoppix

so I can read it when I reboot under ubuntu without printing it out and wasting paper

---

### Post by coogor on 2005-08-07
knoppix with a 2.6 kernel does not start, it stops with a kernel panic  :neutral: 
I doubt that it has to do with the kernel version: I was using the card for over a year using SUSE 9.1 on a different laptop. 9.1 has a kernel 2.6.6, whereas hoary has a 2.6.10.

---

### Post by elsewhere on 2005-08-07
Netgear's most recent version (v3) of the WG511 doesn't actually use the prism54 chipset, this has caused grief for many users but isn't difficult to workaround (I know, because I'm one of those users myself).

If your card indicates it was Made in China (check the label on the bottom), then you're using the card that is incompatible with the prism54 driver, although it identifies itself as being so (bad, bad Netgear!).

The workaround was do disable the prism54 module from loading (adding it to /etc/hotplug/blacklist) and then using ndiswrapper with the windows driver from the cd-rom.  It's a one time setup but has been working fine for me since.

A google search on "wg511", "ndiswrapper" and "made in china" will turn up loads of info.

On the other hand, if you're using one of the earlier, "true" prism54 cards, then the problem is something altogether different.

Anyways, hope this helps...

Cheers,
KV

---

### Post by coogor on 2005-08-08
It is definitely a card with the prism-chipset, the problem is earlier in time, to my understanding condensing to the PCI-support (The message: 
PCI: device 0000:05:00.0 has unknown header type 7f, ignoring.) after inserting the card.

---

### Post by coogor on 2005-08-12
This device cant also be accessed with knoppix.

From a different machine, the result of lspci -vv is:
[FONT=Courier New]0000:03:00.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)
        Subsystem: Netgear WG511 Wireless Adapter
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66Mhz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 80 (2500ns min, 7000ns max), cache line size 08
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 18800000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [dc] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
[/FONT]
Does that help???

---

