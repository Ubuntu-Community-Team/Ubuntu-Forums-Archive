---
title: "GA-X58A-UD3R motherboard : ata SError?"
date: 2010-12-08
forum: Hardware
---

### Post by Rubel on 2010-12-08
I've been working with a GigaByte motherboard, trying to install Ubuntu Server 64-bit as a VM host.

The machine includes an i7 processor, six 4G sticks of RAM (filling all slots, although I've also tried it with some removed), and a Western Digital SATA drive plugged into the onboard port. (Actually, there are three SATA/RAID controllers: the South Bridge Intel ICH10R, a JMicron JMB362/Gigabyte, and a Marvell 9128. I've tried all of them.)

I've gotten strange data errors under both ESXi 4.1.0 and Ubuntu Server 10.04/10.10 64-bit. I would see a lot of checksum errors when copying files around (for instance, copying over VM disk images or even installing Ubuntu from a USB flash drive.) Sometimes files on an active drive will come back with several different md5sums when I run them in quick succession. At first, the problems were only occasional, but now I get them every time I try to install, and have gotten filesystem corruption and kernel panics. 

So the obvious possibility is a bad hard drive or a bad SATA cable, right? I tried swapping out the SATA cable, but that didn't change anything. I tried moving the hard drive to another machine, and it works flawlessly there.

Next, I thought I'd test the RAM. I have ran Memtest86+ one and half full passes with no errors. I found that it was auto-detecting at lower timings than the RAM is rated for, so I force-set it in the BIOS. I removed all but two sticks of RAM, trying to get it stable and adding back RAM slowly.

I installed Ubuntu Server on the hard drive while on the other, working machine. I moved the drive back to the troubled machine (reseting the network entries since it put the new machine's NIC as eth1). I set it running mprime to test the CPU and bonnie++ to work over the drives. With only 8 Megs RAM, I can get 20-30 minutes of stability while under this load, then seeing errors like this: unable to handle kernel paging request at xxxxxx

I've also seen ata errors on the console (and in /var/log/syslog). They look like what's below...only sometimes it reads "failed command: READ FPDMA QUEUED" and others "failed command: WRITE DMA EXT".

```
Dec  8 14:56:17 george kernel: [   36.442340] ata4.00: exception Emask 0x10 SAct 0x4 SErr 0x4010000 action 0xe frozen 
Dec  8 14:56:17 george kernel: [   36.442355] ata4.00: irq_stat 0x00400040, connection status changed 
Dec  8 14:56:17 george kernel: [   36.442366] ata4: SError: { PHYRdyChg DevExch } 
Dec  8 14:56:17 george kernel: [   36.442375] ata4.00: failed command: READ FPDMA QUEUED 
Dec  8 14:56:17 george kernel: [   36.442388] ata4.00: cmd 60/08:10:88:a9:87/00:00:1b:00:00/40 tag 2 ncq 4096 in 
Dec  8 14:56:17 george kernel: [   36.442389]          res 40/00:64:30:aa:8b/00:00:12:00:00/40 Emask 0x10 (ATA bus error) 
Dec  8 14:56:17 george kernel: [   36.442408] ata4.00: status: { DRDY } 
Dec  8 14:56:17 george kernel: [   36.442418] ata4: hard resetting link 
Dec  8 14:56:23 george kernel: [   41.724689] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
Dec  8 14:56:24 george kernel: [   42.445422] ata4.00: configured for UDMA/133 
Dec  8 14:56:24 george kernel: [   42.445432] ata4: EH complete
```

I've booted off the "Ultimate Boot Disc" to run the Western Digital DOS drive test utility DLGDIAG 5.04f. That's what's grinding along now.

I'm kind of at wits' end, and wonder what I can test next to say, yes, for sure, the motherboard is bad...if that's what it is. I'd love for a diagnostic program to give me an error, instead of just the kernel freaking out. I'd appreciate any and all advice.

---

### Post by amorangi on 2010-12-19
Did you ever get it fixed? It sounds like either an overheating issue or PSU issue to me. I'm thinking of getting this motherboard, so I'd be interested in hearing back.

---

### Post by RayVad on 2011-01-06
Also would like to know if you have fixed this.
Got same board here and also trying ESXi 4.1.
Got corruption problems with Large files in XP VM. Don't know if this is related and will try Ubuntu with VitualBox.

I know that ESXi has troubles with ICH10R controller and settings in BIOS to RAID(XHD)
Maybe also a problem for Ubuntu?

---

