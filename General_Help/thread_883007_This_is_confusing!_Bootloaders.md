---
title: "This is confusing! Bootloaders?"
date: 2008-08-07
forum: General Help
---

### Post by benign on 2008-08-07
I made a bootable USB drive, but didn't put a bootloader on it. I put a remastered distro on it, and tried booting it from the grub console, which works. I ended up editing menu.lst to show this:

title 		USB Drive
root 		(hd1,0)
kernel 		/casper/vmlinuz boot=casper quiet splash
initrd 		/casper/initrd.gz

That works as long as I don't tell the BIOS to boot from USB. If I do that, then I have to play around with the drive/partition number and sometimes get invalid readings (it seems very random).

I tried doing a "grub-install /dev/sdf1" on it after a --recheck, but that didn't do anything.

How can I make my drive boot up on it's own without the help of the GRUB on my internal drive?

---

### Post by caljohnsmith on 2008-08-07
Benign, I think that /dev/sdf1 is probably a partition on your sdf drive, so to get Grub installed on your USB HDD's master boot record (MBR), you would boot into your USB HDD, and run the following:
```
sudo grub-install /dev/[COLOR="Blue"]sdf[/COLOR] --recheck
```
That installs Grub to the MBR of your USB HDD, and it also creates its configuration files in the distro in which you run that command. The only thing that command won't do is create a menu.lst, which you can do with the update-grub command if you like.

---

### Post by benign on 2008-08-07
Thanks for the reply. It turns out that I forgot that I had actually started over with the drive after not loading grub right the first time, so grub wasn't actually installed this time! heh.

I have it working now for my purposes. This time I just ran "grub" from my main install instead "of grub-install" and used "setup (hd1)" after verifying drives with "find" to make sure I wasn't about to mess up my internal drive... which worked, so what your saying about identifying the partition is probably why it didn't work last time.

---

