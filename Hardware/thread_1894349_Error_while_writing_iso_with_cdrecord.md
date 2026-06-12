---
title: "Error while writing iso with cdrecord"
date: 2011-12-12
forum: Hardware
---

### Post by editheraven on 2011-12-12
```
Dec 12 17:01:04 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6048.992065] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec 12 17:01:04 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6048.992075] sr 0:0:0:0: [sr0] CDB: Write(10): 2a 00 00 00 00 d9 00 00 1f 00
Dec 12 17:01:04 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6048.992094] ata1.00: cmd a0/01:00:00:00:f8/00:00:00:00:00/a0 tag 0 dma 63488 out
Dec 12 17:01:04 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6048.992096]          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec 12 17:01:04 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6048.992100] ata1.00: status: { DRDY }
Dec 12 17:01:09 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6054.040050] ata1: link is slow to respond, please be patient (ready=0)
Dec 12 17:01:14 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6059.028024] ata1: device not ready (errno=-16), forcing hardreset
Dec 12 17:01:14 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6059.028037] ata1: soft resetting link
Dec 12 17:01:14 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6059.200211] ata1.00: configured for UDMA/66
Dec 12 17:01:14 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6059.200497] ata1: EH complete
Dec 12 17:03:20 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6185.184067] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec 12 17:03:20 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6185.184077] sr 0:0:0:0: [sr0] CDB: Synchronize Cache(10): 35 00 00 00 00 00 00 00 00 00
Dec 12 17:03:20 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6185.184101] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec 12 17:03:20 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6185.184104]          res 40/00:02:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec 12 17:03:20 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6185.184109] ata1.00: status: { DRDY }
Dec 12 17:03:25 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6190.224038] ata1: link is slow to respond, please be patient (ready=0)
Dec 12 17:03:30 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6195.216065] ata1: device not ready (errno=-16), forcing hardreset
Dec 12 17:03:30 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6195.216077] ata1: soft resetting link
Dec 12 17:03:30 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6195.388204] ata1.00: configured for UDMA/66
Dec 12 17:03:30 editheraven-T-Systems-PC-P5LD2-VM kernel: [ 6195.388466] ata1: EH complete
```


I *usually* write disks using cdrecord/wodim. When i tryed writing a dvd image to disk my computer froze (everything and the music keeped repeating). Is a dvd error, optical unit error or software?

---

