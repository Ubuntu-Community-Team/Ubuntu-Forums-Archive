---
title: "MP-BIOS bug: timer not connected to IO-APIC"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by Mr_Starscream on 2007-05-06
Hey guys, I am a newblet with Linux, and I am using Ubuntu Linux 7.04 Feisty Fawn. When I turn on my computer (laptop), I get the following message:

MP-BIOS bug 8245: timer not connected to IO-APIC

this appears to have no effect whatsoever on the system, but it is annoying. When I add the nolapic and / or the noapic options before AND after the -- the system either hangs at the POST screen or the boot (splash) screen. Here are my system specs:

Advent 7105
15.4" Widescreen TF (XGA 1280x800)
1024MB DDR-Ram
ATI Radon Xpress 200M with PCI Express Graphics up to 128MB Shared Memory
PC2001 Compliment AC97 Audio Integrated Stero Speakers
60GB HDD
DVD +/-RW
AMD Mobile Sempron 3000+

---

### Post by Kurdt on 2007-05-07
Hey, I am experiencing that exact problem, but I add the option noapic and my ubuntu livecd boots with no more problem.

I Want to know now if this is severe, or can give me problems in the future...

---

### Post by Mr_Starscream on 2007-05-08
No. It's fine for you mate. :P

---

### Post by startxjeff on 2007-05-10
Solved with my system.

Abit NF-M2 nView with the same "MP BUG yada yada timer not connected to IO-APIC" issue with X2 5600, and 2Gig DDR2 800 low latency ram, and unreliable operation without noapic or apic=off grub fix.

The Abit NF-M2 nView motherboard ships with BIOS version 1.1 released in the fall of 2006, or at least mine did.

Abit USA website only lists this BIOS as available for download.

BUT - if you FTP to [abit's taiwan (tw) site]("ftp://ftp.abit.com.tw/pub/download/bios/nfm2"), find the pub directory, look for nf-m2  (there is also an nf-m2s) you'll find 1.1, 1.2 and 1.3 BIOS version.

I flashed the BIOS to 1.3.

The MP bug is gone, and HPET is now available.  Yay.   

As to the original poster's issue, you might look at the OEM website for a BIOS update as an earlier reply suggested, or call their tech support and ask for help locating same.     

BIOS is not dependent upon OS, but any OS is dependent upon the BIOS.

---

### Post by Mr_Starscream on 2007-05-15
I checked, no BIOS updates availble.

---

### Post by Mr_Starscream on 2007-05-18
I checked, downloaded BIOS updates, flashed and error still appears.

---

