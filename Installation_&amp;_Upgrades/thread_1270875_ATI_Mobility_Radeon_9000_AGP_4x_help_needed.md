---
title: "ATI Mobility Radeon 9000 AGP 4x help needed"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by ibmT40 on 2009-09-20
hi i have ibm t40 laptop and i just installed last version of ubuntu.but i think i couldn t installed my graphic card`s driver properly.because when i try to watch online video (except you tube) it s showing the video but with frozen rhythim. here my video driver for windows xp

[http://www-307.ibm.com/pc/support/site.wss/MIGR-41918.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-41918.html)

please somebody explain how i gonna install this 
thx

---

### Post by Jimmyfj on 2009-09-20
Go to the System>Administration-menu and click on Hardware drivers. After the program has searched your system you need to install the driver marked (recommended) and activate that driver. Reboot your system and the driver should work fine.

Next you open a terminal and run this command:

```
sudo apt-get install ubuntu-restricted-extras
```

Go to Programs>Add/Remove applications and look in the group "Other" to make sure that Macromedia flash is installed. Then go to the Internet group and find icedteaplugin. If installed remove it, it makes to many flaws to be of any use just yet.

---

### Post by sideaway on 2009-09-20
What version of Ubuntu are you using? ATi's drivers will not work with 9.04.

EDIT: Just read your post properly, silly me :P You need to install the 3rd party drivers called radeonhd if they aren't already.

---

### Post by Jimmyfj on 2009-09-20
> **sideaway said:**
> What version of Ubuntu are you using? ATi's drivers will not work with 9.04.

That is NOT correct - Ati drivers works fine in Ubuntu 9.04 - So please....

True that there are issues with some drivers from ATI, but nothing you can't tweak around. The driver for my Radeon 9600 works better that the driver for my nVidia G-Force 5500 card, but not my 8600GT PCI-E, that card rocks.

---

### Post by sideaway on 2009-09-20
Actually the latest ATi drivers drop support for any car pre the HD 2*00's. And the older ATi drivers aren't compatible with the current xorg... talk about your catch 22. 9.4 won't work with a radeon mobility 9000, and 9.3 won't work with 9.04's xorg.

The issue is fairly well documented and experienced.

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)
[http://ubuntuforums.org/showthread.php?t=1133844&page=2](http://ubuntuforums.org/showthread.php?t=1133844&page=2)

---

### Post by ibmT40 on 2009-09-20
> **Jimmyfj said:**
> Go to the System>Administration-menu and click on Hardware drivers. After the program has searched your system you need to install the driver marked (recommended) and activate that driver. Reboot your system and the driver should work fine.

Next you open a terminal and run this command:

```
sudo apt-get install ubuntu-restricted-extras
```Go to Programs>Add/Remove applications and look in the group "Other" to make sure that Macromedia flash is installed. Then go to the Internet group and find icedteaplugin. If installed remove it, it makes to many flaws to be of any use just yet.



ok this solution handle it the problem thanks a lot.only what i didn t after installing ubuntu was this command.
```
sudo apt-get install ubuntu-restricted-extras
```and after i did it this command;graphic card start to work properly.thanks a lot again.i hope this thread help anyone else like who has the same problem.

---

