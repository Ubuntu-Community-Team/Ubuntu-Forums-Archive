---
title: "Partition adjustment mucked up Windows boot"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by geologic on 2009-09-19
I had a triple boot on a single hard drive, my partitions looked like this:

sda1: XP 64bit
sda2: XP 32bit
sda3: FAT32 data storage
EXTENDED PARTITIONS:
sda5: ext3 ubuntu 9.04
sda6: swap

I had grub, and all was working well. I could select ubuntu, or I would select the windows boot loader and then select which Windows partition I wanted to boot.

Since it's not fun having everything working nicely, I decided to boot off a LIveCD and use gparted to delete the XP 64bit partition (which I was no longer using) and then grow the XP 32bit partition. Well gparted did what it was suppose to do just fine.
BUT
now I cannot boot the XP 32 partition. I can access it fine from ubuntu, or the NTFS is fine, its something with the windows boot that has been funked up. I've tried booting into the the windows recovery console, and doing a fixboot and fixmbr, but this has not helped.

I should say at first the result of windows failing to boot was complaining about bootcfg missing, I added new boot.ini and corresponding files, which I found from a search on these forums. That then changed the error to corrupt or missing hal.dll. That's when I dropped in to the Windows Recovery Console, and rand fixboot/fixmbr and now I just get an empty blinking cursor when I try to boot Windows. I also tried bootcfg /scan (from windows recovery) which reports that it can't find the windows install and it may be corrupt. I ran chkdsk, and this reported no errors.

I'm not sure what to try next. I'm wondering if the problem has something to do between a 64bit/32bit Windows OS. It seems Windows just doesnt see that there is an installation present. I don't know if there would be a way to reinstall just the parts of the OS relevant for booting.

I think I can recover any relevant data, so a reinstall isnt out of the question, but I'd like to see if there's a way to save this.

---

### Post by AmerNewbieInDE on 2009-09-19
after you deleted your 64 partition, did you expand 32 partition? so now, instead of being your second partition, your 32 partition is now actually your first partition. confusing?? yea to me too.. lol, if you are using grub to boot everything, edit your menu.lst file, pointing your 32 partition to the first partition and not the second.. ex.. change (hd0,1) to (hd0,0)

---

### Post by geologic on 2009-09-21
I wound up mucking things up even worse, and finally just did a reinstall. But for the sake of following up:
Since I had 2 windows installs, GRUB just pointed to the first windows, and then I let the windows boot loader give me the option of which xp to boot.
So as far as I could tell grub was always pointing to (hd0,0) where the first windows was located. But since this windows was deleted -- and new one was moved into hd0,0 (sda1) i think this caused some confusion on the windows side of things.
I guess this will just go down as one of those problems I never figured out...

---

