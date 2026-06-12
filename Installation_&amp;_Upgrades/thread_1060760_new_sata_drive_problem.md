---
title: "new sata drive problem"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by Bigneil on 2009-02-05
my IDE HDD died, i bought a new one. it is a sata drive, i have it all plugged in but i cant get ubuntu to see it at all, nor is my BIOS.



here is a link to a thread i started in another catagory

[http://ubuntuforums.org/showthread.php?t=1047615](http://ubuntuforums.org/showthread.php?t=1047615)

---

### Post by Bigneil on 2009-02-05
any advice would be appreciated

---

### Post by callan79 on 2009-02-05
> **Bigneil said:**
> my IDE HDD died, i bought a new one. it is a sata drive, i have it all plugged in but i cant get ubuntu to see it at all, nor is my BIOS


Hi Bigneil,

This may help you:

```
sudo lshw
```

That should list practically ALL the hardware in your entire system. Then you can search though it for "ATA DISK" or perhaps "Serial ATA Disk" (I don't have any SATA drives, so I don't know the exact wording).

If you can see your disk there great.

If not, you need to verify that your BIOS can see it.

But regarding the BIOS, ubuntuforums.org probably isn't the best place for those questions. Perhaps it would be cool if you could visit the support forums of your motherboard manufacturer. Once you are familiar with the BIOS, and you can verify 100% that your BIOS can see the drive, then we can help you with your Ubuntu questions :)

If, on the other hand, lshw DOES see the drive, please post back with the output of:

```
sudo fdisk -l
```

Cheers
Callan

---

### Post by Bigneil on 2009-02-05
Hi Callan, thaks for replying.

here is the output of sudo fdisk -l

there are two drives listed a 30 GB and an 80 GB, 

but not my new 300GB drive.


i will have a good hust through the output of sudo lshw, and report back.

if you read this the othewr thread i started you will find a link to the instructions for my BIOS.


thanks  bigneil

---

### Post by Bigneil on 2009-02-05
no mention of the drive at all there either.   i have also  checked and double checked that it is plugged in correctly etc..   are sata data cables one way round only?

I Did find an option in BIOS but it was already enabled.


this bit here was the only mention of sata, ~~~v

---

### Post by Bigneil on 2009-02-05
i think you are right, i should go and post on a BIOS forum or something

---

