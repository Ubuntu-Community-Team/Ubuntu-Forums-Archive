---
title: "i have problem with wireless in Satellite A200 - 1CR"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by mauud777 on 2007-10-08
hallo every one

how are you ..?

plz help me i have problem with my wireless atheros :(

hers my lspci

> [QUOTE]root@Ahmad-laptop:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
root@Ahmad-laptop:~# 

[/QUOTE]

the wireless work but every five minutes it goes down i dont now why

i try id to install form the source the same thing

plz help me

---

### Post by mauud777 on 2007-10-08
plz help me i am sorry about my bad english

i have problem with my wireless atheros

its every five minutes close the wireless down plz help me

---

### Post by mauud777 on 2007-10-09
plz help me

---

### Post by cubeist on 2007-10-09
I searched the web for you and found this link for a driver for your atheros card

[http://madwifi.org/]("http://madwifi.org/")

You could read through that page and see if that is what you are looking for...it looks like it should work...

post back with results

---

### Post by mauud777 on 2007-10-09
i download the driver and install it from madwifi website but the same thing every five minute network goes down

plz help me

---

### Post by cubeist on 2007-10-09
is it exactly 5 minutes?  If the driver works the problem probably lies elsewhere... 
how far are you from the base station?
does your wired ethernet work?
do you have access to your wireless router?  If so try assigning yourself a static ip and see if that helps...

---

### Post by mauud777 on 2007-10-09
> **cubeist said:**
> is it exactly 5 minutes?  If the driver works the problem probably lies elsewhere... 
how far are you from the base station?
does your wired ethernet work?
do you have access to your wireless router?  If so try assigning yourself a static ip and see if that helps...

no some times 5 some times 15 but often network goes down in from 10 - 20 minute 

i connect to dsl but i dont how far
no i dont wired my ethernet
yes of course but how i will find my static ip in wireless ..?

---

