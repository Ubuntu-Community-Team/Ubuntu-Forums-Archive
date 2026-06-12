---
title: "Ubuntu freezes (crash in nouveau)"
date: 2015-09-30
forum: Hardware
---

### Post by lacibaci on 2015-09-30
Lately I've been getting freezes/crashes. Looks like the faults are in nouveau driver?

syslog:
Sep 30 12:35:05 heron kernel: [102550.251629] nouveau E[compiz[2317]] multiple instances of buffer 216 on validation list 
Sep 30 12:35:05 heron kernel: [102550.251640] nouveau E[compiz[2317]] validate_init 
Sep 30 12:35:05 heron kernel: [102550.251642] nouveau E[compiz[2317]] validate: -22
Sep 30 12:35:05 heron kernel: [102550.406500] nouveau E[ PFIFO][0000:01:00.0] read fault at 0x0001589000 [PTE] from GR/GPC0/T1_0 on channel 0x003f955000 [compiz[2317]] 
Sep 30 12:35:05 heron kernel: [102550.406504] nouveau E[ PFIFO][0000:01:00.0] PGRAPH engine fault on channel 5, recovering...
Sep 30 12:35:05 heron kernel: [102550.406530] nouveau E[ PGRAPH][0000:01:00.0] TRAP ch 5 [0x003f955000 compiz[2317]] 
Sep 30 12:35:05 heron kernel: [102550.406540] nouveau E[ PGRAPH][0000:01:00.0] GPC0/TPC0/TEX: 0x80000049 
Sep 30 12:35:05 heron kernel: [102550.406544] nouveau E[ PGRAPH][0000:01:00.0] GPC0/TPC1/TEX: 0x80000049

lspci:
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation H77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)

Any ideas?

Thanks,
Lac

---

### Post by dino99 on 2015-10-01
what is that "heron" kernel ? are you still using Hardy ?

---

### Post by matt_symes on 2015-10-01
Hi

I'm not sure what the problem is with the nouveau drivers but have you considered installing the nvidia drivers and seeing if they work better ?

Kind regards

---

### Post by lacibaci on 2015-10-01
> **dino99 said:**
> what is that "heron" kernel ? are you still using Hardy ?

LOL, no. Heron is the machine name :)

Lac

---

### Post by lacibaci on 2015-10-02
> **matt_symes said:**
> Hi

I'm not sure what the problem is with the nouveau drivers but have you considered installing the nvidia drivers and seeing if they work better ?

Kind regards

I switched to NVIDIA binary driver (346.96) and no crashes yet...

---

