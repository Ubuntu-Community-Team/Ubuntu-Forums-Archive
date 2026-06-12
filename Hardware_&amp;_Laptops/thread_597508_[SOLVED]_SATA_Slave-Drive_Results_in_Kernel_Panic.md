---
title: "[SOLVED] SATA Slave-Drive Results in Kernel Panic"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by Therion on 2007-10-30
I have dual hard drives on my system: a 200GB Maxtor SATA and a 120GB WD PATA.  When I installed Gutsy I physically disconnected the SATA drive that contains  my WinXP Pro install and installed Gutsy on the secondary, PATA hard drive (Gutsy on PATA, Windows XP on SATA).  The Gutsy drive is set as Master, the Window drive is set as primary Slave.

Everything is peachy with Gutsy as long as I leave the SATA drive physically disconnected.  If I connect it, I can go for one, maaaaybe two reboots before I start getting a Kernel Panic error which leads to the system freezing.

When the SATA drive is connected, and I don't get a Kernel Panic, all is well.  I can access the SATA drive just fine - full read/write access.  It's great!!  But again, after a couple reboots, the Kernel Panic returns and nothing will get me up and running except physically disconnecting the SATA drive.  Also (not sure if it matters) but it seems to take a lot longer to boot with the SATA drive connected -- even if there's no Kernel Panic.  Gutsy just plain boots faster when the SATA drive is not connected.

Any suggestions mucho appreciated.  Forums search turns up nothing specifically related, nor does Google.

---

### Post by dabl on 2007-10-30
Mix 'n match IDE/PATA and SATA drives are a known hazardous situation.  I spent about 3 days, when I first installed Edgy, proving beyond all doubt that there was nfw to make Grub go to the first SATA drive while Win XP was installed on the IDE/PATA drive on the same system.  It simply won't do it.  In the world of the Ubuntu installer, IDE drives take precedence -- especially if they have a bootable partition already set up.

I know that Windows requires the "boot" flag to be set on its drive, and I also know that BIOS recognizes such "bootable" flagged partitions.  I fear that your Linux is picking up on the BIOS recognition and "seeing" that bootable partition as something that it needs to do something with.  So, I think you have an "unnatural" combination there, by setting the drive with the bootable flagged partition as "slave" -- I think BIOS doesn't quite buy it, and therefore neither does Ubuntu.

You didn't want to hear this, but life would be far simpler if you could install Windows on that IDE drive, install Ubuntu on the SATA drive, and let Grub write itself to the MBR on the IDE drive.  That's the natural order of things, today.  If you don't want to do that, here is what I ended up doing, which also worked:

1. FDISK the IDE drive, but don't format it, and leave it connected.
2. Install Win XP on the SATA drive.
3. Install Ubuntu on the IDE drive, and let it write Grub to the MBR on the SATA drive.

Good luck with it!  :)

---

### Post by Therion on 2007-10-30
> **dabl said:**
> You didn't want to hear this, but life would be far simpler if you could install Windows on that IDE drive, install Ubuntu on the SATA drive, and let Grub write itself to the MBR on the IDE drive. ... 
AHHHH HAHAHAHAHAHAHAHAHA... Great!!  Just great!!  You're trying to kill what, a week of my time?  Just kidding.  But you're right, that's not exactly the answer I was hoping for.

[quote=dabl] If you don't want to do that, here is what I ended up doing, which also worked:

1. FDISK the IDE drive, but don't format it, and leave it connected.
2. Install Win XP on the SATA drive.
3. Install Ubuntu on the IDE drive, and let it write Grub to the MBR on the SATA drive.[/QUOTE]
Okay... so, in short then, I can pick between:

Option 1.  A hot poker in the eye, 
[INDENT]or...[/INDENT]
Option 2.  A swift kick in the family jewels.

Niiiiiiiice!!!

Ah well... such is life.  Thanks for your input.  I'm actually finding myself tempted to go ahead and reformat and reinstall both, putting XP on the IDE drive and Gutsy on the SATA.  For as little as I'm using Windows for these days, what the heck?  Or maybe I'm just a glutton for punishment...

Thanks again, dab', appreciate the input even if it's not what I was hoping for!

---

### Post by dabl on 2007-10-30
Call the first installation "practice".

:lolflag:

---

