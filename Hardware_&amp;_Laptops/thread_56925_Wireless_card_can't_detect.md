---
title: "Wireless card can't detect"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by numberexhaust on 2005-08-14
Hey guys... 

I posted in the networking help as well, but I thought that you guys might be able to help as well.

I just recently installed Ubuntu on my laptop with a Proxim Agere Orinoco 802.11b wireless PC card, and the modules (pcmcia-cs, pcmcia, orinoco, orinoco_cs, etc.) are all loaded, but my system still doesn't detect the card!  It's not really a networking issue, more of a hardware one.  (This is my guess, because the light doesn't come on on the card, and it's not detected in System-Administration-Networking, either).

Any help or troubleshooting guide would be appreciated.  The card works on windows fine (i'm running dualboot).

Thanks

---

### Post by invalid on 2005-08-14
Remove the card, re-insert it, and give us the out put of the following command:

dmesg | tail

---

### Post by numberexhaust on 2005-08-14
Here it is:

> asonawalla@ubuntu:~$ dmesg | tail
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 11 (level, low) -> IRQ 11
[drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
mtrr: base(0xe0020000) is not aligned on a size(0x300000) boundary
cs: IO port probe 0x0100-0x04ff: clean.
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
cs: memory probe 0xa0000000-0xa0ffffff: clean.
eth0: no IPv6 routers present
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
asonawalla@ubuntu:~$

---

### Post by numberexhaust on 2005-08-14
OK here is the latest:  apparently my card is being detected but it's not being powered (I think).  Apparently, If I disable acpi, it might work.  Any other ideas while I work on that one?

---

### Post by somuchfortheafter on 2005-08-15
ok 
whenever you plug in the card it should beep. how do the beeps it makes sound compared to each other. one beep is good two beeps the same note is good one high beep and one low beep is bad however.

---

### Post by [Cyanide] on 2005-08-15
[QUOTE=numberexhaust]OK here is the latest:  apparently my card is being detected but it's not being powered (I think).  Apparently, If I disable acpi, it might work.  Any other ideas while I work on that one?[/QUOTE]
 Is there an "ethernet" icon on your System Tray?

You might just need to "Activate" your card...

---

### Post by numberexhaust on 2005-08-16
[QUOTE=somuchfortheafter]ok 
whenever you plug in the card it should beep. how do the beeps it makes sound compared to each other. one beep is good two beeps the same note is good one high beep and one low beep is bad however.[/QUOTE]
 it beeps once...

---

### Post by numberexhaust on 2005-08-16
[QUOTE='[Cyanide]']Is there an "ethernet" icon on your System Tray?

You might just need to "Activate" your card...[/QUOTE]
 if what you're getting at is that the card isn't configured, that's not true.  In system-administration-networking, wireless doesn't even show up along with ethernet and modem.

---

