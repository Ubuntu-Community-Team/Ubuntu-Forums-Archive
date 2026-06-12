---
title: "Doesn't detect hard disk in raid format"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by asundaresan on 2006-07-08
Hi,

The hard disk on my Dell 690n is not being completely detected by my kernel. However, it is detected when I use Knoppix boot CD. The upshot is when I use Knoppix, there is a device /dev/sdb which is not created when booting from dapper server.

I suspect that the reason is because of the version of the mptsas driver in the kernel. Dapper ships with "Fusion MPT base driver 3.03.04", while knoppix ships with "Fusion MPT base driver 3.03.08". 

How do I update the driver, or when can I expect the updated driver to ship?

What do I need to do in order to correctly detect and create /dev/sdb? Please let me know if you need any more information.  

I'm using dapper linux-server. The relevant part of the kernel log is as follows 

```

949378.670000] SCSI subsystem initialized
[42949378.670000] Fusion MPT base driver 3.03.04
[42949378.670000] Copyright (c) 1999-2005 LSI Logic Corporation
[42949378.670000] Fusion MPT SAS Host driver 3.03.04
[42949378.670000] ACPI: PCI Interrupt 0000:05:0b.0[A] -> GSI 24 (level, low) -> IRQ 66
[42949378.670000] mptbase: Initiating ioc0 bringup
[42949380.170000] ioc0: SAS1068: Capabilities={Initiator}
[42949384.610000] scsi0 : ioc0: LSISAS1068, FwRev=00063200h, Ports=1, MaxQ=511, IRQ=66
[42949384.700000] ESB2: IDE controller at PCI slot 0000:00:1f.1
[42949384.700000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 169
[42949384.700000] ESB2: chipset revision 9
[42949384.700000] ESB2: not 100% native mode: will probe irqs later
[42949384.700000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[42949384.700000] Probing IDE interface ide0...
[42949385.500000] hda: LITE-ON CD-ROM LTN-4891S, ATAPI CD/DVD-ROM drive

```

However it is detected when I bppt up using a Knoppix CD. The relevant kernel messages are as follows.

```

Fusion MPT SAS Host driver 3.03.08
ACPI: PCI Interrupt 0000:05:0b.0[A] -> GSI 24 (level, low) -> IRQ 30
mptbase: Initiating ioc0 bringup
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
ts: Compaq touchscreen protocol output
ioc0: SAS1068: Capabilities={Initiator}
scsi6 : ioc0: LSISAS1068, FwRev=00063200h, Ports=1, MaxQ=511, IRQ=30
  Vendor: FUJITSU   Model: MAX3147RC         Rev: D206
  Type:   Direct-Access                      ANSI SCSI revision: 03
  Vendor: FUJITSU   Model: MAX3147RC         Rev: D206
  Type:   Direct-Access                      ANSI SCSI revision: 03
  Vendor: FUJITSU   Model: MAX3147RC         Rev: D206
  Type:   Direct-Access                      ANSI SCSI revision: 03
  Vendor: Dell      Model: VIRTUAL DISK      Rev: 1028
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdb: 855465984 512-byte hdwr sectors (437999 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 08
SCSI device sdb: drive cache: write back
SCSI device sdb: 855465984 512-byte hdwr sectors (437999 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 08
SCSI device sdb: drive cache: write back
 sdb: unknown partition table
sd 6:8:0:0: Attached scsi disk sdb
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:1b.0 to 64
fuse init (API version 7.6)
Linux agpgart interface v0.101 (c) Dave Jones

```

Thanks in advance,
Aravind.

---

### Post by brodie101 on 2006-07-13
Hello, i'm new to ubuntu and this message board but I am having the same problem as described above, i'm trying to install ubuntu server 6.06 on a Dell Poweredge 4400 dual PIII 600 Xeon processors with 3 SCSI Hard Drives, after the network detection on the installation the installer goes onto partition section and just hangs and leaves a blue screen there doing noting, no hard drive activity or anything. I have even left it to it own devices for about two hours! Any suggestions? Thanks in advance. Brodie :rolleyes:

---

### Post by asundaresan on 2006-07-13
Hi Brodie,

I'm not sure if your problem is the same as mine. However, if you are having trouble with the partitioning there are a couple of alternatives.

I guess first you must check if all the drives are detected, the drivers loaded, and the devices mapped. For example, if you have 3 SCSI drives (not  attached to a RAID card or something) you should see /dev/sda, /dev/sdb and /dev/sdc. If the partitioning tool doesn't work, you can open a new console (CTRL-ALT-F[2-6], CTRL-ALT-F1 to go back to the installer console).

here you can check if drives are present 

```
ls /dev/sd[a-z]* 
```

you can check if drives are detected using 

```
dmesg | less 
```

to scroll through the kernel output and check if drives are detected. 

If the drives are not detected, then there might some problem with the wiring or something else; I can't help you there.

If they are detected but the drivers are not loaded, it might be due to some esoteric hardware which is not recognised. I think.

If they are detected but not mapped to some /dev/sd? then you probably need new drivers. You can use knoppix to boot the system and see if everything works. This is what I did and knoppix correctly configured the disk. I then compiled a new kernel (2.6.17) which has a newer version of the mptsas driver. dapper ships with 2.6.15. 

Hope this helps,
Aravind.

> **brodie101 said:**
> Hello, i'm new to ubuntu and this message board but I am having the same problem as described above, i'm trying to install ubuntu server 6.06 on a Dell Poweredge 4400 dual PIII 600 Xeon processors with 3 SCSI Hard Drives, after the network detection on the installation the installer goes onto partition section and just hangs and leaves a blue screen there doing noting, no hard drive activity or anything. I have even left it to it own devices for about two hours! Any suggestions? Thanks in advance. Brodie :rolleyes:

---

### Post by brodie101 on 2006-07-14
Thanks for the reply asundaresan, I will try all what you have suggested and let you all know, brodie.

---

### Post by RonanG on 2007-12-09
I have an IBM Blade Server HS21.  I'm trying to install Dapper using Dapper-server-AMD64.iso.  It's the daily dated 7/12/2007.

Unlike the main distribution disk this does recognise the Broadcom NICs but I can't access the hard drives.

I have tried both RAID (Mirrored) and straight disks but neither show up.

I need to get this server running this week so I'd  really appreciate any help.
I've seen posts recommending using Alien to convert the IBM rpms to .deb and installing.  That in not helping and I havenot been ablr to install the Red Hat 64 bit modules in Ubuntu, I get an invalid modyle type error.

Please help!

Ronan

---

