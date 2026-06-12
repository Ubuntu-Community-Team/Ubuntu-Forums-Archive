---
title: "Uninstalling Ubuntu Completely"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by phroe on 2009-02-07
I have seen many removals for Grub, but I haven't found one that explains how to remove ubuntu completely if thats ALL you have installed, no other bootable or anything.  All i have installed in my laptop is Grub and ubuntu and now i do not want it, and cant remove it.

do you understand, i cant do fixmbr, because when i install the XP cd it says theres no HD located, (when entering in recover or whatever)

everyone else has another bootable os or something where they can delete and repair but not I.  all i have installed in my laptop is Ubuntu and cant remove, can someone please help me out, with this....

ONE MORE TIME...ALL I HAVE INSTALLED IS UBUNTU, SO DONT GIVE ME THE LINK THAT SHOWS HOW TO REMOVE IT AND THEN DELETE PARTITION, WHEN THERE IS OTHER OS'S INSTALLED!!!

thank u a MILLION!!!!

---

### Post by taurus on 2009-02-07
Why don't you boot your machine with Ubuntu LiveCD and use gparted (System -> Administration -> Partition Editor) and delete all the partitions on the harddrive.  Then, create a new partition that takes up the whole harddrive and format it to ntfs.  Now, windows should be able to read that harddrive/partition/or whatever.

---

### Post by yther on 2009-02-07
If your Windows XP CD won't recognize any HDDs, most likely (in my limited experience) it's because your drive is SATA and it needs a special driver.  You would need to find the driver for your hard drive, make a driver disk (usually a floppy) and then press F6 at the beginning of the XP installation so that it will prompt you to load the disk later.  It's a laptop, so... all I can say is good luck, if you don't have a floppy drive.  Try Google to see if you can find info on that procedure.  (Or see if your laptop has a BIOS setting to change the SATA mode; this can result in the drive being recognized as IDE, which means Windows will detect it when installing.)

---

### Post by phroe on 2009-02-07
Thanx...well ima try the ubuntucd live thingy ima look it up and c what it is your talking about...

thanks to the both you for the response...........
'

one

---

### Post by phroe on 2009-02-08
is ubuntucd live the same as an ubunutu install cd??? is it like a fix type cd???

---

### Post by taurus on 2009-02-08
Ubuntu desktop CD is the same as the LiveCD.

---

### Post by TheBig3 on 2009-02-18
Quick question... Have you overclocked anything since your Ubuntu install?  I had my system overclocked and it wouldn't recognize a new sata hard drive. Had to undo all the overclocking for it to recognize the drive.

Also, check you bios to see if it recognizes the drive there. If the bios doesn't see it, no OS will either.

---

### Post by jlaki on 2010-05-20
I had a similar problem with my Acer Aspire One D150.

Check if the bios has the menu for selecting SATA mode anywhere and change it to IDE if you want XP.

AHCI was the default for me and for some reason, Windows does not recognize it.

I was able to install and run Ubuntu in both SATA modes, but Windows only supported IDE mode.

One more reason to stick to Ubuntu.

Edit: Oh god, this topic is old...

---

### Post by wilee-nilee on 2010-05-20
> **jlaki said:**
> I had a similar problem with my Acer Aspire One D150.

Check if the bios has the menu for selecting SATA mode anywhere and change it to IDE if you want XP.

AHCI was the default for me and for some reason, Windows does not recognize it.

I was able to install and run Ubuntu in both SATA modes, but Windows only supported IDE mode.

One more reason to stick to Ubuntu.

Edit: Oh god, this topic is old...

You can get the acer recovery 3 cd discs that have the sata drivers in them if you want to install again, 20$ us.

---

