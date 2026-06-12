---
title: "Dual boot partition"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by mananbshah on 2009-10-08
HEY,
i have installed edubuntu on my system first . then i installed windows xp home edition. now my problem is that it does not ask me which OS i want to open and i have some really important data on edubuntu. please urgent help needed

---

### Post by presence1960 on 2009-10-08
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I need this info to give you the commands to run so you can restore GRUB. When you installed windows it overwrote GRUB in the MBR.

---

