---
title: "Installation woe"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by IAmNoodle on 2009-11-07
I've just tried installing Karmic onto my girlfriend's computer with a CD I burnt off my own computer that I also used to upgrade mine with from Jaunty. All went well until after the partition editor phase and the keyboard type phase. It then went on to claim there was a problem with the CD, then suggested the Hard Disk was too hot. 

I rebooted, selected the option for it to check the CD for errors, and it came back to say there was nothing wrong. 

It won't allow me to select Ubuntu when I boot up, and I can't overwrite the partition. I'm wanting to keep it as a dual booting machine too. 

Anybody know what I can do to solve the problem?

---

### Post by IAmNoodle on 2009-11-07
If it helps, my intention is to overwrite the current non-working ubuntu partition with another one.

I must apologise if I appear impatient. I have a day until I can do anything to fix it for another week, and I'd rather get this sorted to put my girlfriend's worries about computer security at ease

---

### Post by drudogg on 2009-11-07
try getting a gparted live disc. you can run it and use it to delete the bad partition. then also create the new partition, and tehn try to reinstall the kubuntu again afterwards... 

not sure about the heat thing though.

---

### Post by IAmNoodle on 2009-11-07
Thanks. I'll give it a go as soon as I have access to a blank CD tomorrow

---

### Post by PRC09 on 2009-11-07
I ran into this with a bunch of CDRW disks.Burned the same image to CDR and that solved the problem.

---

### Post by IAmNoodle on 2009-11-15
Thought you'd like to know that I've finally succeeded.

I tried burning another copy using a CD-R instead of a CD-RW that I tried the first time, and after that failed, it booted me into the 'trial' version using just the CD, where I used GParted to erase the failed partition. Tried several times (and used GParted as many times) without success. 

This week I burnt off another CD-R from home, and this time it wouldn't even boot up right. I tried messing with the settings for the install after trying (and failing) to install GRUB2. After finding that booting up the trial version in 'safe graphical' mode, I tried the same setting to install. SUCCESS! Sound works, internet works, most things work! 'm now trying to get things to an acceptable workable level for my girlfriend (who's only used to Windows) and we'll hopefully have another Windows convert. We're not there just yet, mind, but nearly.

---

