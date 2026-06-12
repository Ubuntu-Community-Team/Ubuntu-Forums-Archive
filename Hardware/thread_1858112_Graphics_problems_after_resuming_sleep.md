---
title: "Graphics problems after resuming sleep"
date: 2011-10-11
forum: Hardware
---

### Post by ddvlad on 2011-10-11
On my Thinkpad X220, I notice that after resuming sleep some videos (most notably YouTube) are choppy.  Sound has no problems, but videos freeze for two to five seconds after starting, only resuming for periods of less than a second every other two to five seconds.

The same problem exists if I run a VMware virtual machine (also after resuming from sleep): the virtual machine seems frozen until I release the keyboard and mouse by pressing control-alt, at which point the VM screen is updated.

Some embedded videos (ai-class.org, and others) exibit no such problems, nor does opening a local video.  dmesg doesn't show anything relevant.

Here is some hopefully relevant information:

```

# uname -r
Linux doppelganger 2.6.38-11-generic-pae #50-Ubuntu SMP Mon Sep 12 22:21:04 UTC 2011 i686 i686 i386 GNU/Linux
# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 6 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04)
0e:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

```

Thanks in advance,
Vlad

---

