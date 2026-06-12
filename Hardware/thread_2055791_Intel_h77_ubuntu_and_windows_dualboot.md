---
title: "Intel h77 ubuntu and windows dualboot"
date: 2012-09-10
forum: Hardware
---

### Post by tehwizardd on 2012-09-10
Is there any known problems related to h77 chip with having ubuntu 12.04 and windows 7 dualboot and harddrives in raid one?

I plan to have configuration where I have motherboard with h77, two SSD's raid one and two HDD's raid one. 

Just wanted to make sure before I order some expensive hardware.

---

### Post by oldfred on 2012-09-10
Why do you want to RAID the SSD? I would think it would be better to have Windows in one SSD and Ubuntu in the other SSD. 

With RAID you do have to use the alternative installer to have the RAID drivers. But if installing to a non-RAID drive you then can add the RAID drivers from your install.

What video? There are some issues with various combinations. The internal Intel driver seems to work.

You will have a UEFI system and need gpt partitioning.

This site has done a lot of reviews.
[http://www.phoronix.com/scan.php?page=article&item=intel_corei5_3470&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_corei5_3470&num=1)
[http://www.phoronix.com/scan.php?page=article&item=intel_ivybridge_redux&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_ivybridge_redux&num=1)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

There now are many forum posts on dual booting. Not seen much on RAID with UEFI. But I do not know RAID, so have not followed any RAID type systems.
UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Dual Video Intel & nVidia
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

