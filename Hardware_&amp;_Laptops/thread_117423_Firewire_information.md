---
title: "Firewire information?"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by nalmeth on 2006-01-14
EDIT:
By 'firewire' I mean 'firmware'..

I'm trying to get breezy going on a sony viao laptop.
Here are the specs:
Mobile AMD DuronTM processor 800 MHz 15" XGA TFT screen

The only things that are holding this back, are:

(1) My wireless card is not detected in the port. I have run all the common commands to find this out, and I'm certain that for whatever reason, the card is just not registered by the laptop. This isn't right, because it used to run on Windows 98 or 2000 or ME, and because I have checked the card on another laptop, and it works fine. The card is a D-Link DWL-G650, for which driver support is included in the kernel - THIS IS NOT A DRIVER SUPPORT ISSUE. So, little as I know about wireless/hardware, I think I've narrowed it down to a firmware issue (as suggested by someone else), because I doubt that the port is busted - though I don't rule this out.

(2) I have two batteries, and when fully charged, they use up their power EXTREMELY fast. I can't blame this on ubuntu, because likely the batteries simply suck. But I have a sneaking suspision it might be related to the fireware issue again. Can anyone rule this out?

SO, my questions are:
Can anyone offer any ideas *excluding* a firmware issue, as to why I might be having these problems, and if not
Can anyone tell me how to update my firmware, or where I can find out how?

I went to Sony's site, and the only driver updates they offer right off the site are for migrating from one Windows platform to another. Nothing about linux. And in order to contact them, I have to give a lot of imformation I think is unneccessary, so I thought I would try here first.

If you have any thoughts on any of this, I welcome them, and they are appreciated.

:???:     :smile:

---

### Post by Zelut on 2006-01-14
Any firmware updates would most likely be provided by the manufacturer.  When I've updated firmware on my desktop motherboards I got it from the manufacturer of the board.  You could look into that..

As far as your wireless goes.. dmesg doesn't recognize a card at all?  That seems odd.  I've seen that card supported (thru ndiswrapper)..

no tips on the battery, sorry.

---

### Post by nalmeth on 2006-01-14
I had not run dmesg yet, and it did not appear there, but this might mean something:
```
[   25.248824] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   25.248910] 8139cp: pci dev 0000:00:10.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   25.248918] 8139cp: Try the "8139too" driver instead.
[   25.252758] 8139too Fast Ethernet driver 0.9.27[   25.252857] PCI: setting IRQ 10 as level-triggered
[   25.252865] PCI: Assigned IRQ 10 for device 0000:00:10.0
[   25.252882] IRQ routing conflict for 0000:00:07.5, have irq 5, want irq 10
[   25.252891] IRQ routing conflict for 0000:00:07.6, have irq 5, want irq 10
[   25.252901] PCI: Sharing IRQ 10 with 0000:00:0a.1
[   25.252925] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   25.253324] eth0: RealTek RTL8139 at 0x1800, 08:00:46:1d:83:fe, IRQ 10
[   25.253331] eth0:  Identified 8139 chip type 'RTL-8139C'

```
What does this mean? Did Ubuntu automatically try the 8139too driver? Or what? Does this mean anything to anyone?
```

[   66.482865] Linux Kernel Card Services
[   66.482875]   options:  [pci] [cardbus] [pm]
[   66.517705] PCI: IRQ 9 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[   66.517723] PCI: Assigned IRQ 9 for device 0000:00:0a.0
[   66.517786] Yenta: CardBus bridge found at 0000:00:0a.0 [104d:80e3]
[   66.517832] Yenta: Enabling burst memory read transactions
[   66.517841] Yenta: Using CSCINT to route CSC interrupts to PCI
[   66.517846] Yenta: Routing CardBus interrupts to PCI
[   66.517856] Yenta TI: socket 0000:00:0a.0, mfunc 0x012c1222, devctl 0x66
[   66.738903] Yenta: ISA IRQ mask 0x0808, PCI irq 9
[   66.738912] Socket status: 30000006
[   66.778525] PCI: IRQ 10 for device 0000:00:0a.1 doesn't match PIRQ mask - try pci=usepirqmask
[   66.778540] PCI: Found IRQ 10 for device 0000:00:0a.1
[   66.778559] IRQ routing conflict for 0000:00:07.5, have irq 5, want irq 10
[   66.778568] IRQ routing conflict for 0000:00:07.6, have irq 5, want irq 10
[   66.778581] PCI: Sharing IRQ 10 with 0000:00:10.0
[   66.778627] Yenta: CardBus bridge found at 0000:00:0a.1 [104d:80e3]
[   66.778676] Yenta: Using CSCINT to route CSC interrupts to PCI
[   66.778682] Yenta: Routing CardBus interrupts to PCI
[   66.778692] Yenta TI: socket 0000:00:0a.1, mfunc 0x012c1222, devctl 0x66
[   66.999773] Yenta: ISA IRQ mask 0x0808, PCI irq 10
[   66.999782] Socket status: 30000006

```
Or this?

---

### Post by Zelut on 2006-01-14
It looks like it sees your card.  I would suggest trying using ndiswrapper.  Maybe give this page a try for some details..

[http://christer.homeip.net/wireless.html](http://christer.homeip.net/wireless.html)

---

### Post by nalmeth on 2006-01-14
ndiswrapper was the first thing I tried, and when I found the drivers online and installed them, ndisgtk told me that the hardware wasn't found.
What told you the card was detected? I couldn't pick it out. I suppose its time I had a tough run in like this, because I've been in the dark about wireless for a long time.
keep em coming!
thanks!

EDIT: 
thanks for the link aswell. I'll try what is outlined here.
lspci gets me nothing in the way of wireless, only my ethernet card is picked up.

---

### Post by nalmeth on 2006-01-15
ok, just in case this can help out:
```
lspci
*0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365* [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc.: Unknown device b115
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
0000:00:07.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 20)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1420
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1420
0000:00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

lspci -n
[I]0000:00:00.0 0600: 1106:0305 (rev 03)
[/I]0000:00:01.0 0604: 1106:b115
0000:00:07.0 0601: 1106:0686 (rev 22)
0000:00:07.1 0101: 1106:0571 (rev 10)
0000:00:07.2 0c03: 1106:3038 (rev 10)
0000:00:07.3 0c03: 1106:3038 (rev 10)
0000:00:07.4 0601: 1106:3057 (rev 30)
0000:00:07.5 0401: 1106:3058 (rev 20)
0000:00:07.6 0780: 1106:3068 (rev 20)
0000:00:0a.0 0607: 104c:ac51
0000:00:0a.1 0607: 104c:ac51
0000:00:0e.0 0c00: 104c:8020
0000:00:10.0 0200: 10ec:8139 (rev 10)
0000:01:00.0 0300: 1002:4c4d (rev 64)

```
[http://christer.homeip.net/wireless.html](http://christer.homeip.net/wireless.html) tells me to > "Note the first column such as 0000:00:0c.0"
and > "Find the matching column number from Step 2: and write down the PCI ID (ex: 14e4:4320 (rev 02))"

*0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365* [KT133/KM133]

[I]0000:00:00.0 0600: 1106:0305 (rev 03)
[/I]

> "...search for the PCI ID you found at the link above..."
the PCI ID I need is 1106:0305? This PCI ID is not present on the wiki page referenced to find the right driver. Did I miss a step here? It looks like my card was not picked up by either command, as there are no columns containing 0000:00:0c.0 <-- with a c.

Could old firmware be responsible for this type of miss, or would it just effect performance? Any thoughts?
EDIT: sudo did not reveal anything with lscpi -n

---

### Post by handy on 2006-01-15
Have you looked on the sony site for a firmware upgrade?

It has happened to me where I have taken a looong way around to find that a firmware upgrade was waiting for me that solved the problem & would have saved me so much time & effort.

It's probably only a very small chance, but shouldn't take to long to verify.

Good luck...:KS

---

### Post by nalmeth on 2006-01-15
What did you need a firmware upgrade for? Was it easy to obtain/setup? I have heard it can be a dangerous thing to do, but if done correctly usually solves the problem. This seems to be leading to contacting sony for new firmware. I've gone through their site, and they offer updates when upgrading from one Windows platform to another. Nothing about linux. I wanted to avoid contacting them directly if possible, but unless there are other ideas, I may have to now.

---

### Post by handy on 2006-01-16
Hi Nalmeth, 

I've often needed to flash the BIOS in motherboards, not so often the firmware in CD but more often the firmware in DVD drives to remove the country zone protection.  For DVD burners you can also sometimes get improvements in performance.  Rarely there have been some exotic PCI cards that you can upgrade firmware on too.  Oh yeah, my modem/router, I've flashed that too, it is also flash upgradable to ADSL2, that will be a while comming to where I live though. :( 

Most often you are given the option to save your current firmware before you overwrite it.  As long as you don't have a power outage, or some other bizaar phenomenon it is really quite safe.

As far as obtaining the little varmints, well, some are made really easy by the manufacturer, others you have to search for on the manufacturers site, others are made by firmware hackers, & they can be hardest to find.  For DVD stuff look around for doom9.  (I hope I'm not going to get into trouble again! :rolleyes: )  That is not a link! :p

I hope you find a satisfactory solution...

---

