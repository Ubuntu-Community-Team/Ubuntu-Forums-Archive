---
title: "CD-ROM malfunction? (interresting troubleshoot ;-)"
date: 2010-01-09
forum: Hardware
---

### Post by mobrien118 on 2010-01-09
Hello,

I am having a terrible time with my Ubuntu system since I upgraded to Karmic, although I suspect Hardware failure, but need to know how to figure this out.

My system freezes sometimes, and while playing DVDs locally, I get this error set in "dmesg" frequently:
```
[ 6668.955818] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 6668.955823] ata4.00: BMDMA stat 0x26
[ 6668.955833] ata4.00: cmd a0/01:00:00:00:fc/00:00:00:00:00/a0 tag 0 dma 131072 in
[ 6668.955835]          cdb 28 00 00 04 5b 46 00 00  40 00 00 00 00 00 00 00
[ 6668.955836]          res 51/44:03:00:00:08/00:00:00:00:00/a0 Emask 0x20 (host bus error)
[ 6668.955840] ata4.00: status: { DRDY ERR }
[ 6669.010215] ata4.00: configured for UDMA/100
[ 6669.010229] ata4: EH complete
```

I booted into the latest gparted-livecd and got this error once while performing a e2fsck scan:
```
[  382.000037] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  382.000049] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  382.000051]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  382.000052]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  382.000056] ata2.00: status: { DRDY }
[  387.040023] ata2: link is slow to respond, please be patient (ready=0)
[  392.024025] ata2: device not ready (errno=-16), forcing hardreset
[  392.024032] ata2: soft resetting link
[  392.180130] ata2.01: NODEV after polling detection
[  392.204240] ata2.00: configured for UDMA/100
[  392.206414] ata2: EH complete
```

How can I know what the system is referring to as "ata2" and "ata4" in these errors? Are they different in the different distros? Does this look like my MOBO is failing, because I have tried numerous SATA cables and they don't fix it, however, depending on which BUS I put each device on seems to make a difference in the frequency of the errors.

Why do computers have to be so Complicated? (j/k :-)

Thanks in advance for ANY insight you can offer into the issue.

--mobrien118

---

### Post by mobrien118 on 2010-01-12
Just for reference, I have solved this problem.

I have always had issues with disruption of the video signal from the on-board video to my (old) LCD, and since this is a bargain basement ECS motherboard, I figured using a PCI-E graphics card and disabling it was worth a try. If that didn't work, i was going ti try audio next, then other methods to eliminate EMI.

Well, simply putting in a GeForce GT 220 card seems to have dont the trick. I have been running for a few days now, and the things that would trigger many errors, like watching a video or using Boxee, are working just fine.

So, it is a hardware issue and solved.

If anyone would like to post any suggestions on how I *could have* gone about troubleshooting this with software, please feel free.

--mobrien118

---

