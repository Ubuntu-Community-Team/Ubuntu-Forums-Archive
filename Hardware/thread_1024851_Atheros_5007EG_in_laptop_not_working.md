---
title: "Atheros 5007EG in laptop not working"
date: 2008-12-29
forum: Hardware
---

### Post by demodulator on 2008-12-29
Hello i have a HP presario 791ev with an atheros 5007eg wireless card inside.
I am a total newbie in linux an after some reading i installed ubuntu 8.10 on it which worked succesfully. I updated the OS without a problem an installed some programs too.
All this of course via ethernet because even though i can see it recognises my card and in System->Administration->Hardware drivers it has the official atheros driver activated i can't connect to my wireless modem no matter what i do. I created a new wireless connection in the network connections and even deactivated my WPA2 encryption(so there was no proection at all)  and it still will not connect when i remove the ethernet cable. 

This is the lspci output that i read about in another thread. 
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Thank you!:P

---

### Post by demodulator on 2008-12-29
No one? :(

---

### Post by tr8moore on 2008-12-29
check out this website for a driver.  i just this morning got my atheros wireless card working using their driver.  instructions are right there on the website. it will disable the proprietary drivers which may be causing you some problems.  here's the site:

[http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers]("http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers")

let me know if i can help you out more.... my help may limited as i'm a newbie too but i'll do what i can.  i found this to work with no headaches.

---

### Post by demodulator on 2008-12-29
Thanks for your answer even though i looked at another topic a minute before an i used 
> apt-get install linux-backports-modules-intrepid-generic 

and it installed the generic drivers and now it works perfectly.

---

