---
title: "Suspend issues (Asus UL30)"
date: 2010-08-15
forum: Hardware
---

### Post by rdjse on 2010-08-15
Hi!

My Asus UL30JT running Ubuntu 10.04 (kernel 2.6.32-24) have problems suspending/hibernating. When I press the button for hibernation/suspend the screen turns black but is not turned off, there is some HDD activity and then the computer freeze and I cant wake it up. 

I dont have a clue where to begin troubleshooting this, I've looked at the log file pm-suspend.log but it didn't really make sense.

Here's the log file in question:
[http://rdj.se/pm-suspend.log](http://rdj.se/pm-suspend.log)

Heres the lspci output:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev ff)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a70 (rev ff)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

If you need more info/logfiles or have any ideas please post. Thanks!

---

### Post by rdjse on 2010-09-12
Hello again!

It's been a while since I posted to this thread but I just have to
tell you all that I got Suspend working on my Asus UL30JT now. I came
across this thread on the Ubuntuforums:
[http://www.ge.ubuntuforums.org/showthread.php?t=1569380](http://www.ge.ubuntuforums.org/showthread.php?t=1569380)
I then followed the steps described under "Fix Suspend". After
creating that script suspend works as it should! I hope that will
solve your problems too!

//rdj

---

