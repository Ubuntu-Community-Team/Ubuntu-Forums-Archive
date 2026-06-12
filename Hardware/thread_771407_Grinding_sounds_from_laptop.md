---
title: "Grinding sounds from laptop"
date: 2008-04-27
forum: Hardware
---

### Post by Vaftrudner on 2008-04-27
Hello,

I'm kind of in a panic right now. After several hours of usage, my laptop started making grinding sounds. Kind of like gravel on an LP while playing. I shut it down immediately fearing that it might be a processor fan or my HD having a problem. I turned it on later to see if I could pinpoint the sound, there was no error for two hours and then the sound came again. From the direction of my HD. I've turned it on now again to ask for help, it seems to be working perfectly and there's no sound.

I know this is a very strange explanation, but I don't know that much about laptops so I wanted to ask if anyone knows how I can pinpoint this problem more exactly?

I get a lot of these in dmesg:

[  636.664000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x35fdf FIS=005040a1:00002000)
[  636.664000] ata1.00: cmd 60/10:00:75:13:99/00:00:0f:00:00/40 tag 0 cdb 0x0 data 8192 in
[  636.664000]          res 50/00:18:25:e5:98/00:00:0f:00:00/40 Emask 0x2 (HSM violation)
[  636.664000] ata1.00: cmd 60/08:08:ad:d6:98/00:00:0f:00:00/40 tag 1 cdb 0x0 data 4096 in
[  636.664000]          res 50/00:18:25:e5:98/00:00:0f:00:00/40 Emask 0x2 (HSM violation)

Is my HD dying? What do you think?

---

### Post by Vaftrudner on 2008-04-27
I had that sound again, this is the latest in dmesg:

[ 1375.340000] ata1.00: exception Emask 0x2 SAct 0x1c SErr 0x0 action 0x2 frozen
[ 1375.340000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x1c FIS=005040a1:00000002)
[ 1375.340000] ata1.00: cmd 61/08:10:65:27:a8/00:00:11:00:00/40 tag 2 cdb 0x0 data 4096 out
[ 1375.340000]          res 50/00:08:45:27:68/00:00:12:00:00/40 Emask 0x2 (HSM violation)
[ 1375.340000] ata1.00: cmd 61/08:18:75:27:a8/00:00:11:00:00/40 tag 3 cdb 0x0 data 4096 out
[ 1375.340000]          res 50/00:08:45:27:68/00:00:12:00:00/40 Emask 0x2 (HSM violation)
[ 1375.340000] ata1.00: cmd 61/08:20:45:27:68/00:00:12:00:00/40 tag 4 cdb 0x0 data 4096 out
[ 1375.340000]          res 50/00:08:45:27:68/00:00:12:00:00/40 Emask 0x2 (HSM violation)
[ 1375.652000] ata1: soft resetting port
[ 1375.824000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1375.824000] ata1.00: configured for UDMA/100
[ 1375.824000] ata1: EH complete
[ 1375.824000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1375.824000] sd 0:0:0:0: [sda] Write Protect is off
[ 1375.824000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1375.824000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

