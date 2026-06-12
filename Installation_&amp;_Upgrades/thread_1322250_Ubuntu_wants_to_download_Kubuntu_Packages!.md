---
title: "Ubuntu wants to download Kubuntu Packages?!"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by cainwen296 on 2009-11-10
Ok, I have a problem that I have never seen before, can't find anyone whose had it, and can't think why I have it. 

When I run the update manager, it downloads most of the packages and then asks me 
"Please insert the disk labeled:
Kubuntu 9.10 _Karmic Koala_ - Beta i386 (20090929.2)
in drive /cdrom/"

when I click ok , it keeps asking (becuase there is no Kubuntu disk).
If I click cancel, it says 
"The following error occured: W: Failed to fetch cdrom:[Kubuntu 9.10 _Karmic Koala_ - Beta i386 (20090929.2)]/pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb"

The only think I can think of  is that I helped out a friend who wanted to install Kubuntu, but whose cdburner died, so I burned the disk on my computer. However, I've done things like that before, and never had ubuntu ask to update the disk.  Why does the update manager even know about it? I can't see anyhting relating to Kubuntu in the actual update list, btw.

Anyone have any ideas on how to make it stop looking/skip so I can update? I don't want to upgrade to 9.10 till it can handle  LANs with windows machines.

I"m running Ubuntu 9.04 (up to date save this last batch) on a 3 year old Dell Inspiron 1505e, with Vista on a seperate partition, if that makes any difference.

---

### Post by nerdy_kid on 2009-11-10
is the cdrom entry checked in your software sources?? just a thought...have no idea what the purpose of that entry is in the first place...

---

### Post by cainwen296 on 2009-11-10
wow, never would have looked there.yes, it was checked (I wonder why didn't it want to update opensuse or any of the other cds i've burned??)  once I unchecked it, the update worked perfectly. 

Thanks again!

---

### Post by nerdy_kid on 2009-11-10
glad i could help; have fun!!!;)

---

