---
title: "HP dv2000 notebook problems"
date: 2008-06-30
forum: Hardware
---

### Post by irvy on 2008-06-30
I am having a lot of issues with my laptop. It came with Vista Home Premium. I have recently tried loading Ubuntu 8.04 and UbuntuStudio 8.04. It runs for a few minutes and then freezes. It does not happen with any particular program but at random. I will give you some more information from by laptop as obtained from Belarc Advisor:

Hewlett-Packard HP Pavilion dv2000 (RM669AV#ABA) F.39
System Serial Number: 2CE71609BY
Enclosure Type: Notebook
2.00 gigahertz Intel Core 2 Duo
64 kilobyte primary memory cache
4096 kilobyte secondary memory cache

MATSHITA DVD-RAM UJ-850S ATA Device [CD-ROM drive]

TOSHIBA MK1637GSX [Hard drive] (160.04 GB) -- drive 0, s/n 475IF2IQS, rev DL021A, SMART Status: Healthy
Board: Wistron 30B3 61.65
Bus Clock: 667 megahertz
BIOS: Hewlett-Packard F.39 08/27/2007
IDE Channel [Controller] (3x)
Intel(R) 82801G (ICH7 Family) Ultra ATA Storage Controllers - 27DF
Ricoh Memory Stick Controller
Ricoh MMC Host Controller
Ricoh xD-Picture Card Controller
Standard AHCI 1.0 Serial ATA Controller
NVIDIA GeForce Go 7200 [Display adapter]
Generic PnP Monitor (14.0"vis)
Microsoft iSCSI Initiator
Intel(R) PRO/Wireless 3945ABG Network Connection

Please help as I have had nothing but grief with this laptop while using vista.

---

### Post by ukripper on 2008-06-30
> **irvy said:**
> I am having a lot of issues with my laptop. It came with Vista Home Premium. I have recently tried loading Ubuntu 8.04 and UbuntuStudio 8.04. It runs for a few minutes and then freezes. It does not happen with any particular program but at random. I will give you some more information from by laptop as obtained from Belarc Advisor:

Hewlett-Packard HP Pavilion dv2000 (RM669AV#ABA) F.39
System Serial Number: 2CE71609BY
Enclosure Type: Notebook
2.00 gigahertz Intel Core 2 Duo
64 kilobyte primary memory cache
4096 kilobyte secondary memory cache

MATSHITA DVD-RAM UJ-850S ATA Device [CD-ROM drive]

TOSHIBA MK1637GSX [Hard drive] (160.04 GB) -- drive 0, s/n 475IF2IQS, rev DL021A, SMART Status: Healthy
Board: Wistron 30B3 61.65
Bus Clock: 667 megahertz
BIOS: Hewlett-Packard F.39 08/27/2007
IDE Channel [Controller] (3x)
Intel(R) 82801G (ICH7 Family) Ultra ATA Storage Controllers - 27DF
Ricoh Memory Stick Controller
Ricoh MMC Host Controller
Ricoh xD-Picture Card Controller
Standard AHCI 1.0 Serial ATA Controller
NVIDIA GeForce Go 7200 [Display adapter]
Generic PnP Monitor (14.0"vis)
Microsoft iSCSI Initiator
Intel(R) PRO/Wireless 3945ABG Network Connection

Please help as I have had nothing but grief with this laptop while using vista.

Can you post output of the following:

```
uname -a
```

```
lspci
```

```
dmesg | tail
```

and in gedit /var/log/messages look for WW or EE and if you find anything related to EE are errors and WW are warnings post here.

---

### Post by nomadsoul21 on 2009-06-02
Hey I have an HP Pavillion dv2000 and I installed Ubuntu a couple of months ago (the experience has been really nice, I like Ubuntu a lot). 

I have been experiencing the same freezing phenomenon since a couple of weeks. But I noticed it only happens when I connect the AC current cable when i'm at my office... and in my office there is a problem with the electric current, it has hi and low peaks, randomly during the day. 

I suspect that the freezing has something to do with the electricity. You can check that by using your laptop with the battery power alone. If you keep getting freezes, then I am very wrong and we both will have to look for a good solution!!

Best of luck to you all.

---

