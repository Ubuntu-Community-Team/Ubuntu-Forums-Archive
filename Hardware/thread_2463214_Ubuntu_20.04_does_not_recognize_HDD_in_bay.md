---
title: "Ubuntu 20.04 does not recognize HDD in bay"
date: 2021-06-06
forum: Hardware
---

### Post by mkasemer on 2021-06-06
I have a Dell 7820 workstation which contains an AVAGO MegaRAID SAS 9460-16i pcie card which controls 4 hard drive bays at the front of the workstation. TLDR: Ubuntu does not recognize any drives placed in the top two bays, though the UEFI does recognize when drives are in the bays.

Previously this system worked as intended: I could put any drives in the top bays and Ubuntu would recognize them as additional volumes. The bottom two bays work as intended. At some point, Ubuntu began to fail to recognize any drives which were placed in the top two bays. However, the drive is still recognized when I run Dell diagnostics at startup, it can see that it is present (see slot 1-0-2 in the attached image of the diagnostic scan).

When I run lsblk:

```

NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0         7:0    0   9.1M  1 loop /snap/canonical-livepatch/99
loop1         7:1    0  55.4M  1 loop /snap/core18/2066
loop2         7:2    0    99M  1 loop /snap/core/11081
loop3         7:3    0  32.1M  1 loop /snap/snapd/11841
loop4         7:4    0  99.2M  1 loop /snap/core/11167
loop5         7:5    0  55.5M  1 loop /snap/core18/1988
loop6         7:6    0    51M  1 loop /snap/snap-store/518
oop7         7:7    0  65.1M  1 loop /snap/gtk-common-themes/1515
loop8         7:8    0   219M  1 loop /snap/gnome-3-34-1804/66
loop9         7:9    0  64.8M  1 loop /snap/gtk-common-themes/1514
loop10        7:10   0  32.1M  1 loop /snap/snapd/12057
sda           8:0    0   931G  0 disk 
sdb           8:16   0   931G  0 disk 
&#9492;&#9472;sdb1        8:17   0   931G  0 part 
nvme0n1     259:0    0 238.5G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2 259:2    0   238G  0 part /

```

It recognizes the two 1TB drives (sda, sdb, corresponding to slots 1-0-0 and 1-0-1 in the diagnostic scan) and the main 256GB SSD where Ubuntu is installed (nvme0n1, corresponding to 2-0-1 in the diagnostic scan), but not the 2TB drive (1-0-2).

I have an identical workstation, and Ubuntu recognizes drives put into the top two bays. When I swap drives into the second, functioning workstation, it can recognize them - including the drive in the diagnostic scan above (read: it is seemingly not an issue with the drive itself). When I take drives from the functioning workstation and put them into the top 2 bays of the non-functioning workstation, it does not recognize them. I have not done anything (knowingly) to change the configuration. I have not set up RAID, though I'm curious if somehow this may be to blame?

I do not know what other information to post immediately, but am happy to provide any information to resolve this.

---

### Post by CharlesA on 2021-06-06
Remove the top two drives and then insert one of them and run this command:

```
sudo dmesg
```

And see if there are any indication that the drive is trying to spin up or not.

It should look similar to this:

```

[2030268.257542] scsi 5:0:0:0: Direct-Access     ATA      WDC WD80EMAZ-00W 0A83 PQ: 0 ANSI: 5
[2030268.258185] sd 5:0:0:0: [sdq] 15628053168 512-byte logical blocks: (8.00 TB/7.28 TiB)
[2030268.258189] sd 5:0:0:0: [sdq] 4096-byte physical blocks
[2030268.258203] sd 5:0:0:0: [sdq] Write Protect is off
[2030268.258205] sd 5:0:0:0: [sdq] Mode Sense: 00 3a 00 00
[2030268.258232] sd 5:0:0:0: [sdq] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[2030268.259959] sd 5:0:0:0: Attached scsi generic sg18 type 0
[2030268.304539] sd 5:0:0:0: [sdq] Attached SCSI disk

```

---

### Post by mkasemer on 2021-06-06
Hi @CharlesA: I will do that when I can physically access the workstation on Tuesday. I can ssh in now, however, and run the command (bottom 2 bays and 1 top bay occupied, same configuration as described above). Would you like to see the *full* output?

**EDIT:**I'll just post the entire output here preemptively - I'm not sure what is or isn't important: [https://paste.ubuntu.com/p/rwyWScj7Jw/](https://paste.ubuntu.com/p/rwyWScj7Jw/)

---

### Post by CharlesA on 2021-06-06
Well, I only see two drives in the dmesg output.

I also see this, which is a bit concerning.

```
[ 3441.507732][ 3441.507732] megaraid_sas 0000:18:00.0: megasas_disable_intr_fusion is called outbound_intr_mask:0xffffffff
**[ 3441.507827] megaraid_sas 0000:18:00.0: FW in FAULT state Fault code:0xfff0000 subcode:0xff00 func:megasas_wait_for_outstanding_fusion**
[ 3441.507840] megaraid_sas 0000:18:00.0: resetting fusion adapter scsi0.
[ 3441.508622] megaraid_sas 0000:18:00.0: Outstanding fastpath IOs: 0
[ 3552.623247] megaraid_sas 0000:18:00.0: Diag reset adapter never cleared megasas_adp_reset_fusion 3977
[ 3663.982765] megaraid_sas 0000:18:00.0: Diag reset adapter never cleared megasas_adp_reset_fusion 3977
[ 3775.342278] megaraid_sas 0000:18:00.0: Diag reset adapter never cleared megasas_adp_reset_fusion 3977
**[ 3775.342284] megaraid_sas 0000:18:00.0: Reset failed, killing adapter scsi0.**
[ 3776.354351] megaraid_sas 0000:18:00.0: Failed from megasas_fault_detect_work 1933, do not re-arm timer
[ 4833.218938] sd 0:2:1:0: [sdb] tag#964 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK cmd_age=0s
[ 4833.218944] sd 0:2:1:0: [sdb] tag#964 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[ 4833.218949] blk_update_request: I/O error, dev sdb, sector 0 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 0
[ 4833.219000] sd 0:2:1:0: [sdb] tag#965 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK cmd_age=0s
[ 4833.219003] sd 0:2:1:0: [sdb] tag#965 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[ 4833.219006] blk_update_request: I/O error, dev sdb, sector 0 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 4833.219011] Buffer I/O error on dev sdb, logical block 0, async page read
[ 4833.219035] sd 0:2:1:0: [sdb] tag#966 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK cmd_age=0s
[ 4833.219038] sd 0:2:1:0: [sdb] tag#966 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[ 4833.219041] blk_update_request: I/O error, dev sdb, sector 0 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 4833.219044] Buffer I/O error on dev sdb, logical block 0, async page read
[ 4833.219424] sd 0:2:0:0: [sda] tag#967 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK cmd_age=0s
[ 4833.219427] sd 0:2:0:0: [sda] tag#967 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[ 4833.219430] blk_update_request: I/O error, dev sda, sector 0 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 0
[ 4833.219458] sd 0:2:0:0: [sda] tag#968 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK cmd_age=0s
[ 4833.219461] sd 0:2:0:0: [sda] tag#968 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[ 4833.219463] blk_update_request: I/O error, dev sda, sector 0 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 4833.219466] Buffer I/O error on dev sda, logical block 0, async page read
[ 4833.219486] sd 0:2:0:0: [sda] tag#969 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK cmd_age=0s
[ 4833.219489] sd 0:2:0:0: [sda] tag#969 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[ 4833.219491] blk_update_request: I/O error, dev sda, sector 0 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 4833.219493] Buffer I/O error on dev sda, logical block 0, async page read
```

Based on what I've seen with my older LSI 9260-8i, this type of error occurred and caused the array to disappear on my server.

Replacing the RAID card resolved the issue, but it recurred after a couple of years due what I assume was  insufficient cooling. I've moved to a dumb HBA and software RAID and I haven't had any more of those issues.

---

### Post by mkasemer on 2021-06-06
@CharlesA: A bad pcie card was my first thought. Dell sent me a new one, and the issue persists (they also replaced the motherboard, which seemed a bit extreme...). They are going to send a new bay assembly, though I'm skeptical this will resolve the issue.

It is confusing that the Dell diagnostic scan can recognize that there are drives in those bays, but Ubuntu cannot. While not conclusive, it does indicate that the hardware is functioning correctly (to some degree). That Ubuntu fails to recognize it *at all* is strange, and the errors happening at ~3441 are well after boot (**EDIT: **this is not to say that I think that the errors are inconsequential, I just think something is happening earlier).

I'll remove the bottom two drives on Tuesday to see if that leads to a significantly different result, and we will wait to see if replacement bays yields a change.

---

### Post by CharlesA on 2021-06-06
> **mkasemer said:**
> @CharlesA: A bad pcie card was my first thought. Dell sent me a new one, and the issue persists (they also replaced the motherboard, which seemed a bit extreme...). They are going to send a new bay assembly, though I'm skeptical this will resolve the issue.

It is confusing that the Dell diagnostic scan can recognize that there are drives in those bays, but Ubuntu cannot. While not conclusive, it does indicate that the hardware is functioning correctly (to some degree). That Ubuntu fails to recognize it *at all* is strange, and the errors happening at ~3441 are well after boot (**EDIT: **this is not to say that I think that the errors are inconsequential, I just think something is happening earlier).

I'll remove the bottom two drives on Tuesday to see if that leads to a significantly different result, and we will wait to see if replacement bays yields a change.

Have you tried booting a livecd/usb and seeing if all the drives are detected? That might rule out a software issue with that install, or confirm it's an issue with the hardware itself.

---

### Post by mkasemer on 2021-06-06
Well, I've reformatted the main drive, so good point...

**EDIT: **They sent the wrong parts, so we will see again next week if new cables change anything.

---

