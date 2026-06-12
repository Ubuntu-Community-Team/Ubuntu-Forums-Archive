---
title: "Screen goes black and switches back on"
date: 2016-03-07
forum: Hardware
---

### Post by puginu on 2016-03-07
Hi, I just installed Ubuntu 14.04.4 LTS on my Acer TimelineX 3820TG. When I open new window in same cases the screen goes black and then after around 5 seconds switches back on. This happens always when I start "System settings..." for example. 

My computer configuration is: 
Acer TimelineX 3820TG
i3-370M,
 ATI Mobility Radeon HD 5470,
 500GB HDD,
 6GB RAM.

I get the following log:

> 
kernel: [  373.317966] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
kernel: [  373.317980] pci 0000:00:1e.0: PCI bridge to [bus 0f]
kernel: [  373.317986] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
kernel: [  373.317994] pci 0000:00:1e.0:   bridge window [mem 0xa0300000-0xa04fffff]
kernel: [  373.318000] pci 0000:00:1e.0:   bridge window [mem 0xa0500000-0xa06fffff 64bit pref]
kernel: [  373.318077] pci_bus 0000:0f: Allocating resources
kernel: [  373.318091] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
kernel: [  373.318095] pci 0000:00:1e.0: PCI bridge to [bus 0f]
kernel: [  373.318099] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
kernel: [  373.318104] pci 0000:00:1e.0:   bridge window [mem 0xa0300000-0xa04fffff]
kernel: [  373.318109] pci 0000:00:1e.0:   bridge window [mem 0xa0500000-0xa06fffff 64bit pref]
kernel: [  373.318700] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
kernel: [  373.318707] pci 0000:00:1e.0: PCI bridge to [bus 0f]
kernel: [  373.318710] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
kernel: [  373.318716] pci 0000:00:1e.0:   bridge window [mem 0xa0300000-0xa04fffff]
kernel: [  373.318721] pci 0000:00:1e.0:   bridge window [mem 0xa0500000-0xa06fffff 64bit pref]
kernel: [  373.318847] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
kernel: [  373.318852] pci 0000:00:1e.0: PCI bridge to [bus 0f]
kernel: [  373.318855] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
kernel: [  373.318861] pci 0000:00:1e.0:   bridge window [mem 0xa0300000-0xa04fffff]
kernel: [  373.318865] pci 0000:00:1e.0:   bridge window [mem 0xa0500000-0xa06fffff 64bit pref]
kernel: [  373.318972] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
kernel: [  373.318977] pci 0000:00:1e.0: PCI bridge to [bus 0f]
kernel: [  373.318980] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
kernel: [  373.318986] pci 0000:00:1e.0:   bridge window [mem 0xa0300000-0xa04fffff]
kernel: [  373.318990] pci 0000:00:1e.0:   bridge window [mem 0xa0500000-0xa06fffff 64bit pref]
kernel: [  373.319013] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
kernel: [  373.319018] pci 0000:00:1e.0: PCI bridge to [bus 0f]
kernel: [  373.319021] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
kernel: [  373.319026] pci 0000:00:1e.0:   bridge window [mem 0xa0300000-0xa04fffff]
kernel: [  373.319031] pci 0000:00:1e.0:   bridge window [mem 0xa0500000-0xa06fffff 64bit pref]
kernel: [  373.319191] pci_bus 0000:03: Allocating resources
kernel: [  373.319232] pci_bus 0000:05: Allocating resources
kernel: [  373.319250] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
kernel: [  373.319255] pci 0000:00:1e.0: PCI bridge to [bus 0f]
kernel: [  373.319259] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
kernel: [  373.319267] pci 0000:00:1e.0:   bridge window [mem 0xa0300000-0xa04fffff]
kernel: [  373.319273] pci 0000:00:1e.0:   bridge window [mem 0xa0500000-0xa06fffff 64bit pref]
kernel: [  373.330948] [drm] PCIE GART of 1024M enabled (table at 0x000000000025E000).
kernel: [  373.331091] radeon 0000:02:00.0: WB enabled
kernel: [  373.331097] radeon 0000:02:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff8801cad5cc00
kernel: [  373.331100] radeon 0000:02:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff8801cad5cc0c
kernel: [  373.331846] radeon 0000:02:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0xffffc90001c1c418
kernel: [  373.348563] [drm] ring test on 0 succeeded in 1 usecs
kernel: [  373.348576] [drm] ring test on 3 succeeded in 2 usecs
kernel: [  373.524752] [drm] ring test on 5 succeeded in 1 usecs
kernel: [  373.524764] [drm] UVD initialized successfully.
kernel: [  373.524821] [drm] ib test on ring 0 succeeded in 0 usecs
kernel: [  373.524872] [drm] ib test on ring 3 succeeded in 0 usecs
kernel: [  373.676021] [drm] ib test on ring 5 succeeded
kernel: [  373.698285] snd_hda_intel 0000:02:00.1: Enabling via VGA-switcheroo
kernel: [  373.802145] snd_hda_intel 0000:02:00.1: CORB reset timeout#2, CORBRP = 65535
kernel: [  379.336338] snd_hda_intel 0000:02:00.1: Disabling via VGA-switcheroo
kernel: [  379.436521] snd_hda_intel 0000:02:00.1: Cannot lock devices!



Any ideas on how to fix that?

---

### Post by svante-jacobsen on 2016-05-11
I have pretty much the exact same problem. Also on an Aspire Timeline. Ubuntu is 15.10 (problem has been going on since atleast 14.x though). New is that after latest update (kernel 4.2.0-30 I think) it will not come back from the black screen.

Did you manage to solve it?

$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8)

---

