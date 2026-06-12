---
title: "HDD help, unable to mount volume."
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by Toshmate on 2007-07-18
not to familiar with Linux/Ubuntu yet so I dont know what to do.

This is whats up: had winxp and wanted to get new computer, i connected a 40GHDD and called it ANIME and transffered everything i needed onto it then took it out again. then i wiped the 80GHDD that XP was on and installed Ubuntu, but now that i have got round to putting ANIME in to put my stuff on the primary HDD it comes up as ANIME but when enter it a warning comes up saying:

Unable to mount the selected volume.

then when i click 'Show More Details' it comes up with

error: device /dev/hdd5 is not removable

error: could not execute pmount


all i want to do is access the HDD and get some files of it.

---

### Post by paulphillips on 2007-07-19
Can you tell us exactly the steps you are taking to attempt mount the drive?

What happens if you go *System->Administration->Disks*? Do you see your "ANIME" drive?  What format is the drive?  I presume NTFS or FAT32?

You could try to mount it via the command line and see how you go:

prompt> sudo mkdir /mnt/anime
prompt> sudo mount /dev/<partition where your stuff is> /mnt/anime

---

