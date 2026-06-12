---
title: "ASMedia RAID1"
date: 2015-07-29
forum: Hardware
---

### Post by Alabamian on 2015-07-29
I have an ASMedia ASM106x PCI-Express to SATA 6Gbs controller card in a Dell Optiplex 790.  I have two 750 Gb drives on the ASM106x controller, and want to install Ubuntu onto these two drives as a RAID 1 system.  However, every time I boot and get past the little Ubuntu "man" symbol and the sequential "lights", the screen goes blank.  I've tried booting from the regular 14.04.2 Desktop disk, the 14.04 Server disk, and even a CentOS 7 with Gnome boot disk.  In all cases, after seeing the POST and going to the boot DVD volume and a small amount of initial interaction to indicate it is beginning to use the boot disk, there's this small amount of access, then nothing.  Dead screen.  No errors, no nothing.  I've set the BIOS ATA after the initial AHCI didn't work (it's back to AHCI, which is what the contoller is supposed to use, from my understanding).  I've turned off PCXE for the Ethernet NIC if that might have anything to do with it -- no change in behavior.  I turned off SATA 2 from the motherboard (the ASM card on the POST says it's using SATA 2), but it behaves exactly the same regardless of whether the SATA2 is active or disabled on the motherboard.  Any help is appreciated.

---

### Post by Alabamian on 2015-07-31
I gave up on the SD-PEX40049 SATA PCI Express Card.  I eventually found this [site]("http://www.ubuntulinuxguide.com/software-raid-ubuntu-14-04-setup-install-configure/") from Randy Ray, which worked for me perfectly.  Sadly, I had used Ubuntu's own Software RAID sites for days and days with only frustration resulting.  Randy Ray tells you how to REALLY do it.  Wish I'd found his site before buying this card, and it's truly a shame Ubuntu doesn't have better explanations about how to set up a RAID on their own websites for 14.04, but, at least I found out how to setup mdadm correctly.  The Ubuntu RAID sites, apparently, only work with 12.04 or previous versions (maybe).  I don't really care how mdadm works with older versions, since I want to use the latest LTS (14.04 as of this writing).

---

