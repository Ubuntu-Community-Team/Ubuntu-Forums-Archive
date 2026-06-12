---
title: "DualBooting Ubuntu and XP"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by .:Justus:. on 2009-03-22
Well, my home OS is xubuntu 8.10 but i would like to install xp (nlited version) as well. I have XP bootable off of a flashdrive, but i have no clue how to install onto my hardrive  so that i can choose to boot either xp or xubuntu when i turn on the computer.
How do i go about doing this?

---

### Post by .:Justus:. on 2009-03-22
gparted won´t let me partition my hardrive either, it gives me an error without details.

---

### Post by upchucky on 2009-03-22
you can try partedit i have found that where gparted sometimes fails, partedit works instead.

you must have xp installed first, then install ubuntu, this is because windows is stoopit when it comes to dualbooting. it thinks it is a master supreme Os and nothing else should be on the drive.

you could use imaging software to create images of your working systems then restore the images to their respective partitions instead of reinstalling everything.

However since Windows is designed to slowly self destruct over an unknown period of time, it may be better to back up all data to a storage drive, the do a clean install of everything, remembering to install windows first, this lets you plan the partitions properly from scratch. remember to have a partition for your files in windows separate from the Os. and have a separate home partition and swap partiton for Ubuntu. This ensures a safer file storage scenario. Ubuntu swap is typically half the size of the available ram in the Pc.

---

### Post by .:Justus:. on 2009-03-22
> **upchucky said:**
> you can try partedit i have found that where gparted sometimes fails, partedit works instead.

you must have xp installed first, then install ubuntu, this is because windows is stoopit when it comes to dualbooting. it thinks it is a master supreme Os and nothing else should be on the drive.

you could use imaging software to create images of your working systems then restore the images to their respective partitions instead of reinstalling everything.

However since Windows is designed to slowly self destruct over an unknown period of time, it may be better to back up all data to a storage drive, the do a clean install of everything, remembering to install windows first, this lets you plan the partitions properly from scratch. remember to have a partition for your files in windows separate from the Os. and have a separate home partition and swap partiton for Ubuntu. This ensures a safer file storage scenario. Ubuntu swap is typically half the size of the available ram in the Pc.

Well the thing is, i´m sure its just some stupid error that can be fixed easily, and all i want to do is resize my drive so that i have 5 unused gigs which i can use to install xp on. And i dont want to go through such a big hassle when it should be working within minutes.

---

### Post by upchucky on 2009-03-22
if you already have ubuntu and you want to install xp to the same drive on a different partition, then you are gonna have to either reinstall everything or make restore-able images, this is due the simple fact that  either by poor design or the arrogance of Microsoft, windows wants to be the first and only os installed on a given drive and will not write a master boot record that allows any other os to boot. when you install Ubuntu,(with windows already installed) it writes a master boot record that allows both OS to boot.

Sometimes making both Os bootable requires some editing of the grub bootloader. see other posts about this.

Linux is more forgiving, it does not care where it is installed.

---

