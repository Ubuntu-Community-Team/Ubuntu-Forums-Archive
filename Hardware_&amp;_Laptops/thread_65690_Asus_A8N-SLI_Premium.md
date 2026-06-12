---
title: "Asus A8N-SLI Premium"
date: 2005-09-14
forum: Hardware &amp; Laptops
---

### Post by fujie on 2005-09-14
Hello,

I just bought a new mobo, cpu, ram, and video card.

Mobo: Asus A8N-SLI Premium (BIOS Version 1007)
CPU: AMD Athlon 64 3500
RAM: OCZ Dual Channel Kit 1 GB
Video Card: Gigabyte Nvidia Geforce 6600GT PCI-E 128 MB

My main problem is installing linux.  I tried to install Ubuntu Hoary Hedgehog 5.04 and my system freezes upon setting up packages during the final stages of installation.  The install gets past installing the base system and grub, reboots, then boots the kernel, and starts to setup packages then freezes.  I tried installing Debian Sarge 3.1 and the exact same thing happens, my system freezes upon setting up the packages.

When I reboot after a "freeze", my system usually hangs on the Mobo/BIOS splash screen.  I have to power down and then power on to get my system going again.

I had a working install of Windows XP at first, it seemed to work fine for a bit and then crapped out after trying the Debian install.

I am able to boot up with Knoppix just fine, everything seems to work with no freezes.  I'm no expert, but my best guesses are:

1) Mobo problem? - either my mobo is too new for linux stock kernel support, OR a manufacturing defect
2) Hard drive issue??? - I'm using a Maxtor 40 GB (about 4 years old), again, I dunno...

Should I try another distro? I dunno, Ubuntu is my favourite and I would really like to get it working on my brand new system. Any help, suggestions, comments are greatly appreciated.

Many Thanks,

Fuji

PS: I posted this to installation help as well, I hope that is okay.

---

### Post by mlomker on 2005-09-14
[QUOTE=fujie]Mobo: Asus A8N-SLI Premium (BIOS Version 1007)
[/QUOTE]

Is that the latest version?  Their website lists A8N-SLI Premium as V6.07.01 and I'm not sure how that translates to a 100x number.

---

### Post by fujie on 2005-09-14
I believe so, yes.

According to this link:
[http://support.asus.com/download/download.aspx?Type=All&model=A8N-SLI%20Premium](http://support.asus.com/download/download.aspx?Type=All&model=A8N-SLI%20Premium)

---

### Post by mlomker on 2005-09-15
My first thought was BIOS but you say that Knoppix runs fine.  hmm.  If it were me then I'd try the beta BIOS that they have on their website, just in case.  You can always revert to 1007 if it doesn't help.  I'd also go in there and shut off every port, feature, etc that isn't essential for getting a system installed (parallel, serial, firewire, USB, etc).

I'm betting you have a SATA drive and that's the next place that I'd look.  I know that drivers and whatnot for SATA are still a bit unstable in linux.

---

