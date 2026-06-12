---
title: "Dual Boot on a USB Flash Drive"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by Mig Daddy on 2009-03-04
I have recently come across a bootable 2gb USB flash drive.  I have already used it to boot and install Intrepid.  I am a long time Windows user and fairly new to Linux and GRUB, but here's what I want to do:

I want to dual boot BartPE and a live version of Linux (identical to an ISO image of a distro like Unetbootin would create) from the UFD.  I have done whatever research I could online, but am still unsure how to approach it.

I am planning to create 3 separate partitions: an active GRUB partition, a BartPE partition, and a live Ubuntu partition.  The reason being I want to be able to modify, delete, and completely replace the Linux partition.  It would be mainly used to install one or more distros of Linux one at a time.  I would like the boot loader and BartPE to be undisturbed in such cases.

I understand I would have to customize the menu.lst file.  So here are my questions.

1) Is this 3 partition scheme possible on a UFD?
2) I assume the BartPE partition would have to be chainloaded, but is it necessary for the Linux Partition?
3) Is making the GRUB partition active via Gparted and removing any active flags from the other partitions be sufficient for creating a stable boot system?

---

