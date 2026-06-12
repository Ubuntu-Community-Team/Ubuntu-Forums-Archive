---
title: "Installation Fails! Boot Questions"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Zapster on 2009-11-02
Hello everybody!

**Preamble:**
At the end of the last week I decided to upgrade from 9.04 to 9.10. Unfortunately the upgrade process failed because of some strange package manager errors (most properly because my hdd had 786445 bad sectors :shock:). 
So I decided to make a fresh installation (on a brand new hdd). 

**Problem:**
Now the real fun starts. I am using a 3 years old Sony Vaio Fe21m Laptop. I burned the ubuntu 9.10 iso using the internal cd/dvd writer and rebooted. First time the cd was not recognized and my pre installed WinXP started. The second reboot the ubuntu installation menu showed up. I started the installation process and boom I got an I/O error message (like some other posters claimed). I came the the conclusion that my internal disc drive can not read burned CDs (or DVDs) correctly. It does recognize all replicated discs.
So I prepared my 8GiB USB flash drive but unfortunately my bios does not support usb booting. I downloaded a boot disc from [http://plup.at](http://plup.at) to boot from my flash drive but the boot manager freezes if I select boot from usb (maybe because the boot manager disc is not correctly read by my drive).
Today a bought an external cd/dvd rw drive to give it another try. But, surprise, surprise, my bios can not boot from external drives. The external drive can read all discs burned by the internal drive but not the other way round.
So that is pretty much the status quo. 

**Summary:**
* I have a bad internal drive which is not capable of reading CD-RWs nor DVD-RWs correctly (but replicated discs)
* I have the a flash drive and an external CD/DVD writer but can not boot from these devices
* Currently there is no other computer available to set up an installation server

**Questions:**
* Is there the possibility to boot from another drive using the ubuntu live cd boot prompt? If so, how to do?
* Can anyone think of a network (I better say internet) installation method where no local server is required?
* Is it possible to copy the the copy the live cd files onto the hard disc an set up some MBR magic to start the installation from the hard disc? (That would be really cool 8-))
* Any other solutions?

**Not an option**
* I know that I can order free Ubuntu discs from Canonical but I can't wait 6-10 weeks.

* I will not buy a replacement drive for my vaio. They are overpriced and the the computer is too old to spend more money on it.

Thank you all in advanced! I've spend now more than 30 hours and 250€ on that issue an still no success :(.

br
Josef

---

### Post by Zapster on 2009-11-05
Ok, I found a solution :D
I made a netboot installation using super grub disk [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet](https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet) (note that super grub disk does not have the 'kernel' command. Use 'linux' instead.)
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Josef

---

