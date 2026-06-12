---
title: "Ubuntu Inventing its own Raid :S Help"
date: 2013-05-04
forum: Hardware
---

### Post by zeroplayer on 2013-05-04
Ok so i was trying to install windows 8 and ubuntu on my raid set up. after lots of messing i decided to scrap my raid and go back to having 2x 500gb drive.

So formatted them both to empty and installed windows 8 on the first one then booted into ubuntu setup on pendrive to start installing and it is showing both drives under the MAPPER
asif they are still raided. this is causing install issue :(

Dose ubuntu always add the drives to a mapper or is somthing msytical taking over lol any help would be apriciated as i am currenty without ubuntu :(

---

### Post by zeroplayer on 2013-05-04
[IMG]http://tinypic.com/r/30979s1/5[/IMG][IMG]http://i40.tinypic.com/30979s1.png[/IMG]

---

### Post by Squidge1980 on 2013-05-04
Have you changed your BIOS to AHCI or IDE mode?

When base installing, make sure your BIOS is set correctly. I am guessing your SATA mode is still set to RAID.

Due to modern OSs, i would suggest AHCI mode -> avoid IDE at all cost

---

### Post by oldfred on 2013-05-04
Drives retain meta-data.

If you are sure you do not want RAID remove meta-data from drives.
       sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

### Post by zeroplayer on 2013-05-05
Hi again i change the option in my bios :) and its working for windows and ubuntu side by side :D Thank you

Not tried raiding it back up yet but i will remove the meta-data and let you know if that works.

Thanks again for your quick responce

---

