---
title: "Installation oddities with harddrives"
date: 2009-01-30
forum: Hardware
---

### Post by coldsteel2001 on 2009-01-30
Hi. I'm not new to the linux scene, but i'm still not yet experienced enough imho.
I've had to reinstall Ubuntu 8.04 (due to miscellanious reasons of breaking every system on my last installation) and I've run into an odd problem.
Basically every ide harddrive I have is read as /dev/sd(a,b etc). I know they're an IDE drive a piece, I built the machine...yet they're detected as SCSI or to some extent similar.
Back on track...after installation I remove the disc and reboot...it can't find the boot loader and stops with "DISK FAILURE: PLEASE INSERT SYSTEM DISK" or similar boot error.

I reinsert the disc and load into ubuntu live cd and run partion editor (GParted). I check the boot flags.../dev/sda1 has been set to boot (boot been the only flag set). So I reboot with the disc removed. Same error yet again. I even tried reinstalling windows 2000 and that wouldn't boot either.

The only way I can get my Ubuntu installation to boot is by leaving my windows 2000 install disc in the drive, so I may boot at all times.

Can I get some help here please? I don't even know why this happens, it's never happened with any other distro I've installed on other machines before (well except Debian, but that WAS my fault).

Thanks](*,)

---

### Post by electrogeist on 2009-01-30
It sounds like the boot device order may not be correct in the BIOS settings.  If you moved any hardware around or unplugged/replugged a drive it might change on its own.

If you have hard drives on multiple controllers that can complicate things further... sometimes the install will see drives being in a different order (one controller before the other) than the order they are in at POST when you reboot.  To be honest with you I feel more comfortable dealing with that situation using the LILO bootloader vs GRUB which is much more common nowadays.  So if you have multiple controllers that may be the issue, and I'll leave it to you to read up on GRUB

IDE drives now show up as /dev/sd_

---

### Post by dabl on 2009-01-30
> **coldsteel2001 said:**
> 

Basically every ide harddrive I have is read as /dev/sd(a,b etc). 



Yep, that's as expected.  All hdds are /dev/sdx for over two years now, with the libata driver.

> 

I know they're an IDE drive a piece, I built the machine...yet they're detected as SCSI or to some extent similar.



No, the "s" in "sda" has no such significance any more.

> 

Back on track...after installation I remove the disc and reboot...it can't find the boot loader and stops with "DISK FAILURE: PLEASE INSERT SYSTEM DISK" or similar boot error.



That's coming from a Windows boot loader. Did you make a Linux partition, and format it ext3?  Did you allow the Grub bootloader to be installed?  If not, you're doomed to use the Windows bootloader, I guess.  Here's information that might help:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by coldsteel2001 on 2009-02-12
No I did a reformat and reinstall and allowed grub to be installed, but I find grub doesn't work unless my windows 2000 cd is in the drive...
I'll have a go later on with lilo and see if that fixes all the problems.

I've never had issues with grub in the past, especially when I tried out Linux Mint and Debian Etch.

I had much better luck installing hardy heron onto my laptop, grub did its job fine and I can duel boot XP and Ubuntu yay! No fussing around with the installation...even made sure I had a 1Gb swap partition just incase I needed it...it hardly even touches it.

Thanks for the help guys, I'll try your advice out soon.

Ah just realised, I never know the driver changed lol. It was just something I noticed from using Debian Etch and swapping to Hardy Heron.

---

### Post by coldsteel2001 on 2009-02-22
Well I tried lilo and it doesn't even work, I even configured it to boot my primary partiton (/dev/sda1) but that didn't work. I've tried reconfiguring grub on sda1 in ubuntu and also tried the same method off the livecd option on ubuntu 8.04...nothing...
I'm not sure what to do other than reformat the drive and start again...
I originally formatted it as ext2, like I did on my laptop with no worries (both installed the grub bootloader). I never opted to use ext3 as the primary partition sits on a 8Gb drive...I suppose I should've used ext3 for the file speeds it has...would explain why binaries execute a bit slow.
So yeah, I've messed around with grub and lilo configurations to get it going but the damn machine refuses to boot off the drive without some form of windows boot loader present (my windows 2000 cd). I even reset my bios to see if there was any problems there...no luck. I have a third hdd present in the machine, but my ide cable can only run 2 of them lol...might see if i got one spare that can run all of them.

I'm at a complete loss at what to do, so I might swap my 8Gb for my spare 6Gb and have a go with that after I've backed up all my files. Is it possible for me to install ubuntu on my spare hdd if its setup as sd0 and still keep my user area on sdb1 (/home/username) if i mount sdb at /home?

---

### Post by coldsteel2001 on 2009-02-22
Actually don't worry about it I found out what the problem was lol...I just had to remove the power cable for 12 seconds...after all that bios was confused lol.
Guess I shouldn't have perminantly left it to boot off cdrom drive first then try the hdd.
Thanks for your help guys, it was really appreciated. Can't believe it was the bios.

---

