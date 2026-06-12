---
title: "Dual Monitor Support"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by raghav_p on 2005-07-04
Hi,

I have a Gateway M405 Laptop w/Centrino etc..

I have everything configured except Dual Monitors. I frequently need to make presentations and would like my laptop to be able to connect to a projector and display the screen I am viewing. 

After consulting Google, I tried this:

$ sudo lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Re gisters (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process  Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graph ics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Dev ice (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Contro ller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Contr oller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem  Controller (rev 03)
0000:02:02.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controlle r
0000:02:04.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:02:08.0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 83)

Looking at the X conf file, I saw that the device at 0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graph ics Device (rev 02) is the internal LCD monitor with the laptop. Logically then, :00:02.1 is the external slot I have for a second monitor/projector.

Does anyone know how I should configure this? Thx for ur help!

---

### Post by magicfab on 2006-01-04
Interesting, I have not been able to do this on my Averatec Laptop either.

I even tried to lower resolution to 800x600 to no avail. You'd think this would be pretty standard. I am guessing you would have to defin a new monitor in the /etc/X/xorg.conf config file, then somehow make it activate using the FN+F5 key combination (in my case).

I've never had any problems hooking up external LCD monitors but projectors seem to be harder for some reason.

---

