---
title: "lowest writin speed for Ubuntu 9.04?"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by vpnm_87 on 2009-05-26
I downloaded the 9.04 iso image and did the md5 checksum...
now when right clickd n chose "write to disc" it shows max possible speed..
but in 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
they said to choose lowest possible speed to use "Live CD"..

 ```
          *-cdrom
                description: CD-R/CD-RW writer
                product: CD-R/RW SW-252S
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: R952
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8093
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Memory at e8100000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 1
	Kernel modules: intelfb
```


wats the optimum speed i should use?(got 1.0x to 61.0x options)
my previous 8.10 cd hangs when i try Live CD option jus before the desktop screen...
this time i want to make sure whether my VGA an CD drive can succeed in Live CD boot option...
help me plz...

---

### Post by Shazaam on 2009-05-26
4x is good. 1x would take too long.

---

### Post by vpnm_87 on 2009-05-26
thaks dude:-)
selected 4.0x:-)
also compiz was not workin in my 8.04..
is that due to my VGA problem?
i downloaded a .rpm and .tar.gz package for my VGA from ASUS website for linux..
i think rpm cant b installed in ubuntu..so yet to work wit that tar package..
does that solve compiz and live CD prob in my PC?any suggestion plz

---

### Post by Shazaam on 2009-05-26
You can install ALMOST anything in Ubuntu...
[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)
or...
[https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html)
For the Compiz problem, did you try the Hardware Drivers manager yet to see if there were any drivers for your video card? (System>Administration>Hardware Drivers)

---

### Post by vpnm_87 on 2009-05-26
no propriatary drivers in System->Administrator->Hardware Drivers...
checked in my Ubuntu 8.10 and 9.04(Live CD)..
in both versions am getting the same...

also another issue with 9.04 Live CD display..plz refer
[http://ubuntuforums.org/showthread.php?t=1170234](http://ubuntuforums.org/showthread.php?t=1170234)

---

### Post by Shazaam on 2009-05-26
I haven't had any experience with Intel cards but you should be able to find quite a few posts here on the board that should help you. Try the "Tutorials and Tips" section or "Multimedia and Video".

---

### Post by vpnm_87 on 2009-05-26
Thanks for the info Shazaam:-)

---

