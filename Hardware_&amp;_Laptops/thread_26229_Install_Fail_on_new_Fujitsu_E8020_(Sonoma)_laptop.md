---
title: "Install Fail on new Fujitsu E8020 (Sonoma) laptop"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by sweenes on 2005-04-12
Hi / Help 

Hoary won't install on my new laptop (a fujitsu-siemens E8020), it uses SATA and there's no bios option to set compatibility mode to PATA. Gentoo (2005.0) manages it, probably because of SATA support in the kernel (from what I've been reading on other newsgroups.)

Basically, it complains during the install about not being able to load CD-ROM drivers. After looking at other posts on here, I'm convinced the SATA is stopping normal detection of the IDE CD-ROM. 

Because I can't even get onto the machine, I don't know what to do next. Some posts on forums say 'Rebuild the kernel to include SATA support' while others say they have installed Hoary on SATA systems with no such faffing about.

Can anyone suggest a definitive coarse of action. I want ubuntu, and I'll accept no substitutes, Gentoo or otherwise... [-X 

Thanks in advance,

Steve-O

---

### Post by heimo on 2005-04-12
Ubuntu 5.04 can be installed on SATA disks with the default kernel. I've done it on my system (with prerelease version). So this detecting CDROM error may be unrelated. Maybe it has something to do with ICH6M (South Bridge on you mother board?) support? 

I went through lots of forums about this and saw the same thing you said. But you don't need special kernel just because of SATA disk. What you could try is disabling DMA (if that's available on your BIOS, those laptop BIOSes...) Or maybe it can be forced on the boot menu? dma=off or something like that. That's a very faint idea, but I saw someone with same south bridge having problems with DMA.

Would it be possible to use external CD-drive to install Ubuntu and then diagnosing what's wrong with the CD drive? That would at least make it easier.

---

### Post by sweenes on 2005-04-12
Thanks for a speedy reply man :)

I hear what you're saying. The south bridge answer you've suggested sounds plausible. I don't have an external CD-ROM drive, but I could look at installing it from the network as an alternative.

I'll post my progress back here, if there's any body else with the same problem, please add your solution if you find one.

Thanks,

Steve-O

---

### Post by Innocent on 2005-09-08
Had an exactly similar problem. Disabling AHCI in BIOS did the trick.

Inno

---

### Post by sweenes on 2005-12-23
Same here - disabling AHCI in the bios worked for me. 

Sadly I had to reinstall windows afterward as it repeatedly hung in what looked like a hardware detection/initalisation phase of startup. Safe mode etc. didn't help, but the reinstall only overwrote the system files so my data was intact. Also I think I could access the volume from Ubuntu using the read-only NTFS driver, so I could've backed up the winxp partition data.

Can anyone tell me if I'm somehow taking a performance hit by turning off AHCI though?

---

