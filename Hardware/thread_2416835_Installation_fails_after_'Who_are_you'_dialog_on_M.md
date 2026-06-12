---
title: "Installation fails after 'Who are you' dialog on Momentus XT hybrid disk"
date: 2019-04-16
forum: Hardware
---

### Post by blokkendoos on 2019-04-16
Dear members,

This problem has a long story on an older laptop with a Seagate Momentus XT 500GB 7200 rpm disk.

What worked was with Windows Vista, 7, 8 and 8.1 and several linux installs beside. The installation of Windows 10 completely ruined the linuxes next to it.
Did not think it would be a lasting problem, so, once in a while I tried installing some sort of ubuntu next to it. To no avail.
A week ago I decided to live without Windows so I could use the disk space for one or more linuxes, as before. Deleted the windows partition and started with the latest Mint Mate 19.1. Checksum was OK. Tried it several times and each time it failed after the Who Are You dialog, when it really starts installing. It just freezes.
Tried older Mints, Xubuntu, latest Raspbian desktop etc. 
What was consistent were the messages in **dmesg**:
```
[ 4947.048125] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 4947.048146] ata1.00: failed command: WRITE DMA EXT
[ 4947.048165] ata1.00: cmd 35/00:08:1b:90:11/00:09:0f:00:00/e0 tag 0 dma 1183744 out
                        res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[ 4947.048176] ata1.00: status: { DRDY }
[ 4947.048195] ata1: hard resetting link
[ 4947.368107] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 4947.394758] ata1.00: configured for UDMA/33
[ 4947.394809] ata1: EH complete

```
I also noted that in the earlier phases the UDMA/** notifications started higher, 100 then 66, followed by some errors to settle on a looping messaging of UDMA/33.

I downloaded the Seagate USBbootSetup-SeaToolsXBootable.220.zip -which needs windows to create the bootable usb disk, so I had to find one with at my neighbours - to check the disk. All tests passed.
I found some remarks about the partition table that should be GPT, checked that and added GPT with gdisk. Tried installing again. Failed again.

Having an identical spare disk of the same type I tried installing Mint Mate 19.1 from another machine on this disk. That also failed. 
```
[    8.770846] scsi 8:0:0:0: Direct-Access     Seagate  ST95005620AS     0000 PQ: 0 ANSI: 2 CCS
[    8.771085] sd 8:0:0:0: Attached scsi generic sg6 type 0
[    8.771321] sd 8:0:0:0: [sdf] 976773168 512-byte logical blocks: (500 GB/466 GiB)
[    8.771757] sd 8:0:0:0: [sdf] Write Protect is off
[    8.771758] sd 8:0:0:0: [sdf] Mode Sense: 28 00 00 00
[    8.773033] sd 8:0:0:0: [sdf] No Caching mode page found
[    8.773036] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[    8.794529]  sdf: sdf1 sdf2
[    8.795966] sd 8:0:0:0: [sdf] Attached SCSI disk
[   38.812347] sd 8:0:0:0: timing out command, waited 30s
[   39.007933] Adding 2047996k swap on /dev/sdf2.  Priority:-2 extents:1 across:2047996k FS
[   69.716339] sd 8:0:0:0: timing out command, waited 30s
```

In a desperate mood I grabbed my dvd player and pushed in an old Mint13 xfce 32b disk. It installed without a moan. Then I burned the Mint and pushed that in. It hang on the same point and with the same grub messages as from the usb boot disk.

I spent the afternoon installing older and younger ubuntu's by dvd. Somehow it seems the older ones like ubuntu 12 get installed easy. But 14 and 16 fail although I tried different DVD's per version. Mint 19.1 failed again also. 
In this case older is better it seems. But I still would like to install a more modern one on this machine.

I have no clue what is going on or why.
Please help me.

---

