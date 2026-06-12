---
title: "Computer / disk access REALLY slow"
date: 2010-11-29
forum: Hardware
---

### Post by ola on 2010-11-29
Hi,

I just installed Ubuntu 10.10 on my computer and it is so slow. 

I think I have managed to narrow it down to being disk access that's slow by running *hdparm*.
```

/dev/sda:
 Timing cached reads:   1774 MB in  2.00 seconds = 886.99 MB/sec
 Timing buffered disk reads:    4 MB in  3.08 seconds =   1.30 MB/sec

```

Also when I'm running dmesg I get the following output. 
```

[   65.824014] ata1: lost interrupt (Status 0x51)
[   65.824034] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6 frozen
[   65.824039] ata1.00: BMDMA stat 0x26, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0
[   65.824043] ata1.00: SError: { UnrecovData Handshk }
[   65.824048] ata1.00: failed command: WRITE DMA
[   65.824056] ata1.00: cmd ca/00:08:48:a1:9a/00:00:00:00:00/e8 tag 0 dma 4096 out
[   65.824057]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x34 (host bus error)
[   65.824061] ata1.00: status: { DRDY }
[   65.824070] ata1.00: hard resetting link
[   66.144020] ata1.01: hard resetting link
[   66.620066] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   66.620079] ata1.01: SATA link down (SStatus 0 SControl 300)
[   66.748063] ata1.00: configured for UDMA/133
[   66.748068] ata1.00: device reported invalid CHS sector 0
[   66.748076] ata1: EH complete
[   98.820017] ata1: lost interrupt (Status 0x51)
[   98.820037] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6 frozen
[   98.820042] ata1.00: BMDMA stat 0x26, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0
[   98.820046] ata1.00: SError: { UnrecovData Handshk }
[   98.820050] ata1.00: failed command: WRITE DMA
[   98.820058] ata1.00: cmd ca/00:08:08:89:1a/00:00:00:00:00/e9 tag 0 dma 4096 out
[   98.820059]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x34 (host bus error)
[   98.820063] ata1.00: status: { DRDY }
[   98.820072] ata1.00: hard resetting link
[   99.140023] ata1.01: hard resetting link
[   99.620084] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   99.620097] ata1.01: SATA link down (SStatus 0 SControl 300)
[   99.752050] ata1.00: configured for UDMA/133
[   99.752056] ata1.00: device reported invalid CHS sector 0
[   99.752067] ata1: EH complete
[  239.808020] ata1: lost interrupt (Status 0x51)
[  239.808041] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6 frozen
[  239.808046] ata1.00: BMDMA stat 0x26, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0, BMDMA stat 0x0
[  239.808051] ata1.00: SError: { UnrecovData Handshk }
[  239.808055] ata1.00: failed command: WRITE DMA
[  239.808063] ata1.00: cmd ca/00:80:a8:08:a0/00:00:00:00:00/e6 tag 0 dma 65536 out
[  239.808065]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x34 (host bus error)
[  239.808068] ata1.00: status: { DRDY }
[  239.808077] ata1.00: hard resetting link
[  240.128017] ata1.01: hard resetting link
[  240.604073] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  240.604085] ata1.01: SATA link down (SStatus 0 SControl 300)
[  240.796062] ata1.00: configured for UDMA/133
[  240.796069] ata1.00: device reported invalid CHS sector 0
[  240.796078] ata1: EH complete

```

I attach the full *dmesg* output.

Any ideas?

---

### Post by ola on 2010-11-30
I think I have solved it. I replaced my SATA cable + removed my wlan dongle. Strange and I'm not sure it works but it has been running for some hours now.

The behavior was really strange. I dual boot the machine with win7 and in windows it worked fine. For some hours. Then suddenly it started acting weird in windows as well. So I figured it must be a hardware failure. I think the problem was the SATA cable being broken or not properly connected.

---

