---
title: "external HDD not appearing"
date: 2008-07-26
forum: Hardware
---

### Post by mattmaddox on 2008-07-26
Hey I just installed ubuntu today, friggen love it

but I want to transfer my old files off my external hdd onto my laptop (asus c90s)

When I plug the external in, I go to "computer" and nothing appears.

Anyone know why?

cheers

---

### Post by argosreality on 2008-07-27
Its possible that for some reason Ubuntu isn't auto mounting the drive. After you plug it into the computer check /var/log/dmesg to see if the computer is detecting the drive and what device ID its assigned it to. then you can create a folder in media "sudo mkdir /media/YourName" and then mount the drive to that folder sudo mount /dev/sdX /mediaYourName" and that'll then show it in the media folder

---

