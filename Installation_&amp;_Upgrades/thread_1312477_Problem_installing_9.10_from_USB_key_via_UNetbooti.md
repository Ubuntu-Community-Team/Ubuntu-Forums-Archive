---
title: "Problem installing 9.10 from USB key via UNetbootin"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by rkent on 2009-11-03
I'm having a problem installing 9.10 from a USB key.  The frustrating thing is it (mostly) worked the first time, but promptly stopped working on subsequent tries.

Since I have no CD/DVD drive I'm trying to install from USB.  Never having done this before I poked around online a bit and found UNetbootin.  I had already downloaded the 9.10 ISO and so I just wrote it to the (Cruzer u3) memory stick.  I checked my BIOS and it is capable of booting from USB.

The first install partly worked, but it had various problems (i.e., random freezes in first 30 seconds of operation) so I decided to downgrade to 9.04.  Unfortunately I deleted my 9.10 partitions on the HD at this point

So I downloaded that archive and tried to install it on my memory stick with Unetbootin, but this time I get a BIOS error "reboot and select proper boot device" whenever the USB drive is selected for boot.  This confused me; why would I be able to install 9.10 from USB but not 9.04?

I decided then to try and re-install 9.10 from Unetbootin, just to get the HD set up if nothing else, but this time it STILL wouldn't work - same BIOS error about no proper boot device.

What is going on here??  Is my USB key ruined somehow?  Can you only install Unetbootin once on any given USB key?  Why did the installer work once but not anymore?  What have I done wrong?


Details:
Foxconn R10-S4 barebones system (Atom 330 / Intel 945 / 2GB Crucial memory / 320GB WD drive / no optical drive)
Trying to install desktop-64bit version
I also have "staging" computers, one running Hardy and one running XP, so I can download any utilities compatible with either of those platforms.

---

### Post by perineal_sponge on 2009-11-03
If your BIOS is not recognizing the USB disk a bootable then therein lies the problem - there is a "boot" flag set when writing the disk image that lets the BIOS know it can boot from it... I'm guessing that this has been wiped somehow or the disk has become corrupted. I'd start wipe the USB disk and start again with unetbootin / 9.10... you can check using gparted that the USB disk is formatted with a bootable flag.

---

### Post by rkent on 2009-11-03
Right... thanks for that.  Since my last post I've gone ahead and wiped out the read-only isofs partition that comes on all Cruzer U3 devices.  So far that has not solved my problem.

Other than re-writing a bootable image yet again with Unetbootin, is there another way to set the bootable flag on this USB device??


> **perineal_sponge said:**
> If your BIOS is not recognizing the USB disk a bootable then therein lies the problem - there is a "boot" flag set when writing the disk image that lets the BIOS know it can boot from it... I'm guessing that this has been wiped somehow or the disk has become corrupted. I'd start wipe the USB disk and start again with unetbootin / 9.10... you can check using gparted that the USB disk is formatted with a bootable flag.

---

### Post by OriginalName on 2009-11-03
I think you can re-set the boot flag from the partition editor... probably will need to reformat the disk though. I'd do this then re-write the boot image from unetbootin... also check you've latest version of ynetbootin with 9.10 support.

---

### Post by rkent on 2009-11-03
thanks again.  So far I have repartitioned with cfdisk in Linux, tagged as "bootable" there, formatted in FAT (16, not 32), and used the Windows edition of Unetbootin to write the 9.04 image to my USB drive.  I'm using the very latest version of Unetbootin as I just downloaded it tonight.  Still no love.

Can anyone help boot via USB on the configuration mentioned above??  I have no idea how it worked once earlier, I have tried rebooting about 20 more times and it gives me the "reboot and select proper boot device" error every single time.

---

### Post by rkent on 2009-11-03
Ah!  In AMI-Bios 8 (at least on the Foxconn R10-S4 system) you need to turn on "Forced FDD" emulation of USB devices for this to work.  

How very intuitive.


> **rkent said:**
> thanks again.  So far I have repartitioned with cfdisk in Linux, tagged as "bootable" there, formatted in FAT (16, not 32), and used the Windows edition of Unetbootin to write the 9.04 image to my USB drive.  I'm using the very latest version of Unetbootin as I just downloaded it tonight.  Still no love.

Can anyone help boot via USB on the configuration mentioned above??  I have no idea how it worked once earlier, I have tried rebooting about 20 more times and it gives me the "reboot and select proper boot device" error every single time.

---

