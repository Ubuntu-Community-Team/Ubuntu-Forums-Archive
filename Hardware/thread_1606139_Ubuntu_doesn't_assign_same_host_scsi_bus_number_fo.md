---
title: "Ubuntu doesn't assign same host scsi bus number following reboot"
date: 2010-10-26
forum: Hardware
---

### Post by domw on 2010-10-26
I have installed a QLogic 2460 FC into my DL185 running Ubuntu 8.04 (kernel 2.6.24.23). Whenever the system reboots, Ubuntu seems to assign a different host number to the HBA.

So on one boot I will get 
# cat /proc/scsi/scsi
Attached devices:
Host: scsi6 Channel: 00 Id: 00 Lun: 00
Vendor: HP Model: Ultrium 4-SCSI Rev: V52Z
Type: Sequential-Access ANSI SCSI revision: 05
Host: scsi6 Channel: 00 Id: 00 Lun: 01
Vendor: ADIC Model: Scalar i500 Rev: 111G
Type: Medium Changer ANSI SCSI revision: 03

and after a reboot I will get
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
Vendor: HP Model: Ultrium 4-SCSI Rev: V52Z
Type: Sequential-Access ANSI SCSI revision: 05
Host: scsi0 Channel: 00 Id: 00 Lun: 01
Vendor: ADIC Model: Scalar i500 Rev: 111G
Type: Medium Changer ANSI SCSI revision: 03

The only thing changing is the "Host: scsi" number which has changed from scsi6 to scsi0. So far I have had "scsi0", "scsi4", "scsi6" and "scsi8".  Unfortunately some application software requires this number to remain the same between reboots.

The problem also exists with an ATTO U320 SCSI card, so it doesn't seem to be confined to one card - but rather the server itself or the kernel.

I have booted using CentOS 5.3 (2.6.18.92-el5), and this seems to always come up with "scsi6".  But I cannot change OS.

Therefore does anybody know a way of guaranteeing that everytime the system boots it will define that HBA as being scsi6, or whatever, preferably without having to recompile a kernel. I have tried some experiments with udev, but I believe that the problem is occuring at a lower level than this.  I have therefore tried booting with acpi=off (and strict,ht,noirq) but no change.

Thanks, Dominic

---

### Post by domw on 2010-10-28
As an update I have also attempted a fresh installation of 10.04 (kernel 2.6.32-21) and whilst it seems marginally more fixed, it has still assigned the qlogic hba to scsi4 as well as the more regular scsi6.

The other "scsi" devices allocated (as at this latest boot) are

dominic@db-ubu1004:~$ dmesg | grep scsi[0-9]
[    1.082373] scsi0 : pata_serverworks
[    1.094416] scsi1 : pata_serverworks
[    1.095638] scsi2 : sata_svw
[    1.097126] scsi3 : sata_svw
[    1.097677] scsi5 : sata_svw
[    1.098453] scsi6 : sata_svw
[    1.470104] scsi4 : qla2xxx
[    3.548302] scsi7 : ioc0: LSI53C1030 C0, FwRev=01032700h, Ports=1, MaxQ=255, IRQ=35
[    5.968362] scsi8 : ioc1: LSI53C1030 C0, FwRev=01032700h, Ports=1, MaxQ=255, IRQ=35
[    6.484473] scsi9 : SCSI emulation for USB Mass Storage devices

Most of the time though pata is assigned scsi0-1, sata scsi2-5, qla scsi6 and ioc scsi7-8.

Any clues would be more than welcome.

Thanks, Dominic

---

