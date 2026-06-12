---
title: "System hangs after upgrading RAM to 1 GB"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by gradavies on 2005-10-21
Upgraded to Breezy last week. Loaded 686 and K7 kernels. All working well. Upgraded RAM today from 512MB to 1 GB. System hangs either on Nvidia splash screen, login screen or desktop - can't run any applications. 

Ran memtest for 2 hours - no problem. Did apt-get install nvidia-glx and nvidia-glx-config enable to make sure latest driver in use. System still hangs.

Tried all combinations of of the 2 x 512MB memory modules. Ubuntu runs every time using either of the 512MB RAM modules but hangs every time with 1GB. Tried 386, 686 and K7 kernels - all the same. Both modules are DDR400. Speed shown as DDR400 with either 512MB module in use but DDR333 with 1GB. This seems to correspond with the information in the motherboard manual for this configuration. Motherboard is Foxconn Winfast K8S 755A series, SiS chipset, AMD Athlon 64 3000 processor.

Any ideas???

---

### Post by Kyral on 2005-10-21
Maybe try manually setting the RAM speed in the BIOS...

---

### Post by gradavies on 2005-10-21
[QUOTE=Kyral]Maybe try manually setting the RAM speed in the BIOS...[/QUOTE]

That worked! Reset RAM speed back from 800 to 200 Mhz and it's working. Will try intermediate settings as well. Thanks!

---

