---
title: "reinstalling after a format"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by Shooree on 2009-03-21
Couldn't get my Acer 5920G stuff to work fully with the previous install of Xubuntu 8.10, so decided to reinstall since I'm a newb and probably messed up some important files while I was working on trying to fix those issues (hibernation mostly).

So, I stupidly merge the linux partition with an attempt at linux swap partition 2GB in size. (done from windows vista, which is on a partition of its own. realized I was making a HUGE mistake only when it was done). when it was done GRUB said that the file system check (or something) failed in auto mode, and that I sould do it manually. So I end up having to hold "y" for half an hour while it tried to reconfigure all the nodes and stuff I somehow messed up by joining the two partitions. 
Unable to wait, I restart and log on to Vista. I format the entire linux partition, thinking that I'll boot from the xubuntu cd and reinstall everything.

But now, regardless of what order my boot sequence is in, I just get the horrible>
GRUB Loading, please wait...
ERROR 15

at which point I can only restart. Please provide advice as to how to at least get to my windows partition and install xubuntu from there again. Thanks and sorry for the long post.

---

### Post by Shooree on 2009-03-21
Just tried a Vista bootable CD. It diagnoses no problems with my Vista config.

As I see it, this GRUB thing just stands in the way of windows' own boot manager, and since it has no data to load is stuck like that. How do I turn it off or uninstall. I need to get to Vista in order for the Xubuntu Install CD to work.

Setting BIOS to boot from CD doesnt solve it, since it ignores the Xubuntu one, if it wasn't clear from what I said above. Can I download something and use an USB drive to fix this perhaps?

EDIT: I'm redeownloading Xubuntu, as it still refuses to boot from the CD I burned it to previously. Trying hard to understand why it won't. Is it possible that it's JUST regular Ubuntu that can do the LiveCD boot thing, and Xubuntu can't?

---

### Post by coffeecat on 2009-03-21
> **Shooree said:**
> I format the entire linux partition

Oops. That's where you went wrong. Quick explanation. Stage 1 of grub occupies the first 400 or so bytes of the HD, exactly the same place the Windows MBR goes, because there's no place else it can go. I.e. stage 1 overwrites the Windows MBR.

> **Shooree said:**
> As I see it, this GRUB thing just stands in the way of windows' own boot manager

Er, yes, true, but that's how it's designed. Just try booting Linux from the Windows boot manager. It can be done, but.... :( :roll:

Anyway, Grub stage 1 calls stage 1.5 which is an otherwise unused part of the HD just after the partition table. Stage 1.5 calls grub stage 2 which (along with the grub menu.lst configuration file) is in the /boot/grub directory of your Linux root partition. Reformat your root partition and... You get the picture.

Here's what to do.

1 Repair the Windows mbr. With XP, you used the install CD and issued the FIXMBR command from the repair terminal. I don't know whether that's true of Vista, but a search of these forums should help. (I have no experience of Vista: neither do I intend to have any.) Then you'll be able to boot into Windows.

2 Reinstall whichever Ubuntu flavour you want. This will reinstall grub back to the mbr (and overwrite the Windows mbr).

Or just go straight to 2. The installer should pick up the presence of your Windows partition and set up a dual-boot menu for you.

**Edit:** saw your edit after I posted. There's no reason why the Xubuntu CD shouldn't boot up if the Ubuntu one does. Perhaps you had a bad burn or a corrupted download first time around. Once you've finished the download, don't forget to check the md5sum, and burn at a slow speed - say x4. It's more reliable that way.

---

### Post by Shooree on 2009-03-21
cheers. will try the new cd burn and see how it goes

EDIT: Yes! the new burn booted up properly. Damn,that was an unnecessary headache... cheers coffeecat, this cup's for you :)

---

