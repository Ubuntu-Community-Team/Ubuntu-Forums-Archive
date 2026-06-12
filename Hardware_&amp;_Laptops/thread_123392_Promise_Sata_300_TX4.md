---
title: "Promise Sata 300 TX4"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by keebler411 on 2006-01-29
I've been struggling with sata for almost a week now.  I can't beleive its this hard.  Well anyway I got a Promise Sata 300 TX4 card and am trying to make it work under some sort of Debian system.  I really don't want to go back to RedHat but I will if I can't get the controller to work.

According to the linux mafia webpage [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html) this controller should work.  Quote:

(link) Promise PDC40718-chip-based SATA300 TX4 SATA-II chipset &#8212; fakeraid. Supported by libata's sata_promise driver as of 2005-04-15. Alternatively, use the manufacturer's GPLed driver code.

I don't want to use raid I just want to access the disk.  I've already tried the following:

1) Installed Debian 3.1 with kernel 2.6.8.x  Does not detect controller.
2) Okay maybe kernel is too old.  Upgraded to 2.6.15.1 from kernel.org.  It worked but caused major system instability.  Could not find any apt packages with newer kernels.
3) Reinstalled Debian 3.1 with 2.4 series kernel and compiled driver from promise.  Compile worked okay but could not get module to insert without unresolved symbol errors.
4) Booted with Ubuntu Live 5.10.  Did not detect sata controller or it seems my secondary IDE drive.  I tried modprobe sata_promise.  No luck.  I think all other needed scsi drivers were loaded as my external usb drive was detected at boot.

I saw in another thread that someone has gotten this card to work but didn't post any details.  Any help would be greatly appreciated.  Thanks

Keeb :cry:

---

### Post by Teroedni on 2006-01-30
Could you try a ubuntu5.10 Install?
IIt should work better than the live version
Ubuntu install usually finds all devices

---

### Post by keebler411 on 2006-01-30
Thanks.  I already tried that.  No luck.  I just don't get the whole sata thing at all.  I've never had problems making other hardware like cameras etc work.  Most references I see to sata problems seem to assume the controller is recognized and the problem is raid.  I don't care about raid right now.

Keeb

---

### Post by keebler411 on 2006-02-02
Well it seems I got it to work under ubuntu 5.10 a couple days ago.  I've been waiting to see if its stable before I replied with the solution. 

Short answer solution:

1) you MUST have the right software/source installed to compile a kernel for your distribution
2) d/l the appropriate driver from promise and follow the instructions in the readme to compile the driver

One point though worth mentioning now is since step 2 requires that you compile your kernel you might want to copy the config from /boot to the kernel source directory so you don't have to guess at the options.  However I made my own customized monolithic kernel.

I'll post a more detailed solution when I've ironed out a few little details.  Since I'm relatively new at this I don't want to post anything detailed before I'm sure I'm right.

Keeb

---

### Post by Teroedni on 2006-02-02
Im glad you make it work:D


A installation instruction would be very welcome
Thanks :)

---

### Post by keebler411 on 2006-02-06
The howto I posted has all the details:

[http://www.ubuntuforums.org/showthread.php?t=126199](http://www.ubuntuforums.org/showthread.php?t=126199)

keeb

---

