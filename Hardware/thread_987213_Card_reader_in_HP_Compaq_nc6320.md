---
title: "Card reader in HP Compaq nc6320"
date: 2008-11-19
forum: Hardware
---

### Post by johnwards on 2008-11-19
Hello,

I am trying to get my card reader to mount my XD card from my camera.

I am a bit stumped as all the suggestions I have found about this issue say about including a tifm module, which I have done, and it still isn't mounting the card.

It's weird because dmesg seems to print expected output:
```

[ 3710.820043] tifm_core: SmartMedia/xD card detected in socket 0:0

```

When I pull it out I get:
```

[ 3820.485473] tifm0 : demand removing card from socket 0:0

```

Output of df:
```

john@john-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              19G  3.9G   14G  23% /
tmpfs                1009M     0 1009M   0% /lib/init/rw
varrun               1009M  348K 1008M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
procbususb           1009M  2.9M 1006M   1% /proc/bus/usb
udev                 1009M  2.9M 1006M   1% /dev
tmpfs                1009M  500K 1008M   1% /dev/shm
lrm                  1009M  2.0M 1007M   1% /lib/modules/2.6.27-8-generic/volatile
/dev/sda4              26G  2.9G   22G  12% /backup
/dev/sda3              46G   27G   18G  61% /home

```

Output of lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
02:06.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

Any pointers would be great!

---

### Post by tonsai on 2009-05-08
I've tried this method below on my nc6320 but it doesn't seem to work. I might be donig something wrong:
 
```
 
Cardreader
To get access to the cardreader, modules [FONT=monospace]sdhci, mmc_block and mmc_core[/FONT] must be loaded. Furthermore, a PCI-register must be altered any time, you start your notebook by [FONT=monospace]setpci -s 02:04.2 4c=0x22[/FONT], where 02:04.2 is the PCI address of your cardreader. You will get the PCI address with [FONT=monospace]/sbin/lspci | grep "Mass storage controller"[/FONT]. 
I made it a bit more convenient for me by
[LIST]
[*]concatenating [FONT=monospace]alias cardreader sdhci[/FONT] to my [FONT=monospace]**file**:/etc/modprobe.conf[/FONT],
[*]dropping my Python script [[FONT=monospace]init_cardreader.py[/FONT]]("http://andreas-kleisun.homepage.t-online.de/nx6325-data/init_cardreader.py") into [FONT=monospace]/usr/bin[/FONT]
[*]making it executable with [FONT=monospace][FONT=monospace]chmod 4711 /usr/bin/init_cardreader.py[/FONT][/FONT]
[*]concatenating[FONT=monospace][FONT=monospace] /usr/bin/init_cardreader.py [/FONT][/FONT]to your [FONT=monospace][FONT=monospace]**file**:/etc/rc.local[/FONT][/FONT]
[*]concatenating [FONT=monospace][FONT=monospace]/dev/mmcblk0p1    /media/card    auto    noauto,users 0 0 [/FONT][/FONT]to your[FONT=monospace][FONT=monospace] **file**:/etc/fstab[/FONT][/FONT]
[/LIST]
```

---

