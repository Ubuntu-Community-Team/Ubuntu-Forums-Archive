---
title: "Dual Boot Install onto SATA drive"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by mgchan on 2006-01-09
I've got a Serial ATA drive acting as C: (running Windows XP) along with an IDE drive (D:) for storage, connected to the first IDE channel.  Currently Windows is booting up off the SATA drive.  I'd like to install ubuntu onto either drive.  Currently, ubuntu setup sees my IDE drive as drive #1 and SATA drive as #2.

Yesterday I tried installing onto a partition on the end of my D drive simply because it has more space.  Using the default install of grub, my computer simply ignored grub and went straight to Windows.  I figured this was because it installed grub onto the IDE drive, so I re-installed and told grub to install to /dev/sda1.  This messed up the boot record, giving me a "GRUB Geom Error", and after some panicking I figured out that "fixboot" would fix my MBR.  

So I figured I'd try installing onto my SATA drive, but when I did that and allowed the default grub install my computer again ignored it.  What would be the correct way to set this up?

---

### Post by Kipper on 2006-01-10
Welcome to the wonderful whacky world of dual-boot systesm. Joking aside, what I think has happened is that when you installed Ubuntu and the GRUB bootloader on your IDE drive you simply forgot, or didn't realise you needed to make your IDE drive tha first boot drive in your BIOS. As your system was still set to boot from the SATA drive that's exactly what it did. Hey presto, Linux seemed to have disappeared.

Installing Ubunutu and GRUB on your SATA drive has generated a problem which I think relates to the SATA controller. A quick "google" of "GRUB geom error" will show you lots of posts on that subject.

I would say install linux on your PATA drive attached to the IDE controller, change the boot order of the drives in your BIOS and away you go. 

Post-install you may not see a Windows entry or be able to boot to Windows from GRUB first time. Don't worry, you just need to edit the "menu.lst" file that GRUB uses at boot time.

This should sort it:

title Windows XP
rootnoverify (hd1,0)
hide (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

Hope that helps.

---

