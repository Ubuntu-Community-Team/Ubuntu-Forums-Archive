---
title: "SSD in Optical Drive Caddy not detected by grub, cannot boot from it"
date: 2019-08-28
forum: Hardware
---

### Post by cmkmanwani on 2019-08-28
Hi,
My situation is somewhat similar to this [https://ubuntuforums.org/showthread.php?t=2342662](https://ubuntuforums.org/showthread.php?t=2342662), but not exactly. I'll try to give all the details, but if I miss out on something please do tell me as I have been unable to find a solution for this on my own.
I have a Dell Inspiron 3543 which came with a HDD. I currently have a dual boot set up on this HDD. Windows 7 and Ubuntu 18.04. I recently bought a Samsung 860 Evo SSD and installed Ubuntu 18.04 on it as well. My end goal is to use the SSD OS for my regular work. Both HDD and SSD have MBR partition table.
**Issue:** Grub shows entry for SSD Ubuntu but shows error - 
error: load kernel first
error: cannot find C\H\S values
On the grub terminal, the ls command does not shoe hd1 (SSD) and only shows the HDD. I think this is the issue but do not know how to resolve it. The fstab file does not have an entry for the SSD, but I do not know how to add an entry there since I am unsure what the mount point would be. Grub config file shows that it tries to mount SSD on / but as I mentioned above, the OS does not load.
**End Goal:** To be able to boot into any OS, Windows or Ubuntu on HDD and Ubuntu on SSD.
**Possible Compromise:** To only be able to boot into SSD.
I cannot switch the places for the SSD and HDD as the HDD is thicker than the SSD so it won't fit in the caddy. I want to use SSD as main OS and HDD as secondary storage. 

**What I have tried:**
1. Disabling fast boot from BIOS.
2. Tinkered around with EasyBCD, that made the situation worse, had to reconfigure grub.
3. Scour the Internet for relevant info and try possible solutions.

So far I haven't been able to solve this issue. Kindly help me out.
Please ask for any information that you need and I will provide it asap.

---

### Post by oldfred on 2019-08-28
Dell typically needs UEFI update & SSDs need firmware updates, even if new you need to check if latest versions of firmware.

But some systems, will not boot from a drive in the DVD caddy. Seems strange that DVD will boot but HDD will not. For those ESP or bios_grub (if gpt) and maybe a /boot needs to be on internal drive with rest of system on drive in caddy. Best to experiment to see whether your system will directly boot or not.

If MBR and BIOS, you can use gpt partitioning only on Ubuntu only drives if you have a bios_grub partition. I converted to gpt with BIOS boot in 2010 on my XP BIOS only system, XP still on MBR drive. Retired XP in 2011  as a new tiny 60GB SSD had to have AHCI, but XP did not make it easy to install AHCI drivers (total reinstall with slipstream drivers during install). And since then every new or totally repartitioned drive has been gpt, even larger flash drives.

---

### Post by slickymaster on 2019-08-28
Thread moved to **Hardware** for a better fit

---

### Post by cmkmanwani on 2019-08-28
> **oldfred said:**
> 
Dell typically needs UEFI update & SSDs need firmware updates, even if new you need to check if latest versions of firmware.

I updated the BIOS to the latest version a few days ago while trying all this out, did not make any difference.
> **oldfred said:**
> 
For those ESP or bios_grub (if gpt) and maybe a /boot needs to be on internal drive with rest of system on drive in caddy.

I found this while searching for a solution but I did not find a way to do this. Is there any resource I could follow to accomplish this?

> **oldfred said:**
> 
If MBR and BIOS, you can use gpt partitioning only on Ubuntu only drives if you have a bios_grub partition. I converted to gpt with BIOS boot in 2010 on my XP BIOS only system, XP still on MBR drive. Retired XP in 2011 as a new tiny 60GB SSD had to have AHCI, but XP did not make it easy to install AHCI drivers (total reinstall with slipstream drivers during install). And since then every new or totally repartitioned drive has been gpt, even larger flash drives.


I didn't quite get you here. Should I format my SSD and reinstall Ubuntu with GPT?

---

### Post by oldfred on 2019-08-28
You do not have to, its just that gpt is only 15 years old where MBR is 35 years old and there are some advantages to gpt.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr) 
    
If you reinstall, you can use Something Else and put grub &  /boot partition on HDD internal drive and / (root) on the SSD.
You can move a /boot from / folder to a partition and edit fstab to then mount new /boot partition. And generally have to reinstall grub. Often easier with Boot-Repair as it will recognize your /boot partition (if already in fstab). 
Manual re-install of grub from live installer also requires you to mount /boot in addition to /.

---

