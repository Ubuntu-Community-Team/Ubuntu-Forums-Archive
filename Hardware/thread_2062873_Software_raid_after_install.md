---
title: "Software raid after install?"
date: 2012-09-25
forum: Hardware
---

### Post by feardotcom on 2012-09-25
So with the annoucement of the Steam client coming to Ubuntu, i decided to format my 250GB windows drive. I'm curious to know (if it's even possible) to put my Ubuntu hard drive and now EX-windows hard drive (which is now ext4) into a software raid so everything shows up as one drive and i dont have to split stuff up. I dont really want to format my ubuntu drive.

---

### Post by feardotcom on 2012-09-27
bump

---

### Post by Ubun2to on 2012-09-28
I think some boards have RAID controllers built in (I just realized that there is a RAID configuration screen on my boot cycle-I just never read it until now).
The Disk Utility might be able to do it-File>Create>RAID Array..., but I am unfamiliar with using it.
I know the Minimal CD supported RAID configuration, but I'm not sure how that would be setup.

---

### Post by SlugSlug on 2012-09-28
you wont be able to add your existing drive to a raid - you'd need to wip it and start fresh.

LVM might do the job though

[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

---

### Post by feardotcom on 2012-09-28
Ok, thanks, i guess i wont worry about it then, i dont want to take a chance of screwing something up. :(

---

