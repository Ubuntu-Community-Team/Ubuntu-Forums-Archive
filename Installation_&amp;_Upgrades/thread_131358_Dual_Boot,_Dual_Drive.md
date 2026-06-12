---
title: "Dual Boot, Dual Drive"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by moore.bryan on 2006-02-16
i've scoured the internet, but no process has worked.  i had hoary working fine, but can't remember how i set it up.  i have two drives on a dell; hda is xp and i want hdb for breezy.  hda1 is ntfs (~38gb), hda2 is fat32 (~150mb), hda5 freespace (~50mb).  as i was installing breezy, i set up hdb1 as ext2 root (~30gb) and hdb2 as swap (~500mb).  when it got to grub/lilo, i've tried both, installing them onto the root partition of hdb1.  i then do the whole "dd if=/dev/hdb1 of=grub.bin (or lilo.bin) bs=512 count=1" thing (through knoppix), copied the file to hda2, and pointed my boot.ini to that file by adding "U:\grub.bin(or lilo.bin)='Ubuntu'"... nothing!  it hasn't worked.  i've read such great things about grub, but i had trouble setting it up last time and i seem to remember lilo working for me better.  i've tried so many different suggestions, i'm almost at wit's end; help!  i'm seriously looking at getting rid of xp, but i first want to get accustomed to ubuntu and all of my technophile friends have said it's the best.

---

### Post by mdsmith on 2006-02-16
I don't know if this will help, but I have been using 2 drives for dual booting a long time with Mandrake, Vector and now Ubuntu and I never set the boot up. I just let the installer do it and install in the MBR (Thats hdba first sector) and it just always works correctly. My current system has win98 and ubuntu on hda and mandriva on hdb. Have never had a problem with how the instller does it. Don

---

### Post by moore.bryan on 2006-02-17
mdsmith... when i install onto hda mbr, nothing boots.  i use knoppix to get into a terminal, gedit my menu.lst to point to the correct boot path for grub (h0,0), restart, and then it sticks at "grub>"... the last time i had it working (xp on hda and hoary on hdb) it took me 6 months to figure out how to rubengolderberg it and now i can't remember how i did it.  thanks, anyway.

---

### Post by schdefan on 2006-02-17
your configuration in menu.lst for the root partition of ubuntu system as to be
(hd1,0) for hdb1 not (hd0,0)

and you have to insall grub in the MBR. But you already did it, didn't you?
schdefan

---

### Post by moore.bryan on 2006-02-18
schdefan... i tried every config possible in menu.lst and grubbed my mbr.  i've since given up on the dual boot, dual disk idea... ubuntu just isn't friendly with it.  instead, i resized my xp partition and put ubuntu on the same disk; booting fine now.  my new issue is getting my smartlink 1801 (linmodem) internal modem to work... no luck so far.

---

### Post by schdefan on 2006-02-19
For internal hardware on PCI-bus I recommand you to follow the link that I posted in the hardware section.
[http://ubuntuforums.org/showthread.php?t=129957&highlight=schdefan]("http://ubuntuforums.org/showthread.php?t=129957&highlight=schdefan")

You will find the module you need for your modem.

---

### Post by moore.bryan on 2006-04-26
*i've tried and tried, but to no avail.  i finally gave up on the dual-drive, dual-boot idea and just installed ubuntu onto my hda, using hdb for swap.  loving ubuntu and almost completely switched out of xp.  thanks to all of the community members who tried to help out.*

---

