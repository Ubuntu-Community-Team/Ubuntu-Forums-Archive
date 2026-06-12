---
title: "LG CH10LS20 issues"
date: 2010-12-02
forum: Hardware
---

### Post by itsagony on 2010-12-02
hi,

today i bought a LG CH10LS20 blue ray reader/cd/dvd writer combo. after replacing the drive and reboot i exerience the following.

the pc restarts and become unresponsible for quite some time 1-2 mins. then it goes on with booting and i end up in kde as usual. the new drive isnt recognized by the system and also im unable to open the tray. speak the drive doesnt respond to anything. so my first thought was, i got a faulty drive and took it back to the vendor.
he plugged the drive onto a win7 pc and ofcourse the drive works well (he played a blue ray, copied some files from a cd and last burned a dvd while i watched).so i can be sure the drive is 100% functional now.

my system is : ubuntu 10.10 with latest updates amd64
the mainboard is : ASUSTeK Computer INC. M4A78 PRO
the onboard sata controller is: SATA controller: ATI Technologies Inc SB700/SB800 SATA

dmesg output after booting (just the impotant things) looks like :




[    2.650028] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.656444] ata1.00: ATA-7: SAMSUNG HD753LJ, 1AA01113, max UDMA7
[    2.656446] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.662933] ata1.00: configured for UDMA/133
[    2.682628] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
[    2.682729] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.682764] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    2.682803] sd 0:0:0:0: [sda] Write Protect is off
[    2.682805] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.682814] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.682891]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 >
[    2.735231] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.530021] ata3: softreset failed (device not ready)
[   21.560017] ata3: softreset failed (device not ready)
[   32.190015] ata3: link is slow to respond, please be patient (ready=0)
[   56.610014] ata3: softreset failed (device not ready)
[   56.610018] ata3: limiting SATA link speed to 1.5 Gbps
[   61.820016] ata3: softreset failed (device not ready)
[   61.820018] ata3: reset failed, giving up


i also tried the sata interface with ahci and ide with always the same result.

so maybe one fellow ubuntu user can tell me whats going wrong here since allmighty google didnt bring up any useful information to my problem.

thanks in advance for reading/giving a solution :)

---

### Post by Jackal84 on 2010-12-05
> **itsagony said:**
> hi,

today i bought a LG CH10LS20 blue ray reader/cd/dvd writer combo. after replacing the drive and reboot i exerience the following.

the pc restarts and become unresponsible for quite some time 1-2 mins. then it goes on with booting and i end up in kde as usual. the new drive isnt recognized by the system and also im unable to open the tray. speak the drive doesnt respond to anything. so my first thought was, i got a faulty drive and took it back to the vendor.
he plugged the drive onto a win7 pc and ofcourse the drive works well (he played a blue ray, copied some files from a cd and last burned a dvd while i watched).so i can be sure the drive is 100% functional now.

my system is : ubuntu 10.10 with latest updates amd64
the mainboard is : ASUSTeK Computer INC. M4A78 PRO
the onboard sata controller is: SATA controller: ATI Technologies Inc SB700/SB800 SATA

dmesg output after booting (just the impotant things) looks like :




[    2.650028] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.656444] ata1.00: ATA-7: SAMSUNG HD753LJ, 1AA01113, max UDMA7
[    2.656446] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.662933] ata1.00: configured for UDMA/133
[    2.682628] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
[    2.682729] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.682764] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    2.682803] sd 0:0:0:0: [sda] Write Protect is off
[    2.682805] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.682814] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.682891]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 >
[    2.735231] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.530021] ata3: softreset failed (device not ready)
[   21.560017] ata3: softreset failed (device not ready)
[   32.190015] ata3: link is slow to respond, please be patient (ready=0)
[   56.610014] ata3: softreset failed (device not ready)
[   56.610018] ata3: limiting SATA link speed to 1.5 Gbps
[   61.820016] ata3: softreset failed (device not ready)
[   61.820018] ata3: reset failed, giving up


i also tried the sata interface with ahci and ide with always the same result.

so maybe one fellow ubuntu user can tell me whats going wrong here since allmighty google didnt bring up any useful information to my problem.

thanks in advance for reading/giving a solution :)

Hello!

I have exactly the same problem, my configuration:

Ubuntu 10.10 amd64
Asus M4A785G HTPC
LG CH10LS2 Combo

Windows 7 have no problem, it boot and play dvd/bluray correctly. When i try to install ubuntu whit the livecd i recive this error: "unable to find medium containing a live file system".
I use to install ubuntu using a usb key, the system will install but at the first reboot it takes 3/4 minutes to boot, and the dvd  isnt recognized and i can't open the tray... Exactly same problem...

I update bios of the mainboard, i try to search a firmware update for the dvd but there is nothing.

I home someone can help us :-(

Thanks a lot in advance!!!!!! :) :)

---

### Post by itsagony on 2010-12-06
hi,

after searching more i found a solution for this problem \o/.

this problem is only in the amd64 version. after i found this bugreport :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668392](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668392)

i reinstalled ubuntu 10.10 32bit and the problem is totally fixed. the drive works flawless now.

i wont put a solved tag since the problem still exist under 64bit ubuntu

---

### Post by Jackal84 on 2010-12-07
> **itsagony said:**
> hi,

after searching more i found a solution for this problem \o/.

this problem is only in the amd64 version. after i found this bugreport :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668392](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668392)

i reinstalled ubuntu 10.10 32bit and the problem is totally fixed. the drive works flawless now.

i wont put a solved tag since the problem still exist under 64bit ubuntu

Well, you find the bug report.

We have to wait... :(:(

---

