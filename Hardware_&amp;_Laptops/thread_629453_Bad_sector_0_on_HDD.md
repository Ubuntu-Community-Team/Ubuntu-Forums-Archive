---
title: "Bad sector 0 on HDD"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by milaz on 2007-12-02
Hi, 
my HDD with a lot of necessary data is broken.
It has bad sectors on it. And sector 0 is one of them.

I bought a new HDD, and installed Ubuntu on it. Now I need to recover data from my old HDD.

I read about ddresque, and would like to use it. The problem is Linux doesn't have a /dev/sdb entry when booted. I got the following errors:

```

Dec  2 17:29:50 zeus kernel: [  507.495280]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
Dec  2 17:29:50 zeus kernel: [  507.516718] ata2.00: configured for UDMA/133
Dec  2 17:29:50 zeus kernel: [  507.516729] ata2: EH complete
Dec  2 17:29:50 zeus kernel: [  517.346986]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
Dec  2 17:29:50 zeus kernel: [  517.361973] ata2.00: configured for UDMA/133
Dec  2 17:29:50 zeus kernel: [  517.361984] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Dec  2 17:29:50 zeus kernel: [  517.361988] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Dec  2 17:29:50 zeus kernel: [  517.361992] Descriptor sense data with sense descriptors (in hex):
Dec  2 17:29:50 zeus kernel: [  517.361994]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec  2 17:29:50 zeus kernel: [  517.362000]         00 00 00 00 
Dec  2 17:29:50 zeus kernel: [  517.362002] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Dec  2 17:29:50 zeus kernel: [  517.362007] end_request: I/O error, dev sdb, sector 0
Dec  2 17:29:50 zeus kernel: [  517.362059] ata2: EH complete
Dec  2 17:29:50 zeus kernel: [  517.362149] sd 1:0:0:0: [sdb] Write Protect is off
Dec  2 17:29:50 zeus kernel: [  527.198672]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
Dec  2 17:29:50 zeus kernel: [  527.219247] ata2.00: configured for UDMA/133
Dec  2 17:29:50 zeus kernel: [  527.219257] ata2: EH complete

```

and it tries to read block 0, which is corrupt, again and again.
Simultaneously, it gives me initramfs prompt, where I enter "return".
Gnome-session is loaded, and in background it still tries to read block 0.

It better give up and let me use /dev/sdb file instead. But no way.

Can anybody help me?
Any ideas how to read bytes from such disk?

---

### Post by mellowd on 2007-12-02
I've used a program called spinrite and it works fantastically in getting data of an old disk - [http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

---

