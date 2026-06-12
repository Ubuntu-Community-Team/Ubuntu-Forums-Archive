---
title: "HowTo: Get your graphics card working on Ubuntu Gutsy (ATI)"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by Kalouste on 2008-01-27
**Problem**

[LIST]
[*]No Desktop Effects or/and
[*]No 3D acceleration in games
[/LIST]

**Hardware**

[LIST]
[*]Laptop: LG P1 Pro Express Dual Laptop
[*] ATI Mobility Radeon X1400
[/LIST]

**Solution**

In this solution I'll be using **Envy**, an application written by Alberto Milone which automatically does the work for you:

[LIST]
[*]detect the model of your graphic card (ATI/NVIDIA only)
[*]package the driver that comes with ATI or NVIDIA's installer (from their respective websites)
[*]install all you need to package and install the driver
[*]configure the XServer for you
[/LIST]

*See [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")* for more info on Envy.

[LIST=1]
[*]Download Envy
[INDENT][LIST]
[*][Download Envy's latest version]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb")
[*]Download to any directory you wish
[*]Open up a terminal window and cd to the directory you chose
[/LIST][/INDENT]
[*]Install and Set-up Envy
[INDENT][LIST]
[*]Install the deb package ```
sudo dpkg -i envy*.deb
```
[*][Enable "universe" and "multiverse" extra-repositories]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")
[*]Check if all package dependencies are installed and install those who are missing
```
sudo apt-get install -f
``` 
[*] Launch Envy's GUI ```
sudo envy -t
```
[/LIST][/INDENT]
[*]Install ATI Driver
[INDENT][LIST]
[*]Choose option 3 "Install ATI Driver"
[*]Follow the instructions and let Envy automatically configure everything for you
[*]Reset X Window by pressing Ctrl + Alt + Backspace key combination
[/LIST][/INDENT]
[/LIST]

_Note_ You can set-up your graphics card's driver manually with Envy. In this tutorial, I chose the "easiest" way.

**Useful links**
[Install Envy FAQ]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu")

---

