---
title: "Grub freezes with Highpoint RocketRaid 2240 card"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by mani99 on 2007-09-15
Working system before upgrade:
480w antec psu
Shuttle FS51v1.1 (motherboard from SS51G barebone)
Pentium 4 Norhwood 2.4ghz
2x512mb ddr3200(400mhz)
6gb old IDE system drive
Highpoint RocketRaid 2240 PCI-X (in pci-slot)
8x Seagate 7200.10 320gb SATA

Hardware changed when upgraded:
Shuttle FN95v2 (motherboard from SN95G5 barebone)
AMD x2 3800+

After upgrading my fileserver, I'm unable to boot Kubuntu from livecd or IDE/SATA-harddrive unless I unplug all 8 hard drives connected to the RocketRaid2240. When booting from cd I select the default choice and after a few seconds the screen goes blank and the system freezes. When booting from hard drive the last messages I see before the system freezes are: 

GRUB Loading stage1.5

GRUB loading, please wait...

The 8 drives connected to the Raid-controller are members of a single evms raid5 volume, so I'm only using the controller for additional sata-ports, not hardware-raid. I got the card cheap, and if the card failed I don't want to have to purchase an identical card as they are very expensive, and therefore I used software raid, as it's independent of controllers.

I have tried to disable various components of the motherboard, the sata-ports, IDE ports and changed the boot order for the hard drives. If I set the rocketraid as the first option I don't even get to grub, the screen is just blank.

I've tried more harddrives, some of them sata (on the 2 integrated ports on the motherboard) and get the same error every time.

If there's something I haven't tried that I should, please let me know.

Thanks in advance

Máni

---

