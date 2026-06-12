---
title: "Boot pauses (&gt;100s) to find missing drives?"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by Tux Aubrey on 2006-10-26
Hi all

A problem with a brand new machine booting edgy.  The install went fine but the boot pauses for nearly a minute and half very near the start.

I have attached (the hopefully relevant part of) dmesg that seems to show timeouts when trying to find (empty) SATA slots and a bootchart that shows the big delay.

The machine has an ASROCK eSATAII 939sli32 M'board, an Athlon 3500+ CPU, 1GB RAM and a single SATAII 250GB HDD.  

I have tried moving the SATA plug between the four available sockets but boot always does a timeout trying to find the "missing" drives.

I have also tried turning the RAID function off and profiling the boot, but neither made any difference.

Any help appreciated.

(Other than booting, this machine is lightning fast.  I wish it was mine!)

---

### Post by John.Michael.Kane on 2006-10-27
Looking at the dmesg you posted The only thing that stands out 

```
[17179570.832000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
```

As it stands unless your having system instabilities I would not worry.

---

### Post by Tux Aubrey on 2006-10-28
thanks. I'll leave it as is.

I _was_ hoping to blacklist something. But that's just a deep McCarthyist tendency I have;) .  I'll blacklist Microsoft instead.

---

### Post by hidden80 on 2006-10-29
I'm also experiencing that problem. I have almost the same machine than you... an ASRock 939-eSATA2 with an A64 3200+ and 1 GB of RAM.

The boot is pausing for almost 2 minutes, and then it goes on... it is strange, but in my case the HDD led is always on.

Why are we suffering this problem? Is there any way to stop it from searching missing SATA drives?

---

### Post by John.Michael.Kane on 2006-10-29
You can look under your bios for raid,and make sure it's disabled unless you have need for it.

hidden80 personally I would not worry unless your having major boot stoping issues.

---

### Post by Tux Aubrey on 2007-01-03
Just a quick update to say that this issue "went away" for the owner of the machine with the problem with the latest kernel update (13 December, I think).  Apparently the ASROCK eSATAII 939sli32 M'board SATA detection problem is fixed.  Anybody else have this experience?

---

### Post by aerie on 2007-04-15
I experienced the same problem with SATA detection under Edgy and the HDD led was always on too. My mainboard is an AsRock (AM2-XLIeSATA2). The mainboards listed above and mine all have ULi Chipsets, I wonder if it has something to do. The good thing is that Feisty sorted out my problems:D

---

