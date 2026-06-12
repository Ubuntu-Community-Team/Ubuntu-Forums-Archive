---
title: "long system start up. hdd trouble? Dmesg"
date: 2014-02-28
forum: Hardware
---

### Post by tkraemer2 on 2014-02-28
Hi there,

can someone tell me something about this messages please. System takes a long time to start up and shows
them. It is possible that the drive sata slot was changed few time ago. I'm not shure if the trouble starts at this
point. Thank you very much!!

[ 5680.001608] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 5680.001623] ata3.00: failed command: IDENTIFY PACKET DEVICE
[ 5680.001638] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[ 5680.001638]          res 40/00:02:00:00:02/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 5680.001646] ata3.00: status: { DRDY }
[ 5680.001656] ata3: hard resetting link
[ 5680.492671] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 5680.495349] ata3.00: configured for UDMA/100
[ 5680.512672] ata3: EH complete
[ 5714.945815] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 5714.945829] ata3.00: failed command: IDENTIFY PACKET DEVICE
[ 5714.945844] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[ 5714.945844]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 5714.945852] ata3.00: status: { DRDY }
[ 5714.945862] ata3: hard resetting link
[ 5715.436910] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 5715.439723] ata3.00: configured for UDMA/100
[ 5715.456927] ata3: EH complete
[ 5745.865399] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 5745.865414] ata3.00: failed command: IDENTIFY PACKET DEVICE
[ 5745.865429] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[ 5745.865429]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 5745.865437] ata3.00: status: { DRDY }
[ 5745.865447] ata3: hard resetting link
[ 5746.360629] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 5746.363203] ata3.00: configured for UDMA/100
[ 5746.380455] ata3: EH complete
[ 5753.850837] ata3: limiting SATA link speed to 1.5 Gbps
[ 5753.850851] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 5753.850861] ata3.00: failed command: IDENTIFY PACKET DEVICE
[ 5753.850875] ata3.00: cmd a1/00:00:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[ 5753.850875]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 5753.850883] ata3.00: status: { DRDY }
[ 5753.850893] ata3: hard resetting link
[ 5754.341939] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 5754.345034] ata3.00: configured for UDMA/100
[ 5754.361909] ata3: EH complete
[ 5784.834300] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 5784.834314] ata3.00: failed command: IDENTIFY PACKET DEVICE
[ 5784.834330] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[ 5784.834330]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 5784.834338] ata3.00: status: { DRDY }
[ 5784.834348] ata3: hard resetting link
[ 5785.325420] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 5785.328124] ata3.00: configured for UDMA/100
[ 5785.345408] ata3: EH complete
[ 5798.304192] sr0: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[ 5798.304199] sr: Sense Key : Hardware Error [current] 
[ 5798.304201] sr: Add. Sense: Media load or eject failed
[ 5828.722267] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 5828.722282] ata3.00: failed command: IDENTIFY PACKET DEVICE
[ 5828.722297] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[ 5828.722297]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 5828.722306] ata3.00: status: { DRDY }
[ 5828.722315] ata3: hard resetting link
[ 5829.213334] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 5829.216747] ata3.00: configured for UDMA/100
[ 5829.233363] ata3: EH complete

###############################################################

Yeah! Thank this fellow  very much :-). But i dont understand why this never happend before.
suddenly it was there.

[http://paulphilippov.com/articles/how-to-fix-slow-boot-with-ata-errors](http://paulphilippov.com/articles/how-to-fix-slow-boot-with-ata-errors)

$ sudo sed -i '/ATAPI/,+1s/^/#/' /lib/udev/rules.d/60-persistent-storage.rules
$ sudo update-initramfs -u
$ sudo reboot now
###############################################################

---

