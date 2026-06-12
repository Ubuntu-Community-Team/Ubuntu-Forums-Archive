---
title: "Hard Drive Timeout Issues"
date: 2009-07-23
forum: Hardware
---

### Post by kc9ddi on 2009-07-23
Hi - I'm having some strange problems that I believe are related to my harddrive.  Basically, every couple minutes, the system will stop responding for a few seconds, and then start responding again.  During the times that it stops responding, I gradually loose functionality.  Eg, at first I won't be able to click on buttons within applications, but I can switch applications.  Then, I won't be able to switch applications at all.  Usually the mouse cursor and the numlock/capslock lights don't fail at any point during this.

My setup is Kubuntu Jaunty fully upgraded, with kernel 2.6.28-13-generic.  I also had this same problem on previous releases of Kubuntu.  I have not tried any non-Linux OSs.  Hardware is an Acer Aspire 7104WSMi laptop with a SATA hard drive.  I've actually replaced the hard drive, and got identical symptoms before and after replacing the harddrive.

I see this output in dmesg:

```
[ 3274.003143] ata1.01: status: { DRDY }
[ 3279.048039] ata1: link is slow to respond, please be patient (ready=0)
[ 3284.032038] ata1: device not ready (errno=-16), forcing hardreset
[ 3284.032050] ata1: soft resetting link
[ 3284.236603] ata1.00: configured for UDMA/100
[ 3284.276837] ata1.01: configured for UDMA/33
[ 3284.285652] ata1: EH complete
[ 3284.293418] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 3284.308924] sd 0:0:0:0: [sda] Write Protect is off
[ 3284.308930] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3284.340561] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3284.372564] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 3284.388593] sd 0:0:0:0: [sda] Write Protect is off
[ 3284.388598] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3284.413083] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3507.002951] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3507.002964] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 3507.002965]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 3507.002967]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 3507.002971] ata1.01: status: { DRDY }
[ 3512.048038] ata1: link is slow to respond, please be patient (ready=0)
[ 3517.048038] ata1: device not ready (errno=-16), forcing hardreset
[ 3517.048050] ata1: soft resetting link
[ 3517.252575] ata1.00: configured for UDMA/100
[ 3517.284436] ata1.01: configured for UDMA/33
[ 3517.292452] ata1: EH complete
[ 3517.308592] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 3517.324815] sd 0:0:0:0: [sda] Write Protect is off
[ 3517.324819] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3517.340507] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3517.356582] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 3517.376558] sd 0:0:0:0: [sda] Write Protect is off
[ 3517.376562] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3517.400582] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```


I don't really know if this is hardware or software related, but I'd appreciate any help in narrowing down exactly what the problem is.

---

### Post by sarfarazkazi on 2009-07-23
Check your hard disk cable, might be faulty.

---

### Post by kc9ddi on 2009-07-23
In this laptop there doesn't seem to be a cable - the hdd slides into a socket.  I've examined the hdd and socket and re-seated it a couple times, and I still get the same behavior.

---

