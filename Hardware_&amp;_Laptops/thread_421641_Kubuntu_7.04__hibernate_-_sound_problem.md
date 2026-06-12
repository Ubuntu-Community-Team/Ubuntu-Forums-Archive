---
title: "Kubuntu 7.04 : hibernate - sound problem"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by zgornel on 2007-04-24
Whenever I resume from hibernate I loose all sound. The interesting thing is that standby produces no issues and when resuming from hibernation it seems that nothing is wrong: volumes are ok, modules loaded, media players/KDE report no errors whatsoever. I can't figure it out. The bug exists for some time now.
Details: Toshiba L20-102 (intel 915gm chipset), Kubuntu 7.04. The problem might exist în Ubuntu 7.04.
I'm attaching results of: *lsmod*, *lspci -v*

---

### Post by DocHoliday52090 on 2007-04-24
Yep. It happens here to. 

I'm running Ubuntu 7.04 on an HP nc6220 with a AC'97 card and a 915 video chipset.

---

### Post by zgornel on 2007-05-03
Problem solved. Instructions [here]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/"). I followed them only for the hibernate part, suspend works ok.

---

### Post by torin on 2007-05-13
This was a great fix ^^ thnx to your prev post

---

### Post by zgornel on 2007-05-16
No problem. Spread the word :D

---

