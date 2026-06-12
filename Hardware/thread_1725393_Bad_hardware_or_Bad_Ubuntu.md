---
title: "Bad hardware or Bad Ubuntu?"
date: 2011-04-09
forum: Hardware
---

### Post by wwbdd on 2011-04-09
I just replaced my motherboard (one of the early generation sandy bridge systems that was recalled), and I'm getting some strange errors. I'm trying to figure out if there is something wrong with the new motherboard, or if it is a software problem.

Every now and then, the system becomes nearly unresponsive, sometimes I have to hard reboot, other times I can wait for 30 seconds or so and it's fine. In the cases in which it is only temporary, I have looked at the output of dmesg to see what's been going on.  I'm seeing some errors, hopefully someone with more knowledge of the linux kernel can help me understand what's going on here.

```
[ 3248.263186] ata10: SError: { 10B8B Dispar }
[ 3248.263196] ata10.00: failed command: WRITE FPDMA QUEUED
[ 3248.263203] ata10.00: cmd 61/08:20:bf:61:81/00:00:0e:00:00/40 tag 4 ncq 4096 out
[ 3248.263204]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 3248.263207] ata10.00: status: { DRDY }
[ 3248.263210] ata10.00: failed command: WRITE FPDMA QUEUED
[ 3248.263215] ata10.00: cmd 61/08:28:c7:aa:81/00:00:0e:00:00/40 tag 5 ncq 4096 out
[ 3248.263217]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 3248.263219] ata10.00: status: { DRDY }
[ 3248.263222] ata10.00: failed command: WRITE FPDMA QUEUED
[ 3248.263227] ata10.00: cmd 61/08:30:87:34:82/00:00:0e:00:00/40 tag 6 ncq 4096 out
[ 3248.263228]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 3248.263231] ata10.00: status: { DRDY }
[ 3248.263233] ata10.00: failed command: WRITE FPDMA QUEUED
[ 3248.263238] ata10.00: cmd 61/08:38:7f:75:82/00:00:0e:00:00/40 tag 7 ncq 4096 out
[ 3248.263240]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 3248.263242] ata10.00: status: { DRDY }
[ 3248.263244] ata10.00: failed command: WRITE FPDMA QUEUED
[ 3248.263250] ata10.00: cmd 61/38:40:87:75:82/00:00:0e:00:00/40 tag 8 ncq 28672 out
[ 3248.263251]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 3248.263254] ata10.00: status: { DRDY }
[ 3248.263256] ata10.00: failed command: WRITE FPDMA QUEUED
[ 3248.263261] ata10.00: cmd 61/10:48:bf:01:00/00:00:05:00:00/40 tag 9 ncq 8192 out
[ 3248.263263]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 3248.263265] ata10.00: status: { DRDY }
[ 3248.263270] ata10: hard resetting link
[ 3248.793183] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 3248.798328] ata10.00: configured for UDMA/133
[ 3248.798335] ata10.00: device reported invalid CHS sector 0
[ 3248.798338] ata10.00: device reported invalid CHS sector 0
[ 3248.798340] ata10.00: device reported invalid CHS sector 0
[ 3248.798342] ata10.00: device reported invalid CHS sector 0
[ 3248.798345] ata10.00: device reported invalid CHS sector 0
[ 3248.798347] ata10.00: device reported invalid CHS sector 0
[ 3248.798357] ata10: EH complete
[ 4372.913053] ata10.00: exception Emask 0x0 SAct 0x20 SErr 0x180000 action 0x6 frozen
[ 4372.913063] ata10: SError: { 10B8B Dispar }
[ 4372.913065] ata10.00: failed command: WRITE FPDMA QUEUED
[ 4372.913067] ata10.00: cmd 61/50:28:f7:e2:20/03:00:05:00:00/40 tag 5 ncq 434176 out
[ 4372.913068]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 4372.913069] ata10.00: status: { DRDY }
[ 4372.913071] ata10: hard resetting link
[ 4373.442323] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 4373.447325] ata10.00: configured for UDMA/133
[ 4373.447328] ata10.00: device reported invalid CHS sector 0
[ 4373.447332] ata10: EH complete
```

Is there a way to fix this?  Or is this the sign of a failing drive or a failing SATA controller?

---

### Post by dabl on 2011-04-09
That's a hard drive or SATA controller problem (or perhaps motherboard integration problem).  Do you have a disk diagnostics tool that you can use on it?  If you test the hard drive in another (known good) computer, and the hard drive itself has no issues, then I'd be looking at the motherboard and the SATA controller with suspicious eyes.

---

### Post by wwbdd on 2011-04-09
That was what I was afraid.  The problem presented itself immediately after I replaced the motherboard.  Somehow I doubt it is one of the disks; they are only about a month old, and again, they had been working perfectly fine until I replaced the motherboard.

What disk diagnostic utilities do you recommend I try? Can I do it from within ubuntu, or do I have to create a boot usb-stick and run it from there? If the controller is bad, does a disk check even mean anything?

---

### Post by Yellow Pasque on 2011-04-09
Make sure BIOS is updated and also see if there's any setting in there to limit the SATA controller to 3.0Gb/s mode.

---

