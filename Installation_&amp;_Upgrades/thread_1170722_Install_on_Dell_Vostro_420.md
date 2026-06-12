---
title: "Install on Dell Vostro 420"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by Sonybuntu on 2009-05-26
I have 2 questions.

Question 1: Since I have a Dell, can I just download a Dell Ubuntu iso file and install it using that? After Googling, I found this link. [http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)

Question 2: I want to install ubuntu on a 2nd hard disk. I have no clue how to do so.

EDIT: I want to install it on a 2nd hard disk because I have Windows XP Pro on my 1st hard disk

---

### Post by lemming465 on 2009-05-30
> can I just download a Dell Ubuntu iso file and install it using that?
I don't see why not.  I'm not sure about Vostro 420's, but plain Ubuntu 9.04 installs OK for me on Vostro 220's.  The Dell page you referenced describes the pro's and con's fairly well.  If you care about Dell recovery partitions or something else they mentioned, feel free to use their image.

> I want to install ubuntu on a 2nd hard disk
At the disk partitioning step pick "manual", select the second disk, and make a new partition (ext3 or ext4) used as root (/).  You'll probably want a swap partition too; I usually go for 1-2 GB more than my memory size for swap.  It's OK to use the whole rest of the disk for root (/) if you want; more complicated setups are possible but usually only interesting on servers.  I can't remember if there is an easier option to automatically allocate partitions on a second drive. I have complicated multiboot systems and nearly always end up using the manual partitioning option, which definitely works for this, and isn't all that scary to use.

You'll have to figure out what your boot strategy is.  Simplest is to let Ubuntu take over the MBR; the Ubuntu boot menu will automatically include an option for booting the legacy XP install on the first disk.  This is what I do.  It's also possible to arrange for the XP boot loader to chain to an Ubuntu Grub loader installed directly on the second disk somewhere, but it's a bit more complicated to set up.

---

