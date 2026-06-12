---
title: "Screen resolution in 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Howie Williams on 2009-11-02
Just upgraded but now cant get screen res the way I want. System > Pref > Display only 2 choices 800 x 600 (4:3) and 640 x 480 (4:3). Also Syst > Admin > Hardware Drivers list is empty. Help please!!!

---

### Post by soare.florian on 2009-11-02
> **Howie Williams said:**
> Just upgraded but now cant get screen res the way I want. System > Pref > Display only 2 choices 800 x 600 (4:3) and 640 x 480 (4:3). Also Syst > Admin > Hardware Drivers list is empty. Help please!!!

Please give us some technical details about your graphics ... 
Type of videocard is : ....
You can find it with " lspci " command on the terminal....

---

### Post by Howie Williams on 2009-11-02
> **soare.florian said:**
> Please give us some technical details about your graphics ... 
Type of videocard is : ....
You can find it with " lspci " command on the terminal....

This is what I got

howie@williams-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by stvnvndnbrgh on 2009-11-02
i have the same problem

---

### Post by dylan_newb on 2009-11-03
take a look here
[http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283](http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283)

---

