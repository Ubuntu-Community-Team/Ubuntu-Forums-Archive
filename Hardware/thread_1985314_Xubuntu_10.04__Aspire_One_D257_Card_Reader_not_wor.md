---
title: "Xubuntu 10.04 : Aspire One D257 Card Reader not working"
date: 2012-05-23
forum: Hardware
---

### Post by NekoMaster on 2012-05-23
Alright so I pretty much have everything working that I need in Xubuntu on my Acer Aspire One D257 netbook.

Though I have one minor problem that I would like to try and fix if it's possible. The card reader in my netbook doesn't appear to be working with Xubuntu (or other linux distros like Puppy or PepperMint).

Not sure if the following will help (since its the same commands I used while trying to solve my wifi problem)

lspci

```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Intel Corporation Device 08ae
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
```

lsusb

```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0402:7675 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I hope that helps.

Like I said, this is a minor problem but I would like to get my card reader working so I dont have to use up my limited USB ports for a USB reader (I only have 3 ports on this netbook with one occupied for my wireless mouse)

---

### Post by NekoMaster on 2012-05-23
So any takers? I kinda would like to use my card slot so I can use the microsd I use with my cellphone and sync music between my netbook and the phone.

---

### Post by NekoMaster on 2012-05-26
So is there no fix for my card reader problem?

---

### Post by NekoMaster on 2012-05-31
I'm still waiting on a fix for this, I could have used this yesterday when my friend came over with their digital camera and they wanted to download the pictures from the camera using their SD Card

---

