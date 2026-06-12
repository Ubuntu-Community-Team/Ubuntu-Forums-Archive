---
title: "Upgrade from 9.04 to 9.10 trashed my system"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by poldie on 2009-11-01
I did the install from the upgrade manager.  Left it running overnight.  This morning I checked and it had stopped on:

could not install /var/cache/apt/archives/indicator-session_0.1.7-0ubuntu3_i386.deb

conflicting packages.


i continued - what else could I do.   A few mins later I got the same thing only with:

module-init-tools.

It told me it could now not continue and that my system might be unstable.   It suggested I report it.  It's right - I can't boot into ubuntu now.  When I boot I get the grub menu, and then, as it tries to load, the screen goes black.  I left it a min and remembered that when I pressed escape here before I got some text, so I did that and got told it had an error mounting the file system.

Any chance I could try again somehow, perhaps from a cd?  I want to have a look around and see if I can rescue any files before doing a fresh install.  I'm wary of doing a fresh install because I don't want to damage my existing windows XP install, and I've lost faith in Ubuntu's ability to perform an upgrade successfully.

---

### Post by kiking74 on 2009-11-01
I wanted to install 9.04 on my laptop and have it working nicely (with the graphic card is a sux)... When I tried to install the updates, my wireless connection get sux, though it is set as an unsecured. I cannot access the network connection... I always have (wired connection; Setup VPN)... What shall I do???
 
Computer Specs:
ACER 4530, AMD Turion, NVIDIA GeForce 9100G, 2GB DDR2, 160GB HD, Atheros AR5007EG.
 
Can somebody help me????

---

### Post by poldie on 2009-11-01
> **kiking74 said:**
> I wanted to install 9.04 on my laptop and have it working nicely (with the graphic card is a sux)... When I tried to install the updates, my wireless connection get sux, though it is set as an unsecured. I cannot access the network connection... I always have (wired connection; Setup VPN)... What shall I do???
 
Computer Specs:
ACER 4530, AMD Turion, NVIDIA GeForce 9100G, 2GB DDR2, 160GB HD, Atheros AR5007EG.
 
Can somebody help me????


You should start your own thread.  Your problem has nothing to do with mine.

---

### Post by balak on 2009-11-01
> **poldie said:**
> 

Any chance I could try again somehow, perhaps from a cd?  I want to have a look around and see if I can rescue any files before doing a fresh install.  I'm wary of doing a fresh install because I don't want to damage my existing windows XP install, and I've lost faith in Ubuntu's ability to perform an upgrade successfully.

Yes, you should be able to recover everything with a CD. I have upgraded (mostly) successfully for several generations now.. It just depends on how many manual modifications you do on your system - which can really break the upgrade.

Download the alternate CD iso of karmic, i386 or amd64 depending on what you currently have. Burn it into a CD using another computer.
Boot from the alternate CD, choose 'repair/fix' an installation. It will ask you to choose which installation to "repair". If you know where you had installed before, or if you have installed ubuntu/linux in only once, then it will be easy to find out.

---

### Post by poldie on 2009-11-01
> **balak said:**
> Yes, you should be able to recover everything with a CD. I have upgraded (mostly) successfully for several generations now.. It just depends on how many manual modifications you do on your system - which can really break the upgrade.

Download the alternate CD iso of karmic, i386 or amd64 depending on what you currently have. Burn it into a CD using another computer.
Boot from the alternate CD, choose 'repair/fix' an installation. It will ask you to choose which installation to "repair". If you know where you had installed before, or if you have installed ubuntu/linux in only once, then it will be easy to find out.

Thanks. I just tried that.  Sadly, there is no `repair fix` option anywhere.

---

