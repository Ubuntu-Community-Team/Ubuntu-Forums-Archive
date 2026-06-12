---
title: "Nvidia + low graphics"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by briantoumbs on 2009-02-19
My question: 

I have installed each of these in a dual boot system with Windows XP pro:  Ubuntu 8.10 32bit, Ubuntu 8.04 32bit, Ubuntu 8.04 64bit.


Each time I finish installing one of them I complete all of the system updates, I install Compiz manager, fusion-icon, emerald, ubuntu-restricted-extras, and some random games. After all that with my computer fully up to date I goto [www.nvidia.com](www.nvidia.com) and download the graphics driver. When it finishes downloading I push ctrl+alt+F1 and logon as root. At root I type /etc/init.d/gdm stop to stop my Xserver. Then I install the driver with sh NVIDIA(tab) "tab completion doesn't work on forums =(" 

It goes through this part fine. When I start X and logon to my user account again I have the special effects. However when I turn my pc off or restart it always returns in Low graphics mode or VGA mode. 


I have been having this problem for a while now, I feel comfortable, and can do most things I need to when I am working with Ubuntu, and the terminal but I cannot figure out what I am doing wrong with this. 


I have a Nvidia 8600 gt card, I have used either a Dell 17' or a Acer 17' LCD monitor. I only use one monitor with the OS. If I install it with the Acer that is all I use with it.

---

### Post by briantoumbs on 2009-02-19
-- 
I looked up some other posts about this and tried again. I'm stuck in low graphics again.

---

### Post by overdrank on 2009-02-19
> **briantoumbs said:**
> -- 
I looked up some other posts about this and tried again. I'm stuck in low graphics again.

Have you tried booting into recovery mode and use the xfix option to correct this issue. 
Recovery mode is usually the second choice from the grub, once into recovery mode you should be given 4 options and the last is xfix. After completing the xfix option your should be given the 4 options again and you may choose to boot normally. 
If you are using 8.04 Hardy then you may try what PmDematagoda suggest [here]("http://ubuntuforums.org/showpost.php?p=4970051&postcount=2")

---

### Post by briantoumbs on 2009-02-21
I tried the xfix with no success and then I tried that link, my screen was cut in half and all messed up. 

I tried to install with envy, a time before I used this program and it worked fine, this time it didn't work.


It seems as if I install the driver but when I shutdown or restart I loose it.

---

