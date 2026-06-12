---
title: "inspiron 1525 amd64 crash blinking num lock and caps lock lights"
date: 2009-08-30
forum: Hardware
---

### Post by misha680 on 2009-08-30
Hi All:

I have very annoying crashes on Ubuntu 8.04 amd64 with blinking num lock and caps lock lights and computer unresponsive on an Inspiron 1525. Disabling almost everything except Ethernet in BIOS and booting with acpi=off seems to fix.

Here are my kern.log and syslog:
[http://people.hnl.bcm.edu/misha/tmp/kern.log](http://people.hnl.bcm.edu/misha/tmp/kern.log)

[http://people.hnl.bcm.edu/misha/tmp/syslog](http://people.hnl.bcm.edu/misha/tmp/syslog)

Also here are my original specs except I upgraded to 4 GB of Dell memory (Kingston actually):
```

Quantity        Parts #         Part Description
1       C118J   PROCESSOR..., T3200, 2.0, 1MB, CPEN, 2C, M0
1       NK750   Keyboard, 86, United States English, Single, Pointing Barents
1       Y465H   GUIDE..., SETUP, 1525, INSPIRON..., ENGLAND/ENGLISH...
1       DF771   CORD..., Power, 125, 1M, C7, 2P Dual, United States
0       01323   INFORMATION..., NO ITEM
1       G383G   GUIDE..., PRODUCT..., INFORMATION..., WSI, ENGLAND/ENGLISH...
1       H510G   GUIDE..., PRODUCT..., INFORMATION..., SERI,
ENGLAND/ENGLISH..., WORLD WIDE...
1       HN662   Assembly, Adapter, Alternating Current, 65W, Cost Reduced,
Hipro2P
1       WK447   Assembly, Cable, Liquid Crystal Display, 15.4, Spears/Skye
1       PT068   Assembly, Dvd+/-rw, 8X, IDE SPSY, Toshiba Samsung Storage
Technology
1       MK933   Card, Wireless, Minicard, 4965 Most Of World 1
1       D196J   Liquid Crystal Display 15.4WXGA, 0-2BD, True Life, Lg Philips Lcd
1       U990C   ASSEMBLY..., BASE (ASSEMBLY OR GROUP)..., NOTEBOOK...,
MODEM..., A1, 1525
1       WK446   KIT..., Bracket, Liquid Crystal Display, Metal, Spears
1       KW721   Hard Drive, 250GB, S2, 5.4K, 9.5 Seagate Consair
1       F987H   Kit, Software, Dell Media Direct, 3.5, Digital Video Disk
Drive, W1, Inspiron
1       P005H   Kit, Software, Roxio, 10.2-0, DellEdition
1       XR733   Assembly, Bracket, Hard Drive Spears/Skye
1       XT984   Bezel, Liquid Crystal Display Silver, 15.4, No-camera
4       2864D   Screw, M3X3, K SCREW HEAD..., MICROSOFT..., BLACK OXIDE...
1       K257H   KIT..., Software, VHP32SP1A, DigitalVideo Disk Drive, Multiple, 5
1       TX760   Dual In-Line Memory Module 2GB, 800, 256X64, 8K, 200
1       X409G   Battery, Primary, 41WHR, 6C Lithium, SIMPLO
1       R020C   Kit, Software, Works, 9, English
1       PP102   Dual In-Line Memory Module, 1G 800, 128X64, 8, 200, 1GBIT
1       NN198   Heatsink, Central Processor Unit, Notebook, Unified Memory
Architecture, 1525
6       NN783   Bumper, Liquid Crystal Display Rubber, Arctic Silver, SPEARS
1       F706H   Assembly, Cover, Hinge, Plastic 1525
1       RU676   Assembly, Cover, Liquid Crystal Display, UPSELL, Black, SPEAR

```

Thank you so much

Misha

EDIT: Forgot to say, no problems on Vista, so I don't think its hardware related.

---

