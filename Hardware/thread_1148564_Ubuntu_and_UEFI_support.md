---
title: "Ubuntu and UEFI support?"
date: 2009-05-04
forum: Hardware
---

### Post by ajmas on 2009-05-04
I am looking to upgrade my motherboard in the next three months, and will be looking into buying a UEFI based motherboard. The thinking here is that I will be using a 64-bit processor (Core 2 Duo or better) and don't want to deal with the 2.2TB limit on hard drives. I also don't want to be replacing my motherboard within a year of purchasing it.

For this reason, does anyone know what the current state of EFI/UEFI support is in Ubuntu? I know the existence of [ELILO]("http://sourceforge.net/projects/elilo/") and [rEFIt ]("http://refit.sourceforge.net/"), though I don't whether they are the only necessary parts for getting Ubuntu working on this hardware, and whether they are already part of Ubuntu?

---

### Post by krazyd on 2010-04-10
Any update on this? Has anyone installed Lucid (or Karmic) on a UEFI system? 

I would like to install GRUB2 (without rEFIt or similar) on a HP laptop with UEFI and there seems to be little information on whether this is supported in Ubiquity.. :confused:

---

### Post by srs5694 on 2010-04-10
I don't know about Ubuntu specifically, and I don't know many specifics, but I do know that Linux in general works with EFI/UEFI. In addition to ELILO, there's [GRUB 2 support for EFI.](http://grub.enbug.org/TestingOnEFI) I don't know if Ubuntu's version of GRUB 2 includes this support.

Also, UEFI is *not* required to overcome the 2TiB limit of MBR. I've got several computers that boot just fine using GUID Partition Table (GPT) disks on BIOS-based computers. I'm typing on one of them. The most important caveat on this score is to be sure to create a small (100KiB to 1MiB) [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) to hold part of GRUB 2. Another caveat is that some BIOSes seem to have problems with specific GPT configurations, but these problems seem to be rare and are easily overcome. See [my Web page on the topic](http://www.rodsbooks.com/gdisk/bios.html) for more information.

---

### Post by krazyd on 2010-04-14
Hi, thanks for the information.

I realise that the kernel supports UEFI, but my question was more about the ubuntu installer. Does it correctly create the EFI partition so that grub2 can boot without rEFIt? My main motivation is the faster boot time of EFI over BIOS.
eg.
[http://www.engadget.com/2009/09/24/video-phoenix-instant-boot-bios-starts-loading-windows-in-under/](http://www.engadget.com/2009/09/24/video-phoenix-instant-boot-bios-starts-loading-windows-in-under/)

Imagine Ubuntu on that, POST-ing in under a second!

---

