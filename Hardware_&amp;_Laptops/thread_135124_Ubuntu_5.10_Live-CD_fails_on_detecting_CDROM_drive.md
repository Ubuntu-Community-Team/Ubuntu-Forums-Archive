---
title: "Ubuntu 5.10 Live-CD fails on detecting CDROM drive"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by jives on 2006-02-23
Hi!

I'm trying to get Ubtuntu 5.10 working from a live-cd on a [Maxdata PRO 6000 I Select](http://partnernet.maxdata.co.uk/download/midrange_index.htm) laptop wit a Philips SDVD8441 DL DVD+-RW drive. Unfortunately Ubuntu seems to have problems with finding and mouting the cdrom. I have tried to boot with
```

noapic acpi=off
hdb=ide-scsi

```
but had no success. Does anybody have an idea what else I could do?

tia

---

### Post by Kiran on 2006-02-27
I couldn't get a live CD of Ubuntu to work on my Toshiba Satellite, but I tried Kubuntu and it worked, so I did the install.  I've been using it for a couple of weeks with fairly good success.

---

### Post by spandon on 2006-02-27
Hi,
I had the same problem, but with an Acer Aspire 1654.
The Live Cd of Kubuntu worked but not ubuntu.
I eventually tried the following:
Boot: live noapic,hw-detect/start_pcmcia=false,vga=771
This worked perfectly.
Don

---

