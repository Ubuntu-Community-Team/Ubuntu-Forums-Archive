---
title: "Adding Windows Recovery to Grub"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by orc_dragoon on 2009-11-09
For some reason the fedora grub didnt detect my windows recovery partition ( Im on a netbook ).

How would I go into adding that to grub.

Its on /dev/sda2

---

### Post by mechro on 2009-11-09
Is it a bootable Windows installation? Calling it "recovery" implies it's a back-up.

---

### Post by orc_dragoon on 2009-11-09
Its basicly a backup where if its ran it replaces the windows thats installed with whats on the partition.

---

### Post by rplantz on 2009-11-09
I have a laptop with Vista and a "hidden" partition that allows me to restore Vista if need be. I did not get a restore CD/DVD with my laptop.

The first time I installed Ubuntu it wrote over the master boot record with grub. I do not think there is any way to tell grub about the hidden partition, which meant I could not restore my Vista without getting a restore CD/DVD.

I found a disk image that I could download and burn to a CD that allowed me to reinstall the Vista boot loader. I had to search a bit to find out how to do this. I verified that I could boot into Vista again.

Then I reinstalled Ubuntu using the **advanced** option to install grub only on Ubuntu's partition, thus leaving Vista's boot loader.

Then I downloaded EasyBCD, which makes it very easy to add Ubuntu to Vista's boot loader menu.

When my system first boots, the Vista boot loader gives me the choice of booting into Vista or into Ubuntu. Plus, I can still use the "hidden" partition to restore Vista.

---

