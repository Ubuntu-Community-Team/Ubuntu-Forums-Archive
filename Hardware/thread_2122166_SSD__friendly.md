---
title: "SSD  friendly"
date: 2013-03-04
forum: Hardware
---

### Post by KegHead on 2013-03-04
Hi!

Is there an SSD that is friendly  with 12.10?

Thanks!

KegHead

---

### Post by Cheesemill on 2013-03-04
All of them.

---

### Post by KegHead on 2013-03-04
Hi!

I read recently that there were some problems.

Are they all cleared up?

KegHead

---

### Post by sasparilla on 2013-03-05
Does 12.10 actually support TRIM?

---

### Post by Cheesemill on 2013-03-05
Trim support has been built in to the kernel for about two and a half years now.

You just need to activate it by adding the discard option to your /etc/fstab file

---

### Post by KegHead on 2013-03-07
Hi!

Thanks!

KegHead

---

### Post by KegHead on 2013-04-02
Hi!

Trying to find an inexpensive 16 gb or 32gb ssd only as a boot drive.

Any ideas where to find one in the US?

Thanks!

KegHead

---

### Post by blrossjr79 on 2013-04-02
Im using an intel 520 SSD now and it works great

---

### Post by blrossjr79 on 2013-04-02
> **KegHead said:**
> Hi!

Trying to find an inexpensive 16 gb or 32gb ssd only as a boot drive.

Any ideas where to find one in the US?

Thanks!

KegHead

Newegg, Tiger Direct. Unless you want Brick store, then BB, Staples, Etc.

---

### Post by dabl on 2013-04-02
> **KegHead said:**
> Hi!

Trying to find an inexpensive 16 gb or 32gb ssd only as a boot drive.

Any ideas where to find one in the US?

Thanks!

KegHead

I've been using the world's cheapest Kingston 15GB SSD for my /boot (and the rest for swap) for over 2 years now.  (There are reasons -- my OCZ Revodrive PCI SSD is not recognized as a bootable device by my Asus AMI BIOS, which I only discovered after I bought it).  I partitioned the Kingston into a 512MB partition, formatted that ext2, and left the rest for swap.  It works perfectly.  Here it is:

```
root@imerabox:/# hdparm -iI /dev/sdc

/dev/sdc:

 Model=KINGSTON SS100S216G, FwRev=D100719a, SerialNo=16GAA0002142
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=31277232
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


ATA device, with non-removable media
        Model Number:       KINGSTON SS100S216G                     
        Serial Number:      16GAA0002142        
        Firmware Revision:  D100719a
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
```

---

