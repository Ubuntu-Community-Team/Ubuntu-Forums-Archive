---
title: "May be time for a new computer - Possible motherboard/IDE issue"
date: 2010-05-31
forum: Hardware
---

### Post by Zerp64 on 2010-05-31
So about every two minutes or so when there is HDD activity on any of my drives (say I'm downloading a torrent or something, or something else that is very HD intensive) my computer gets totally locked up for about 30 seconds, with the HD indicator light on my tower glows steadily. This computer is pretty old (got it in '02, maybe) and has been through the ringer- power surges, a video card literally melting inside of it, hotswapping, overclocking, and just about anything else considered not-so-good-for-computers, so I'm thinking that it's about time the thing needs to be laid to rest. Still, if I can get a few more miles out of it, I wouldn't mind that at all.

So, rant over. Here's a segment of dmesg immediately after one of these lockups:
```
[ 2437.042231] ata1.01: status: { DRDY }
[ 2437.042259] ata1: soft resetting link
[ 2437.396640] ata1.00: configured for UDMA/33
[ 2437.412395] ata1.01: configured for UDMA/33
[ 2437.412403] ata1.01: device reported invalid CHS sector 0
[ 2437.412414] ata1: EH complete
[ 2897.000042] ata1: lost interrupt (Status 0x58)
[ 2897.000077] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2897.000085] ata1.01: failed command: WRITE DMA EXT
[ 2897.000093] ata1.01: cmd 35/00:48:2e:9d:81/00:00:12:00:00/f0 tag 0 dma 36864 out
[ 2897.000095]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 2897.000099] ata1.01: status: { DRDY }
[ 2897.000126] ata1: soft resetting link
[ 2897.356901] ata1.00: configured for UDMA/33
[ 2897.372378] ata1.01: configured for UDMA/33
[ 2897.372386] ata1.01: device reported invalid CHS sector 0
[ 2897.372397] ata1: EH complete
[ 3959.576267] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[ 3959.576275] ata1.01: BMDMA stat 0x65
[ 3959.576280] ata1.01: failed command: READ DMA EXT
[ 3959.576288] ata1.01: cmd 25/00:60:7f:26:04/00:01:09:00:00/f0 tag 0 dma 180224 in
[ 3959.576290]          res 36/36:36:36:36:36/00:00:00:00:00/36 Emask 0x3 (HSM violation)
[ 3959.576293] ata1.01: status: { DF }
[ 3959.576296] ata1.01: error: { IDNF ABRT }
[ 3959.576324] ata1: soft resetting link
[ 3963.124527] ata1.00: configured for UDMA/33
[ 3963.141952] ata1.01: configured for UDMA/33
[ 3963.141978] ata1: EH complete
[ 3963.916791] usb 1-4: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[ 4461.000039] ata1: lost interrupt (Status 0x58)
[ 4461.000073] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 4461.000081] ata1.01: failed command: WRITE DMA EXT
[ 4461.000090] ata1.01: cmd 35/00:08:76:b1:81/00:00:12:00:00/f0 tag 0 dma 4096 out
[ 4461.000091]          res 40/00:36:36:36:36/00:00:00:00:00/36 Emask 0x4 (timeout)
[ 4461.000095] ata1.01: status: { DRDY }
[ 4461.000123] ata1: soft resetting link
[ 4461.357141] ata1.00: configured for UDMA/33
[ 4461.372397] ata1.01: configured for UDMA/33
[ 4461.372416] ata1: EH complete
[ 5224.000532] ata1: lost interrupt (Status 0x58)
[ 5224.000568] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 5224.000577] ata1.01: failed command: WRITE DMA EXT
[ 5224.000585] ata1.01: cmd 35/00:20:ae:c5:81/00:00:12:00:00/f0 tag 0 dma 16384 out
[ 5224.000587]          res 40/00:36:36:36:36/00:00:00:00:00/36 Emask 0x4 (timeout)

```

I'm guessing that the 'soft resetting link' is the thing causing my computer to lock up like it is. Hard drives are all PATA, and they're all newer than the PC (as in, the original drive was fried after a power surge), so I don't think the hard drives themselves are the problem. I suspect the IDE cables are damaged (they are very bent out of shape), or maybe the IDE port on the mobo itself.

What do you all think? Is it time to relegate this machine to the graveyard, or can I fix it yet again?

*EDIT:* Oh, forgot to mention that the system locked up a good three or four times while I wrote this.

---

### Post by Zerp64 on 2010-06-02
Bump. I don't like these freezes every few minutes.

Using an HP Pavilion a800n, Radeon HD 4650, 2.2GHz processor with three HDs, one new 500Gig HDD and two 160Gig drives, all Maxtor.

---

### Post by josarn on 2010-06-03
Hi there! Based on what you say should the problem be the cable it should be unexpensive to test that possibility. If not, pinpointing the issue can cost time and money better spent on building a new system. Just an opinion, though...

---

### Post by mindpowerz on 2010-06-03
System freezes can also be due to overheating processor, or faulty motherboard.

I think that migrating your hard drives (but that would mean re-installing OS as well) would solve your problem.

---

### Post by texaswriter on 2010-06-03
I vote for ripping that computer's guts out but keeping that nice heavy computer exterior, you know, so at least the veneer of that old computer lives on... I'm always a big fan of reusing components and am very disappointed in the way the computer industry turned out so much in favor of NOT recycling. I make all my computers and would custom build my laptops if I could [easily]. That said, I don't have much use for laptops and much prefer the robustness and long-life of desktop PC's. 

If you are all for value for your dollar, you can always pick up NICE cpu/mobo combo's at your local Fry's OR try [www.newegg.com](www.newegg.com) as well. Throw in some appropriate memory [at a deal] and you've got the core of a new computer. Reuse CDROM/DVDROM + hard drives + peripherals and VOILA!!!! 
 
New computer inside, old comfortable one outside, and you managed to preserve the environment [a little bit] by conserving.

---

### Post by Zerp64 on 2010-06-12
> **texaswriter said:**
> I vote for ripping that computer's guts out but keeping that nice heavy computer exterior, you know, so at least the veneer of that old computer lives on... I'm always a big fan of reusing components and am very disappointed in the way the computer industry turned out so much in favor of NOT recycling. I make all my computers and would custom build my laptops if I could [easily]. That said, I don't have much use for laptops and much prefer the robustness and long-life of desktop PC's. 

If you are all for value for your dollar, you can always pick up NICE cpu/mobo combo's at your local Fry's OR try [www.newegg.com](www.newegg.com) as well. Throw in some appropriate memory [at a deal] and you've got the core of a new computer. Reuse CDROM/DVDROM + hard drives + peripherals and VOILA!!!! 
 
New computer inside, old comfortable one outside, and you managed to preserve the environment [a little bit] by conserving.

This is exactly what I did.

Turns out the motherboard was finally giving out, so I decided to finally spring for a new computer. I didn't want to bother with building one (I know, I'll regret it later) and just bought one from Fry's. The thing was pretty cheap, only about $340, but it flies compared to my old one. I guess you crazy kids with your silly PCI-e and your 64-bit processors and SATA drives were right. Also, it's got a good NVidia integrated card (so no need to upgrade right away) and doesn't sound like it's being cooled by a leaf blower like my old one.

Anyways, I had an old external USB DVD-RW that I don't really need anymore, so I scooped out the drive and replaced it with my old 500 GB drive. Works absolutely fine, but I wish I could use my other drives, too.

So yeah, thanks guys. Now I'm all excited about my 64-bit processor that wasn't made in 1992 like my last computer's processor was.

By the way, if anyone wants to give me a free Nvidia card that's better than a 6200, let me know. ;)

*Edit:* I also might try to repurpose my old computer to do.... something. I just don't know what yet. Something that would still be useful despite locking up every thirty seconds.

---

