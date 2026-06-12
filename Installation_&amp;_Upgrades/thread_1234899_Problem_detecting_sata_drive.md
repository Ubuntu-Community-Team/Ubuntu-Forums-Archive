---
title: "Problem detecting sata drive"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by phuchungbhutia on 2009-08-08
I have two drives one is sata and another pata and . . I have win xp in sata and i installed ubuntu in the other today . . But i couldnt see ubuntu detect sata drive even while installing and so there is no bootloader either . . One more thing is that i didnt partition swap so could that be any problem but i dont think so . . As it didnt show any other drive i dont think so . .  Plus it takes time to start up the ubuntu os . . Now i have to change boot drive priority everytime i need to change the os i want to use . .   and if swap does help . . How do i install bootloader plus create swap . .

---

### Post by presence1960 on 2009-08-08
Boot into Ubuntu or from the Ubuntu live CD. When the desktop loads download the [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/") to the desktop. Once downloaded to desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted here, highlight all text pasted and click the # sign on the toolbar to place code tags around the text. This info will show us your setup & boot info.

---

