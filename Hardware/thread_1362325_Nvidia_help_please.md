---
title: "Nvidia help please"
date: 2009-12-23
forum: Hardware
---

### Post by AnimeFreak on 2009-12-23
Problem info:

i am trying to enable nvidia graphic drivers. i activate the drivers and restart but
 when i restart i get an error. i have the nvidia x server settings and when i open 
it i get an error i get an error saying i need to reset and edit the config file.
the nvidia drivers i can choose from are 160, 173, and 96

My system info:

OS: Ubuntu 9.04
motherboard: ASUS M2NPV-VM
video card: (built-in) Nvidia GeForce 6150
monitor: Dell 1704 FPTt 19 in

it has worked before but its not working now i just got a 80 gig sata HDD
would have anything to do with the problem?

thank u in advanced and if u need any more info just ask

---

### Post by steveneddy on 2009-12-23
Are you changing drivers?

Uncheck the one you are deleting and check the one you want to install.

---

### Post by AnimeFreak on 2009-12-23
> **steveneddy said:**
> Are you changing drivers?

Uncheck the one you are deleting and check the one you want to install.

no i have tried all the drivers but none will work 

none are checked at the moment

---

### Post by AnimeFreak on 2009-12-27
bump

---

### Post by lindsay7 on 2009-12-28
Do you know if a new Kernal was updated. That can be the problem. Try going back to a previous Kernal and see if that fixes the problem.

---

### Post by mark.altern on 2009-12-28
what config file? xorg.conf or simply the .nvidia-settings-rc in your HOME directory. If it is the latter, simple delete that .nvidia-setting-rc file will do the work.

best

---

