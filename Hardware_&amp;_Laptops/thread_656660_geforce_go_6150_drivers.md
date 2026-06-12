---
title: "geforce go 6150 drivers?"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by MasterFateh on 2008-01-02
i have a compaq presario f572us and i installed a 64bit version of 7.10(is this gutsy?) with the text install. it finished fine but when ubuntu finishes loading it goes to a stripy screen and slowly fades to black. i think i need drivers for the videocard but if i find the correct drivers is there a way to install it since i can't get to the login screen. i'm really interested with trying linux but this laptop is giving me nothing to work with. here is the hp site with all the specifications for the computer: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069714&cc=us&lc=en&dlc=en&product=3441671&dlc=en&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069714&cc=us&lc=en&dlc=en&product=3441671&dlc=en&lang=en)
i am extremely new to linux so if you have a good solution please post it as simply as possible. thnx.

---

### Post by overdrank on 2008-01-02
> **MasterFateh said:**
> i have a compaq presario f572us and i installed a 64bit version of 7.10(is this gutsy?) with the text install. it finished fine but when ubuntu finishes loading it goes to a stripy screen and slowly fades to black. i think i need drivers for the videocard but if i find the correct drivers is there a way to install it since i can't get to the login screen. i'm really interested with trying linux but this laptop is giving me nothing to work with. here is the hp site with all the specifications for the computer: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069714&cc=us&lc=en&dlc=en&product=3441671&dlc=en&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069714&cc=us&lc=en&dlc=en&product=3441671&dlc=en&lang=en)
i am extremely new to linux so if you have a good solution please post it as simply as possible. thnx.

HI and welcome, you can try and boot into recovery mode which is usually the second choice in the grub. The reconfigure your xorg with this command ```
sudo dpkg-reconfigure xserver-xorg
``` Then use the command ```
reboot
``` or startx and hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by MasterFateh on 2008-01-03
now when i try to start up in recovery mode it stalls at loading hardware drivers. and when i tried booting into linux normally it stalled with only an eighth of the bar loaded on the splash screen.

---

