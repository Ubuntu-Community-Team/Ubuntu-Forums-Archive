---
title: "Sata Dvd-rw  - No Boot!"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by kubug on 2008-01-14
Hi folks,

here is an odd one: I recently got myself a new motherboard (P35 Chipset) from Gigabyte. All I changed was the mobo+CPU+RAM. 

I used to use my SATA DVD drive without a problem and in fact installed Gutsy just fine. Just the other day it started to not wanting to boot, telling me something about ata3: could not fix speed something-rather, and ended the boot there. 

I kept trying to reboot and nothing. All of a sudden it would boot. And then nothing for the next few times. After trying to change some settings in the BIOS (no luck) and adding the irqpoll-fix in grub (still no go) I decided to pull the plug on the DVD-Drive and voila ... we are booting up! I then plugged the drive back in once Gutsy was booted (all new SATA have hotplug support... or at least in theory).
This way I can use my drive just fine.

Who would have thought that the DVD-Drive is stopping it from booting? How can I fix this? Is this a kernel issue?

---

### Post by kubug on 2008-01-16
Here is what I get at boot up:

ata3.00: failed to set xfermode (err_mask=0x4)
ara3:COMRESET failed (errno=-16)
Buffer I/O error on device sda3, logocal block 87891552
Buffer I/O error on device sda3, logocal block 87891553
Buffer I/O error on device sda3, logocal block 87891552
Buffer I/O error on device sda3, logocal block 87891553
Buffer I/O error on device sda3, logocal block 87891610
Buffer I/O error on device sda3, logocal block 87891611
Buffer I/O error on device sda3, logocal block 87891610
Buffer I/O error on device sda3, logocal block 87891611

---

### Post by kubug on 2008-01-16
Ok, something else is wierd.
It seems that when I put a CD into the drive the chances of it booting up are much better. Once it doesn't boot, I take the CD out and back in, and it will boot the next time.

Wierd, no?

---

### Post by kubug on 2008-01-19
Ok... another update... not putting in a CD didn't work anymore. I rebooted 10 times and no go.

But, I do have a Gigabyte P35-DS3R, and it has 8 SATA Ports. 6 on the Intel Chipset and another 2 on a different one (I forget which one). So I moved the DVD drive from the Intel to the one of the other 2 and it seems to work now. 

Hope this may help someone else.

---

### Post by sml on 2008-02-02
Same problem for me with an Intel P35 board.

Very strange. Sometimes it boots and sometimes it crashes with LinuxMint 4.0.

Sata hard-disks are on the JMicron with AHCI.
DVD/CD is on the Intel ICH9. Tried numerous options .. native, legacy, ahci, ide etc etc.

Tried to boot live CDs:
Debian 4.0 r2 i386 - No Boot
Ubuntu Hardy Aplha 4 i386 - No problems
gOS 2.0.0 Beta 1 - No Boot

---

### Post by kubug on 2008-02-17
Ok, latest issues are that it won't finish a CD/DVD burn...  it will always stop with an error. Sometimes the CD's are useable but usually the end is missing. 

I hope hardy will fix this, like the last post hinted toward.

---

