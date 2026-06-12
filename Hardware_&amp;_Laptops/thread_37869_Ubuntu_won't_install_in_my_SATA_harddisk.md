---
title: "Ubuntu won't install in my SATA harddisk"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by tseliot on 2005-05-29
Hi folks, today I've bought a brand new computer "Compaq presario sr1429". My harddisk is a 160gb seagate serial ata and my motherboard "Ati radeon xpress 200p". I can't install ubuntu (the CD installer boots, and my CD drive is recognised) as it doesn't find "any partitionable media" for the installation (the HD) . I've been reading around  a few several methods to make ubuntu work on SATA. I can't set my bios the way I wanted (I think it's idiot-proof).

Are there any other methods you know?

Thanks in advance.

P.S. If I can't install it now I'll use Xandros for a while (but eventually I'll go back to Ubuntu, once the problem is fixed)

---

### Post by tseliot on 2005-05-29
Doh! Well, Xandros is not compatible with SATA installation...

---

### Post by tseliot on 2005-05-29
Mandrake doesn't work. I'll try Fedora and Ubuntu Breeze. I need a good distro which supports my serial ATA disk (and controller) in order to get rid of winslows until I buy an additional IDE harddisk and install ubuntu there (so as to solve the problem with Ubuntu permanently).

Could you recommend me a good distro which support Serial ATA harddisks out of the box, please?

---

### Post by tseliot on 2005-05-30
This is the model of my motherboard: RS480M2.

I also tried to install Mandriva 2005 LE, it installs the serial Ata drivers for my motherboard but then it hangs and it is impossible to continue the installation process of Mandriva.

---

### Post by spartus4 on 2005-05-31
The reason it will not install is because libata does not yet support your chipset.  Since this is the case none of the current distros will have support for it.

---

### Post by tseliot on 2005-06-04
[QUOTE=spartus4]The reason it will not install is because libata does not yet support your chipset.  Since this is the case none of the current distros will have support for it.[/QUOTE]

Well there's only one distro which supports and sees my SATA harddrive. It's Mandriva LE (ONLY the AMD 64 version). I installed it and then it freezes while booting (wow...).

I've bought an IDE harddisk. I've installed (several) distros 20 times in a week. Then I found out the problems I had in Ubuntu (on the IDE drive) (the mouse freezed very often when using application) was due to the fact that Ubuntu sees only 800MB of RAM out of my 2GB, I have to update the kernel  ](*,)

---

