---
title: "Cdrom drive/cable failure?"
date: 2010-06-12
forum: Hardware
---

### Post by LoloftheRings on 2010-06-12
Hi all,

While I was installing battefield 2 yesterday (wine), the installation suddenly froze. The cdrom drive didn't respond at all, the eject button didn't work either. I rebooted, and.. well.. it took quite a while to reboot. I tried Windows, it didn't boot at all.

After some messing around, I decided to unplug my cdrom drive, which was causing the problems. The errors went away. A few hours later, I plugged it back in and everything just worked.

I got the same issue today when trying to launch Battlefield (yea.. It's really the only CDROM I every use these days). This is what dmesg says about the problem:

```

$ dmesg|grep ata3
ata3: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7200 irq 30
ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata3.00: ATAPI: TSSTcorpDVD-ROM SH-D163B, SB04, max UDMA/33, ATAPI AN
ata3.00: configured for UDMA/33
ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata3.00: configured for UDMA/33
ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata3.00: configured for UDMA/33
ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
ata3.00: status: { DRDY }
ata3: hard resetting link
ata3: softreset failed (device not ready)
ata3: hard resetting link
ata3: softreset failed (device not ready)
ata3: hard resetting link
ata3: link is slow to respond, please be patient (ready=0)
ata3: softreset failed (device not ready)
ata3: limiting SATA link speed to 1.5 Gbps
ata3: hard resetting link
ata3: softreset failed (device not ready)
ata3: reset failed, giving up
ata3.00: disabled
ata3: EH complete

```What do you think, is it the sata cable, the cdrom drive or maybe something else? I still have warranty but I don't want to let them investigate, they're not really good at doing it quick.. Might take a week or two :mad:

It's really strange that it suddenly worked again, no idea why it did. I did mess around with the cables to see which worked and which didnt. 

The following part showed up during boot, I believe it to be the initrd part:
```

ata3: link is slow to respond, please be patient (ready=0)
ata3: softreset failed (device not ready)
ata3: limiting SATA link speed to 1.5 Gbps
ata3: hard resetting link
ata3: softreset failed (device not ready)
ata3: reset failed, giving up

```

I'm currently using Arch by the way, but I just love this forums :)

Hope anyone can help me around here, any help or advice would be apprieciated.

---

