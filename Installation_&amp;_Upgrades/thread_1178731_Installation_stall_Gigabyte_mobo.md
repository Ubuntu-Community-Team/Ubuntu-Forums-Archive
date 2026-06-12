---
title: "Installation stall Gigabyte mobo"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by jmerkin on 2009-06-04
Hi all

I am trying to install some *nix on a box I built yesterday. I've tried Kubuntu, Lenny, a Lenny custom backport I was recommended, Mandriva. No dice.

First, parts:
Gigabyte GA-MA790X-UD4P
AMD Phenom II X3
Western Digital Caviar Black SATA

The gigabyte mobo has both an AMD S750 and Gigabyte SATAII controller. 

My issue:
It always stalls, saying "ata1: softreset failed (device not ready)" or something about not being able find the DMA, depending on which distro I'm trying to install. Both errors seem to be an issue with the SATA HD.

This seems to me an issue with the SATA controller or drivers. I don't think it's an issue with the setup, as I used the Ultimate Boot Disk and modified the partition on it, changing it to Ext2/3 and to FAT32, just to change things up. No problem there.

Some deep googling found [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392/ata1"). They suggest that there is an issue with one of the controllers being compatible. I disabled it in the BIOS, no luck. Switched the disabled one (and the connection), no luck. I tried a number of kernel options that I found and that were suggested to me, including all_generic_ide, ide=nodma, acpi=off, noapic, nolapic. No difference.

Ideas?

edit: I just ran a Western Digital quick media test on it from the Ultimate Book Disk and it came back fine. I am currently running the full media scan, but that has 1.5 hours remaining. The quick scan came back without errors.

---

