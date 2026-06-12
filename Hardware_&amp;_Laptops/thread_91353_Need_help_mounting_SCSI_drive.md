---
title: "Need help mounting SCSI drive"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by vinoloco on 2005-11-17
Hi all,

I'm working on mounting a SCSI drive to my filesystem and I'm having some problems.

In the Disks Manager window I can see that the system recognizes my drive as /dev/sdc1 and that it is an "Extended 2" filesystem.  I setup the mount point and issue the command:  "sudo mount -t ext2 /dev/sdc1 /mnt/scsi3"   and get the following error:

    mount:  /dev/sdc1 is not a valid block device

Any idea what gives here?  Thanks in advance for the help.

  vino

---

### Post by SickTwist on 2005-11-17
Could you please post the results of these two commands:

ls -l /dev/sd*
dmesg

---

### Post by vinoloco on 2005-11-17
OK, here are the results...   Doesn't look good does it?  Any idea why my SCSI drives are giving all those errors?  Is it that they don't like Ubuntu?

lucinda@garagemeister:/dev$ ls -l /dev/sd*
brw-rw----  1 root disk 8,  0 2005-11-16 11:14 /dev/sda
brw-rw----  1 root disk 8,  1 2005-11-16 11:14 /dev/sda1
brw-rw----  1 root disk 8,  2 2005-11-16 11:14 /dev/sda2
brw-rw----  1 root disk 8, 16 2005-11-16 11:14 /dev/sdb
brw-rw----  1 root disk 8, 17 2005-11-16 11:14 /dev/sdb1
brw-rw----  1 root disk 8, 32 2005-11-16 11:14 /dev/sdc
brw-rw----  1 root disk 8, 33 2005-11-16 11:14 /dev/sdc1
brw-rw----  1 root disk 8, 48 2005-11-16 11:14 /dev/sdd
brw-rw----  1 root disk 8, 49 2005-11-16 11:14 /dev/sdd1
brw-rw----  1 root disk 8, 64 2005-11-16 11:14 /dev/sde
lucinda@garagemeister:/dev$ dmesg
): rejecting I/O to offline device
[4294985.901000] scsi0 (0:0): rejecting I/O to offline device
[4294985.902000] scsi0 (0:0): rejecting I/O to offline device
[4294985.904000] scsi0 (0:0): rejecting I/O to offline device
[4294985.906000] scsi0 (0:0): rejecting I/O to offline device
[4294985.906000] scsi0 (0:0): rejecting I/O to offline device
[4294985.906000] scsi0 (0:0): rejecting I/O to offline device
[4295015.912000]  atp870u: abort Channel = 0
[4295015.912000] working=1 last_cmd=ff  quhdu=13 quendu=17  r 0= a r 1=2c r 2=cf r 3=28 r 4= 0 r 5= 0 r 6= 0 r 7= 0 r 8= 0 r 9= 0 r a= 0 r b=40 r c= 0 r d= 0 r e= 0 r f=80 r10=45 r11=ac r12= 0 r13=67 r14=f0 r15= 3 r16=8b r17=80 r1c=81 r1f=37 in_snd= 0  d00= 9 d02= 0
[4295015.912000]  que cdb=  28   0   0   0   0   0   0   0  40   0  last_lenu= 8000  atp870u: abort Channel = 0
[4295025.912000] working=1 last_cmd=ff  quhdu=13 quendu=18  r 0= a r 1=2c r 2=cf r 3=28 r 4= 0 r 5= 0 r 6= 0 r 7= 0 r 8= 0 r 9= 0 r a= 0 r b=40 r c= 0 r d= 0 r e= 0 r f=80 r10=45 r11=ac r12= 0 r13=67 r14=f0 r15= 3 r16=8b r17=80 r1c=81 r1f=37 in_snd= 0  d00= 9 d02= 0
[4295025.912000]  que cdb=  28   0   0   0   0   0   0   0  40   0  last_lenu= 8000 <6>scsi: Device offlined - not ready after error recovery: host 0 channel 0 id 1 lun 0
[4295025.912000] SCSI error : <0 0 1 0> return code = 0x6000000
[4295025.912000] end_request: I/O error, dev sdb, sector 45319231
[4295025.912000] printk: 316 messages suppressed.
[4295025.912000] Buffer I/O error on device sdb1, logical block 22659584
[4295025.914000] scsi0 (1:0): rejecting I/O to offline device
[4295025.914000] Buffer I/O error on device sdb1, logical block 22659585
[4295025.914000] Buffer I/O error on device sdb1, logical block 22659586
[4295025.914000] Buffer I/O error on device sdb1, logical block 22659587
[4295025.924000] scsi0 (1:0): rejecting I/O to offline device
[4295025.924000] Buffer I/O error on device sdb1, logical block 22659584
[4295025.924000] Buffer I/O error on device sdb1, logical block 22659585
[4295025.924000] Buffer I/O error on device sdb1, logical block 22659586
[4295025.924000] Buffer I/O error on device sdb1, logical block 22659587
[4295025.940000] scsi0 (1:0): rejecting I/O to offline device
[4295025.944000] scsi0 (1:0): rejecting I/O to offline device
[4295025.947000] scsi0 (1:0): rejecting I/O to offline device
[4295025.951000] scsi0 (1:0): rejecting I/O to offline device
[4295025.954000] scsi0 (1:0): rejecting I/O to offline device
[4295025.958000] scsi0 (1:0): rejecting I/O to offline device
[4295025.961000] scsi0 (1:0): rejecting I/O to offline device
[4295025.965000] scsi0 (1:0): rejecting I/O to offline device
[4295025.968000] scsi0 (1:0): rejecting I/O to offline device
[4295025.972000] scsi0 (1:0): rejecting I/O to offline device
[4295025.975000] scsi0 (1:0): rejecting I/O to offline device
[4295025.979000] scsi0 (1:0): rejecting I/O to offline device
[4295025.983000] scsi0 (1:0): rejecting I/O to offline device
[4295025.986000] scsi0 (1:0): rejecting I/O to offline device
[4295025.990000] scsi0 (1:0): rejecting I/O to offline device
[4295025.993000] scsi0 (1:0): rejecting I/O to offline device
[4295025.997000] scsi0 (1:0): rejecting I/O to offline device
[4295026.000000] scsi0 (1:0): rejecting I/O to offline device
[4295026.004000] scsi0 (1:0): rejecting I/O to offline device
[4295026.007000] scsi0 (1:0): rejecting I/O to offline device
[4295026.010000] scsi0 (1:0): rejecting I/O to offline device
[4295026.013000] scsi0 (1:0): rejecting I/O to offline device
[4295026.015000] scsi0 (1:0): rejecting I/O to offline device
[4295026.018000] scsi0 (1:0): rejecting I/O to offline device
[4295026.020000] scsi0 (1:0): rejecting I/O to offline device
[4295026.022000] scsi0 (1:0): rejecting I/O to offline device
[4295026.024000] scsi0 (1:0): rejecting I/O to offline device
[4295026.026000] scsi0 (1:0): rejecting I/O to offline device
[4295026.028000] scsi0 (1:0): rejecting I/O to offline device
[4295026.030000] scsi0 (1:0): rejecting I/O to offline device
[4295026.031000] scsi0 (1:0): rejecting I/O to offline device
[4295026.033000] scsi0 (1:0): rejecting I/O to offline device
[4295026.035000] scsi0 (1:0): rejecting I/O to offline device
[4295026.036000] scsi0 (1:0): rejecting I/O to offline device
[4295026.038000] scsi0 (1:0): rejecting I/O to offline device
[4295026.039000] scsi0 (1:0): rejecting I/O to offline device
[4295026.041000] scsi0 (1:0): rejecting I/O to offline device
[4295026.043000] scsi0 (1:0): rejecting I/O to offline device
[4295026.044000] scsi0 (1:0): rejecting I/O to offline device
[4295026.046000] scsi0 (1:0): rejecting I/O to offline device
[4295026.047000] scsi0 (1:0): rejecting I/O to offline device
[4295026.049000] scsi0 (1:0): rejecting I/O to offline device
[4295026.051000] scsi0 (1:0): rejecting I/O to offline device
[4295026.052000] scsi0 (1:0): rejecting I/O to offline device
[4295026.054000] scsi0 (1:0): rejecting I/O to offline device
[4295026.055000] scsi0 (1:0): rejecting I/O to offline device
[4295026.055000] scsi0 (1:0): rejecting I/O to offline device
[4295026.058000] scsi0 (1:0): rejecting I/O to offline device
[4295026.060000] scsi0 (1:0): rejecting I/O to offline device
[4295026.061000] scsi0 (1:0): rejecting I/O to offline device
[4295026.063000] scsi0 (1:0): rejecting I/O to offline device
[4295026.064000] scsi0 (1:0): rejecting I/O to offline device
[4295026.066000] scsi0 (1:0): rejecting I/O to offline device
[4295026.067000] scsi0 (1:0): rejecting I/O to offline device
[4295026.069000] scsi0 (1:0): rejecting I/O to offline device
[4295026.070000] scsi0 (1:0): rejecting I/O to offline device
[4295026.072000] scsi0 (1:0): rejecting I/O to offline device
[4295026.073000] scsi0 (1:0): rejecting I/O to offline device
[4295026.075000] scsi0 (1:0): rejecting I/O to offline device
[4295026.076000] scsi0 (1:0): rejecting I/O to offline device
[4295026.078000] scsi0 (1:0): rejecting I/O to offline device
[4295026.078000] scsi0 (1:0): rejecting I/O to offline device
[4295026.078000] scsi0 (1:0): rejecting I/O to offline device
[4295056.085000]  atp870u: abort Channel = 0
[4295056.085000] working=1 last_cmd=ff  quhdu=13 quendu=19  r 0= a r 1=2c r 2=cf r 3=28 r 4= 0 r 5= 0 r 6= 0 r 7= 0 r 8= 0 r 9= 0 r a= 0 r b=40 r c= 0 r d= 0 r e= 0 r f=80 r10=45 r11=ac r12= 0 r13=67 r14=f0 r15= 3 r16=8b r17=80 r1c=81 r1f=37 in_snd= 0  d00= 9 d02= 0
[4295056.085000]  que cdb=  28   0   0   0   0   0   0   0  40   0  last_lenu= 8000  atp870u: abort Channel = 0
[4295066.085000] working=1 last_cmd=ff  quhdu=13 quendu=1a  r 0= a r 1=2c r 2=cf r 3=28 r 4= 0 r 5= 0 r 6= 0 r 7= 0 r 8= 0 r 9= 0 r a= 0 r b=40 r c= 0 r d= 0 r e= 0 r f=80 r10=45 r11=ac r12= 0 r13=67 r14=f0 r15= 3 r16=8b r17=80 r1c=81 r1f=37 in_snd= 0  d00= 9 d02= 0
[4295066.085000]  que cdb=  28   0   0   0   0   0   0   0  40   0  last_lenu= 8000 <6>scsi: Device offlined - not ready after error recovery: host 0 channel 0 id 2 lun 0
[4295066.085000] SCSI error : <0 0 2 0> return code = 0x6000000
[4295066.085000] end_request: I/O error, dev sdc, sector 45319231
[4295066.085000] printk: 316 messages suppressed.
[4295066.085000] Buffer I/O error on device sdc1, logical block 22659584
[4295066.087000] scsi0 (2:0): rejecting I/O to offline device
[4295066.087000] Buffer I/O error on device sdc1, logical block 22659585
[4295066.087000] Buffer I/O error on device sdc1, logical block 22659586
[4295066.087000] Buffer I/O error on device sdc1, logical block 22659587
[4295066.097000] scsi0 (2:0): rejecting I/O to offline device
[4295066.097000] Buffer I/O error on device sdc1, logical block 22659584
[4295066.097000] Buffer I/O error on device sdc1, logical block 22659585
[4295066.097000] Buffer I/O error on device sdc1, logical block 22659586
[4295066.097000] Buffer I/O error on device sdc1, logical block 22659587
[4295066.113000] scsi0 (2:0): rejecting I/O to offline device
[4295066.116000] scsi0 (2:0): rejecting I/O to offline device
[4295066.120000] scsi0 (2:0): rejecting I/O to offline device
[4295066.124000] scsi0 (2:0): rejecting I/O to offline device
[4295066.127000] scsi0 (2:0): rejecting I/O to offline device
[4295066.131000] scsi0 (2:0): rejecting I/O to offline device
[4295066.134000] scsi0 (2:0): rejecting I/O to offline device
[4295066.138000] scsi0 (2:0): rejecting I/O to offline device
[4295066.141000] scsi0 (2:0): rejecting I/O to offline device
[4295066.145000] scsi0 (2:0): rejecting I/O to offline device
[4295066.148000] scsi0 (2:0): rejecting I/O to offline device
[4295066.152000] scsi0 (2:0): rejecting I/O to offline device
[4295066.155000] scsi0 (2:0): rejecting I/O to offline device
[4295066.159000] scsi0 (2:0): rejecting I/O to offline device
[4295066.163000] scsi0 (2:0): rejecting I/O to offline device
[4295066.166000] scsi0 (2:0): rejecting I/O to offline device
[4295066.170000] scsi0 (2:0): rejecting I/O to offline device
[4295066.173000] scsi0 (2:0): rejecting I/O to offline device
[4295066.177000] scsi0 (2:0): rejecting I/O to offline device
[4295066.180000] scsi0 (2:0): rejecting I/O to offline device
[4295066.183000] scsi0 (2:0): rejecting I/O to offline device
[4295066.186000] scsi0 (2:0): rejecting I/O to offline device
[4295066.188000] scsi0 (2:0): rejecting I/O to offline device
[4295066.191000] scsi0 (2:0): rejecting I/O to offline device
[4295066.193000] scsi0 (2:0): rejecting I/O to offline device
[4295066.195000] scsi0 (2:0): rejecting I/O to offline device
[4295066.197000] scsi0 (2:0): rejecting I/O to offline device
[4295066.199000] scsi0 (2:0): rejecting I/O to offline device
[4295066.201000] scsi0 (2:0): rejecting I/O to offline device
[4295066.202000] scsi0 (2:0): rejecting I/O to offline device
[4295066.204000] scsi0 (2:0): rejecting I/O to offline device
[4295066.205000] scsi0 (2:0): rejecting I/O to offline device
[4295066.207000] scsi0 (2:0): rejecting I/O to offline device
[4295066.209000] scsi0 (2:0): rejecting I/O to offline device
[4295066.210000] scsi0 (2:0): rejecting I/O to offline device
[4295066.212000] scsi0 (2:0): rejecting I/O to offline device
[4295066.213000] scsi0 (2:0): rejecting I/O to offline device
[4295066.215000] scsi0 (2:0): rejecting I/O to offline device
[4295066.216000] scsi0 (2:0): rejecting I/O to offline device
[4295066.218000] scsi0 (2:0): rejecting I/O to offline device
[4295066.219000] scsi0 (2:0): rejecting I/O to offline device
[4295066.221000] scsi0 (2:0): rejecting I/O to offline device
[4295066.222000] scsi0 (2:0): rejecting I/O to offline device
[4295066.224000] scsi0 (2:0): rejecting I/O to offline device
[4295066.226000] scsi0 (2:0): rejecting I/O to offline device
[4295066.227000] scsi0 (2:0): rejecting I/O to offline device
[4295066.227000] scsi0 (2:0): rejecting I/O to offline device
[4295066.230000] scsi0 (2:0): rejecting I/O to offline device
[4295066.232000] scsi0 (2:0): rejecting I/O to offline device
[4295066.233000] scsi0 (2:0): rejecting I/O to offline device
[4295066.235000] scsi0 (2:0): rejecting I/O to offline device
[4295066.236000] scsi0 (2:0): rejecting I/O to offline device
[4295066.238000] scsi0 (2:0): rejecting I/O to offline device
[4295066.239000] scsi0 (2:0): rejecting I/O to offline device
[4295066.241000] scsi0 (2:0): rejecting I/O to offline device
[4295066.242000] scsi0 (2:0): rejecting I/O to offline device
[4295066.244000] scsi0 (2:0): rejecting I/O to offline device
[4295066.245000] scsi0 (2:0): rejecting I/O to offline device
[4295066.247000] scsi0 (2:0): rejecting I/O to offline device
[4295066.248000] scsi0 (2:0): rejecting I/O to offline device
[4295066.250000] scsi0 (2:0): rejecting I/O to offline device
[4295066.250000] scsi0 (2:0): rejecting I/O to offline device
[4295066.250000] scsi0 (2:0): rejecting I/O to offline device
[4295068.122000] Linux agpgart interface v0.101 (c) Dave Jones
[4295068.136000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[4295068.167000] agpgart: AGP aperture is 128M @ 0xd0000000
[4295068.332000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4295068.341000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4295068.341000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4295068.660000] irda_init()
[4295068.660000] NET: Registered protocol family 23
[4295069.345000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4295069.345000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4295069.345000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4295071.972000] Real Time Clock Driver v1.12
[4295072.051000] input: PC Speaker
[4295072.311000] FDC 0 is a post-1991 82077
[4295073.672000] NET: Registered protocol family 17
[4295076.655000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[4295096.572000] NET: Registered protocol family 10
[4295096.572000] Disabled Privacy Extensions on device c02eb280(lo)
[4295096.572000] IPv6 over IPv4 tunneling driver
[4295098.370000] ACPI: Power Button (FF) [PWRF]
[4295098.370000] ACPI: Power Button (CM) [PWRB]
[4295098.370000] ACPI: Sleep Button (CM) [SLPB]
[4295098.542000] ibm_acpi: ec object not found
[4295107.194000] eth0: no IPv6 routers present
[4295110.689000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4295110.689000] apm: overridden by ACPI.
[4295111.082000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[4295113.122000] Bluetooth: Core ver 2.7
[4295113.122000] NET: Registered protocol family 31
[4295113.122000] Bluetooth: HCI device and connection manager initialized
[4295113.122000] Bluetooth: HCI socket layer initialized
[4295113.145000] Bluetooth: L2CAP ver 2.7
[4295113.145000] Bluetooth: L2CAP socket layer initialized
[4295113.185000] Bluetooth: RFCOMM ver 1.5
[4295113.185000] Bluetooth: RFCOMM socket layer initialized
[4295113.185000] Bluetooth: RFCOMM TTY layer initialized
[4320653.782000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4320684.750000]  atp870u: abort Channel = 0
[4320684.750000] working=1 last_cmd=ff  quhdu=13 quendu=1b  r 0= a r 1=2c r 2=cf r 3=28 r 4= 0 r 5= 0 r 6= 0 r 7= 0 r 8= 0 r 9= 0 r a= 0 r b=40 r c= 0 r d= 0 r e= 0 r f=80 r10=45 r11=ac r12= 0 r13=67 r14=f0 r15= 3 r16=8b r17=80 r1c=81 r1f=37 in_snd= 0  d00= 9 d02= 0
[4320684.750000]  que cdb=  28   0   0   0   0   0   0   0  40   0  last_lenu= 8000  atp870u: abort Channel = 0
[4320694.750000] working=1 last_cmd=ff  quhdu=13 quendu=1c  r 0= a r 1=2c r 2=cf r 3=28 r 4= 0 r 5= 0 r 6= 0 r 7= 0 r 8= 0 r 9= 0 r a= 0 r b=40 r c= 0 r d= 0 r e= 0 r f=80 r10=45 r11=ac r12= 0 r13=67 r14=f0 r15= 3 r16=8b r17=80 r1c=81 r1f=37 in_snd= 0  d00= 9 d02= 0
[4320694.750000]  que cdb=  28   0   0   0   0   0   0   0  40   0  last_lenu= 8000 <6>scsi: Device offlined - not ready after error recovery: host 0 channel 0 id 4 lun 0
[4320694.750000] SCSI error : <0 0 4 0> return code = 0x6000000
[4320694.750000] end_request: I/O error, dev sde, sector 0
[4320694.750000] printk: 316 messages suppressed.
[4320694.750000] Buffer I/O error on device sde, logical block 0
[4320694.750000] scsi0 (4:0): rejecting I/O to offline device
[4320694.750000] Buffer I/O error on device sde, logical block 1
[4320694.750000] Buffer I/O error on device sde, logical block 2
[4320694.750000] Buffer I/O error on device sde, logical block 3
[4320694.750000] Buffer I/O error on device sde, logical block 4
[4320694.750000] Buffer I/O error on device sde, logical block 5
[4320694.750000] Buffer I/O error on device sde, logical block 6
[4320694.750000] Buffer I/O error on device sde, logical block 7
[4320694.755000] scsi0 (4:0): rejecting I/O to offline device
[4320694.755000] Buffer I/O error on device sde, logical block 0
[4337360.515000] cdrom: This disc doesn't have any tracks I recognize!

---

### Post by SickTwist on 2005-11-17
Wow, that is strange. Are you sure that the SCSI drives are jumpered correctly and that they are properly terminated? Perhaps it is a hardware issue.

If the hardware is OK, it could be that the driver Ubuntu is trying to use for the SCSI controller is the wrong driver or is set up incorrectly. Could you post the details of your SCSI controller (make, model, chipset)? If you need help obtaining that information, try using the lspci command to see your PCI devices (sudo is required to probe the hardware and -vv tells lspci to be very verbose):

sudo lspci -vv

---

### Post by vinoloco on 2005-11-18
OK, here it is...

I'm pretty sure the drives are jumpered properly.  I was using them on a Fedora system and they worked fine.  Maybe it is a bad driver.  Thanks for the help...

vino




lucinda@garagemeister:~$ sudo lspci -vv
Password:
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [a0] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64 bit- FW- AGP3- Rate=x1,x2,x4
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<n one>
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot -,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 A GP] (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort+ >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: d8000000-d9ffffff
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot -,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:0b.0 SCSI storage controller: Artop Electronic Corp AEC6712U SCSI (rev 0 8)
        Subsystem: Artop Electronic Corp AEC6712U SCSI
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 254
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at c000 [size=64]
        Region 1: Memory at dd000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 1
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot -,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:0d.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
        Subsystem: Netgear FA310TX
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at c400 [size=256]
        Region 1: Memory at dd001000 (32-bit, non-prefetchable) [size=256]

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
        Subsystem: VIA Technologies, Inc. VT8233A ISA Bridge
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot -,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8 235 PIPC Bus Master IDE
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 10
        Region 4: I/O ports at dc00 [size=16]
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot -,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 23) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin D routed to IRQ 11
        Region 4: I/O ports at e000 [size=32]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot -,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 23) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin D routed to IRQ 11
        Region 4: I/O ports at e400 [size=32]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot -,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 40)
        Subsystem: Avance Logic Inc.: Unknown device 4720
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 11
        Region 0: I/O ports at e800 [size=256]
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot -,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Mod el 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step ping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort - <MAbort- >SERR- <PERR-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at da000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d8000000 (32-bit, prefetchable) [size=32M]
        Capabilities: [60] Power Management version 1
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot -,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [44] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA- ITACoh- GART64- HTrans- 64 bit- FW- AGP3- Rate=x1,x2,x4
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<n one>

lucinda@garagemeister:~$ sudo lspci -vv
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [a0] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP] (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: d8000000-d9ffffff
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:0b.0 SCSI storage controller: Artop Electronic Corp AEC6712U SCSI (rev 08)
        Subsystem: Artop Electronic Corp AEC6712U SCSI
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 254
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at c000 [size=64]
        Region 1: Memory at dd000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 1
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:0d.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
        Subsystem: Netgear FA310TX
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at c400 [size=256]
        Region 1: Memory at dd001000 (32-bit, non-prefetchable) [size=256]

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
        Subsystem: VIA Technologies, Inc. VT8233A ISA Bridge
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 10
        Region 4: I/O ports at dc00 [size=16]
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin D routed to IRQ 11
        Region 4: I/O ports at e000 [size=32]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin D routed to IRQ 11
        Region 4: I/O ports at e400 [size=32]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
        Subsystem: Avance Logic Inc.: Unknown device 4720
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 11
        Region 0: I/O ports at e800 [size=256]
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at da000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d8000000 (32-bit, prefetchable) [size=32M]
        Capabilities: [60] Power Management version 1
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [44] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA- ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

lucinda@garagemeister:~$ sudo mount -a
mount: /dev/sda2 is not a valid block device
mount: /dev/sdb1 is not a valid block device
mount: /dev/sdc1 is not a valid block device

---

### Post by vinoloco on 2005-11-19
OK, new update.  I found that one drive was making a strange "clicking" noise so detached it.  Now the error I get is:

lucinda@garagemeister:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

lucinda@garagemeister:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             18421552   1880380  15605388  11% /
tmpfs                   388272         0    388272   0% /dev/shm
tmpfs                   388272     12588    375684   4% /lib/modules/2.6.12-9-386/volatile
lucinda@garagemeister:~$ dmesg | tail
[4294871.478000] VFS: Can't find an ext2 filesystem on dev sdc1.
[4294877.641000] VFS: Can't find an ext2 filesystem on dev sdb1.
[4294892.112000] VFS: Can't find an ext2 filesystem on dev sdc1.
[4294895.806000] VFS: Can't find an ext2 filesystem on dev sdb1.
[4294912.606000] VFS: Can't find an ext2 filesystem on dev sda2.
[4294912.641000] VFS: Can't find an ext2 filesystem on dev sdb1.
[4294912.681000] VFS: Can't find an ext2 filesystem on dev sdc1.
[4294959.797000] VFS: Can't find an ext2 filesystem on dev sda2.
[4294963.088000] VFS: Can't find an ext2 filesystem on dev sda2.
[4294966.268000] VFS: Can't find an ext2 filesystem on dev sda2.

---

