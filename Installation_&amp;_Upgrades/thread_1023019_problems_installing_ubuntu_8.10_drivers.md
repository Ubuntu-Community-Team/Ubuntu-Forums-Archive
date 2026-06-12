---
title: "problems installing ubuntu 8.10 drivers"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by stephen1341 on 2008-12-27
ok hello i am a new user of ubuntu (i have dual booted windows vista and ubuntu 8.10) so far i messed up and installed the server kind of ubuntu and (the one with only the command line) i managed to fix that and now im in the normal graphical mode. my problems so far are trying to install the drivers for my computer (a gateway m-6862 2.0 ghz 4gb ram 250gb hard drive 512mb dedicated video mem. i gave ubuntu 30gb of hard drive space) i have installed envy after much sorrow and pulling of hair and guess what it gives me this error /usr/share/envy# python pulse.py ati
rm: cannot remove `*.deb': No such file or directory
ENVY ERROR: Your Operative System does not seem to be supported by Envy.
so thats kinda straight forward. i do not wish to reinstall or install another kind of ubuntu i just need my drivers! can anyone help? (i guess i can install another kind of ubuntu but that would kind of make me want to keep windows.)

---

### Post by perl20 on 2008-12-27
are u trying to install an SSD card?? I can't install mine either.

---

### Post by cariboo on 2008-12-27
We may be able to help if we knew what kind of hardware you are running, in a Applications-->Accessories-->Terminal type:

```
lspci
```

and paste the output in your next post.

Jim

---

### Post by stephen1341 on 2008-12-28
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


thats what i got. if you need more info just ask (i dont know what kind of info to give)

---

