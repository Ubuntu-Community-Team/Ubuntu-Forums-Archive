---
title: "Orb mass storage tape drive help...."
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by Trab on 2005-04-24
hello, i just recently found one of my old orb tape drives (its pretty nifty, i have almost 5 gigs more with just 2 tapes XD) but im having trouble getting ubuntu to mount it...
the directions ive found online here [http://www.xtremetech.com.au/ORB/old-orb.html](http://www.xtremetech.com.au/ORB/old-orb.html) say
```

T2110cs:~# modprobe paride
paride: version 1.02 installed

3.) Now the driver the for the 'Chipset' needs to be loaded
T2110cs:~# modprobe on26
paride: on26 registered as protocol 0

4.) Almost last, the driver the for the 'Disk Drive' needs to be loaded
T2110cs:~# modprobe pd
pd: pd version 1.04s, major 45, cluster 64, nice 0
pda: on26 1.02, OnSpec 90c26 at 0x378, mode 1 (8-bit), delay 1
pda: CASTLEWOOD ORB, master, 4307184 blocks [2103M], (4273/16/63), removable media
pda: pda1 < pda5 > 

```

their was ALOT of other stuff on that page, and im sure i should check that first, but the first 2 commands (modprobe paride and modprobe on26) worked fine, the last command gave the error
```

tedd@raptor:~ $ sudo modprobe paride
Password:
tedd@raptor:~ $ sudo modprobe on26
tedd@raptor:~ $ sudo modprobe pd
FATAL: Error inserting pd (/lib/modules/2.6.8.1-5-386/kernel/drivers/block/paride/pd.ko): No such device

```

has anyone gotten this device to work? thanks!
-Trab

---

