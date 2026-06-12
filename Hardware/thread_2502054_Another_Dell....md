---
title: "Another Dell..."
date: 2024-10-31
forum: Hardware
---

### Post by ekraus0227 on 2024-10-31
We all know dell's just suck in general. So I have this Dell 980 which supposedly ran the latest LTS version. I however accidentally removed it and haven't been able to figure out what copy they used, because the ISO from clicking Ubuntu Desktop Download, won't boot. I'm assuming it's a BIOS issue? However I've tried multiple different combinations and I just can't seem to get it. Anyone have personal experience? I never have had issues booting linux on any other computer.. So this is wild that I do, have to ask. Pic below is what my bios is. 

[bios-system-information-optiplex-7050.png]("https://i.dell.com/sites/csimages/App-Merchandizing_esupport_flatcontent_Images/all/bios-system-information-optiplex-7050.png")

Oh and it doesn't let me select UEFI or legacy. Only Legacy and RAID (3 different raid types)

---

### Post by TheFu on 2024-10-31
[https://www.dell.com/support/kbdoc/en-us/000131655/how-to-install-ubuntu-linux-on-your-dell-pc](https://www.dell.com/support/kbdoc/en-us/000131655/how-to-install-ubuntu-linux-on-your-dell-pc) is Dell's recommendation. You've probably been following it already.

I have a "new to me" Dell laptop and had no issues installing LM 22 onto it. That's based on Ubuntu 24.04.  There were some BIOS settings that I modified, but I did that before attempting any install. I don't recall what they were, just things that I'd read a few different places that would impact booting. I'm positive that I disabled any Intel-Storage/RAID and I probably disabled any TPM stuff, SecureBoot, etc.

I've been buying Dell laptops since around 2005 and have been mostly happy with the results.  Happier than with any other vendor's options.
As for desktops, I learned long ago never to buy a pre-built desktop from anyone. Got burned for over $1000 and never plan to do that again. $300 and 30 minutes of my time is enough to let me upgrade my current "desktop" to a system 10x faster when it is time for an upgrade.  The key thing is to have standard components and put them into standard cases.

But lots of people for some reason like to buy lots of extra hardware that isn't needed every time they want a little faster computer.  That's their choice, I suppose.  When my car needs an oil change, I'd rather pay for the oil change, not a new engine.

---

### Post by Yellow Pasque on 2024-10-31
From what I can tell, the Optiplex 980 (I'm assuming that's what you meant by 980) is strictly old-school BIOS and doesn't support UEFI, so you need to make sure the USB is partitioned/formatted with MBR and FAT32.
> Only Legacy and RAID (3 different raid types)
That's a different setting, for your SATA controller. Legacy is probably referring to legacy IDE mode. You probably want that set to "RAID Autodetect / AHCI" so it will give you AHCI unless you have some kind of RAID set up.

---

### Post by ekraus0227 on 2024-10-31
Thanks! I'll give AHCI a try and yes I do MBR with Fat32 via Rufus on windows. I also uncheck the use of TPM, so it's to not enable or disable the feature from there, just keep it unchecked. I've been trying sata ubuntu and USB. I used a virtual machine to change the first partition of the ubuntu hard drive to work on legacy, however I'm not sure what it really did.

---

### Post by TheFu on 2024-10-31
> **ekraus0227 said:**
> Thanks! I'll give AHCI a try and yes I do MBR with Fat32 via Rufus on windows. I also uncheck the use of TPM, so it's to not enable or disable the feature from there, just keep it unchecked. I've been trying sata ubuntu and USB. I used a virtual machine to change the first partition of the ubuntu hard drive to work on legacy, however I'm not sure what it really did.

Uh, a full VM doesn't touch any real hardware.  VMs provide virtual hardware of the most compatible type, so unless you are using a hypervisor that allows PCI passthru AND have done the 20 steps to do that, your VM isn't touching any real hardware.  Er ... unless you could USB passthru, which isn't hard for any hypervisor.

To all but the 1% doing extremely high-performance computing, the different storage access modes don't provide much that is useful.  I have no idea how old your 980 is. My Dell laptop is from 2022-ish - it was a business end-of-lease laptop, so it had lots of the best things that 2022 Dell laptops had.  If the 980 is from 2012 or earlier, it may not even support UEFI at all.  I don't really remember when MSFT started mandating UEFI booting.  Those older BIOSes were a little odd with UEFI. Most didn't correctly implement the standard beyond what was needed for MS-Windows to work, so legacy booting was the normal workaround unless you were willing to copy some boot files around manually.  I had a Toshiba laptop in 2015 that still needed for UEFI boot files to be manually copied AND renamed like they were for MS-Windows, though the computer never had MS-Windows on it - ever. It wasn't even shipped with MS-Windows.

---

### Post by ekraus0227 on 2024-11-01
I'm aware what VM's do. I used a different computer to access the hard drive.

---

