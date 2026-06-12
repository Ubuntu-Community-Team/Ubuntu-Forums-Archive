---
title: "Impending HDD failure!"
date: 2008-10-24
forum: Hardware
---

### Post by sirgeekalot on 2008-10-24
The HDD in my M1330 is currently on its last legs after only a year and a half. :(

i'm getting a lot of read errors from certain areas and have had to FSCK it way too many times than is healthy. 

i have a backup of the /home folder on a portable usb drive so thats ok. 

My question is though, if i were to boot using a USB stick and the live distro, could i in theory copy everything from my hdd to the portable drive, upgrade to a new drive and copy everything back without having to reinstall everything?

Many Thanks, 

Adam

---

### Post by cashmoney on 2008-10-24
In theory yes.  Easiest way would be to install DD_rescue,  Attach second HDD and dd_Rescue from HDD 1 (bad one) to the new one.

Link to understand DD-Rescue
[http://www.garloff.de/kurt/linux/ddrescue/]("http://www.garloff.de/kurt/linux/ddrescue/")

---

### Post by tgalati4 on 2008-10-24
When you finally pull the drive, please post the exact model number.  The Google Hard Drive study found that drive reliability is most strongly correlated to age (~3-5 years is the knee in the curve) and specific model number, but not necessarily manufacturer.

It's possible that your specific drive model has some design issues that lead to shorter life.

---

### Post by sirgeekalot on 2008-10-24
thats great.. thank you. 

DD_rescue is just the app i'm looking for. the bad sectors on the drive cause the laptop to lock up for a few mins everytime it reaches a bad bit. 

so i'll hook up the portable drive, copy it all accross with dd_rescue, swap in the new drive (brand spankers 320gb seagate one :D ) boot up with usb ubuntu from memory stick and restore.. presto, new drive and no hassle. 

cheers guys. 

i'll post up the info on the old drive when i get it out of the laptop.

---

### Post by tgalati4 on 2008-10-24
You can run badblocks on the drive and perhaps salvage it for a beater machine.

---

### Post by sirgeekalot on 2008-10-25
worked like a charm. thanks guys.. so much easier than totaly reinstalling everything!!

gonna wipe the old drive and use it as a portable drive.. after running badblocks on it of course..

---

