---
title: "Laptop freezes on Network PC card insertion"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by kosmos on 2006-03-31
I have a Sony Picturebook (old C1XS), with a Linksys Etherfast 10/100 + 56K modem PC card, running Breezy. I actually used the card to install over the network, no problem there. But once I upgraded and installed a mess of packages the card will now freeze/hang the entire system whenever it is inserted. 

lspci says I have a Ricoh RL5c475 Card bridge.

The last message (after I insert/remove the card) in dmesg is something like:
eth0: trigger_send() called with the transmitter busy.

I've googled around and tried things like: edit /etc/pcmcia/config.opts to change memory, port and irq settings. Nothing I changed seemed to have an affect. I tried booting with acpi off, but that didn't seem to solve it. I tried putting the option CORE_OPTS="probe_io=0" in /etc/default/pcmcia, no luck. I've also tried booting up the older kernels left by the multiple installation steps I did, but they have the same problem. Obviously, I'm just flailing around due to my ignorance.

Can anyone give me an idea how to debug the situation?

---

### Post by Ptero-4 on 2006-03-31
Are PC cards pnp? IIRC PCMCIA was not meant to be hotswappable and you had to restart your portable to swap PC Cards (that was on Win95 era, I may be outdated on this). Also check your BIOS settings for PCMCIA port inconsistencies.

---

### Post by kosmos on 2006-03-31
Uh, surely you jest? Of course, pcmcia cards are meant to be swapped in and out while the system is running. I've been doing this on linux for years. But this is my first foray into Ubuntu.

Anyway, I decided to try Debian, and it works like a charm, no BIOS changes necessary or anything. The network install went smoothly and my network card now works after the system has been set up too. 

I just have no idea what the problem is under Ubuntu.

---

### Post by wbmj on 2006-03-31
[QUOTE=kosmos]I have a Sony Picturebook (old C1XS), with a Linksys Etherfast 10/100 + 56K modem PC card, running Breezy. I actually used the card to install over the network, no problem there. But once I upgraded and installed a mess of packages the card will now freeze/hang the entire system whenever it is inserted. 

lspci says I have a Ricoh RL5c475 Card bridge.

The last message (after I insert/remove the card) in dmesg is something like:
eth0: trigger_send() called with the transmitter busy.

I've googled around and tried things like: edit /etc/pcmcia/config.opts to change memory, port and irq settings. Nothing I changed seemed to have an affect. I tried booting with acpi off, but that didn't seem to solve it. I tried putting the option CORE_OPTS="probe_io=0" in /etc/default/pcmcia, no luck. I've also tried booting up the older kernels left by the multiple installation steps I did, but they have the same problem. Obviously, I'm just flailing around due to my ignorance.

Can anyone give me an idea how to debug the situation?[/QUOTE]
This may help.....try adding exclude ports 0x800-0x8ff in /etc/pcmcia/config.opts

---

### Post by kosmos on 2006-04-01
[QUOTE=wbmj]This may help.....try adding exclude ports 0x800-0x8ff in /etc/pcmcia/config.opts[/QUOTE]

Breezy already comments that port range out of config.opts by default.
(if by "adding exclude", you mean "excluding")

---

