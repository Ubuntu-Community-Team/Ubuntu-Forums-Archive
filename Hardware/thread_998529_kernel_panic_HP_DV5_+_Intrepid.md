---
title: "kernel panic: HP DV5 + Intrepid"
date: 2008-11-30
forum: Hardware
---

### Post by Andrade on 2008-11-30
Hello,

I am having the infamous kernel panic problem where the system freezes, the caps-lock light blinks... you know the rest.

At the beginning, when ibex came out, it would freeze (even if I wasn't using any applications) at small intervals: sometimes minutes, sometimes 2-3 hours, sometimes more. Right now the system looked more stable but I still get a freeze once in a while after a couple of hours.


Model: HP DV5-1050ep
OS: Intrepid Ibex

#lspci (copy&paste 2 lines) graphic and wireless card
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I have read tons of pages and haven't found a fix yet. By reading others problems I've seen most people having their system fixed by installing linux-backports-modules-intrepid. I tryed that today. Installed the package (rebooted after), had a few stuff opened (emacs, terminal, ff, totem, sys monitor ...). Went for a walk... when I came back 2-3 hours later unlocked the laptop using my password and it frooze after a few minutes. It seems linux-backports-modules-intrepid doesn't fix my thing so I unistalled. Do not know if I should have kept it anyway.

Sucks when you're working and your computer goes nuts. Any clues of what could be causing me trouble?

Also, should I reinstall linux-backports-modules-intrepid even if it doesn't fix the problem? I wonder if it does any good...


Daniel

---

### Post by Andrade on 2008-11-30
Another freeze.

Powered the computer up, logged in and boom after a minute :(

---

### Post by Lanrat on 2008-11-30
I have a HP dv6500t and I'm having the same problem. A quick look at the logs says its the wireless card. I disabled wireless and used wired. It helped for a while, but it just happened again. still errors with the wireless card even though it is disabled. This did not used to happen.

---

### Post by Zetheroo on 2008-12-01
hey guys ... I have an R61 ThinkPad and am also having the same issue with what I am told are kernel panics. I have my system completely up to date and never had this issue with Hardy or Gutsy. I also have the restricted modules package installed and still get crashes. Nothing works except a hard reset.

Here is my lspci:
```

xxxx@xxxx-xxx:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
```


I have really been trying to find out how to locate the issue, but it is such a ridiculously complex thing to debug that its just not possible for me at this time. We got to find out whats going on here. I have been looking into changing distros since this and other things have started to happen in Hardy and Intrepid.

---

