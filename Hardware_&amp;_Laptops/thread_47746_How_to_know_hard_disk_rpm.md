---
title: "How to know hard disk rpm?"
date: 2005-07-09
forum: Hardware &amp; Laptops
---

### Post by shidai.liu on 2005-07-09
Hi all,

Is there a tool to test the hard disk rpm and cache size?

hdparm -i /dev/hda gives this:
```
 Model=HTS548080M9AT00, FwRev=MG4OA5EA, SerialNo=MRL455L4JV8XVB
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=7877kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:

 * signifies the current active mode
```

---

### Post by DarkManX4lf on 2005-07-09
i dont know of a tool that woudl tell you, maybe someoen else does, but if you do know the model of your harddrive then you can go to the manufacturere website and get the full specs from them.

---

### Post by shidai.liu on 2005-07-10
I don't know if someone has the same harddisk in dell 700m.
It's 5400. Great. [See here](http://www.hitachigst.com/portal/site/en/?epi_menuItemID=4a8443e5524e0c5deb4703e3aac4f0a0&epi_menuID=edf693c2139b099056fb11f0aac4f0a0&epi_baseMenuID=3d0cb215112b6934ab937c27aac4f0a0)

---

### Post by utopial on 2007-12-26
does anyone know the shell code to determine the rpm of your HDDs?

---

### Post by Yellow Pasque on 2007-12-26
I'm not so sure that there is such a command in Linux. I know Solaris has iostat -En, but I think the best Linux has is "hdparm -i" or "lshw -C disk"
I'd be happy to be corrected though :P

---

### Post by utopial on 2007-12-27
yeh those commands just show the device models which u can then google to find out the rpm
i was hoping for something to show the rpm in terminal mode tho
thanks anyway

---

### Post by nick_h on 2007-12-27
The easiest way is to use the hdparm command and then google the model number.  I don't think there is a command to get rpm or buffer size.

---

