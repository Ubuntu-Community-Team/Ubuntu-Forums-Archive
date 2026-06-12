---
title: "Windows 7 overwrites GRUB when I boot into it"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by infernosoft on 2009-09-07
I am not tribooting Ubuntu 8.1, Fedora 11, and Windows 7. After installing Windows 7, GRUB was gone, and everytime I booted up, it would automatically boot into Windows 7 (without showing GRUB). 
 
Anyway, I fixed the problem by booting a live Ubuntu CD, and editing the GRUB. I was able to boot into Ubuntu & Fedora.
 
Then, after booting into Windows, and rebooting, GRUB was gone again and it automatically booted into Windows again.
 
How can I make Windows to stop overwriting GRUB!?

---

### Post by presence1960 on 2009-09-07
This is a relatively simple matter but I need more info so I can give you the commands to run from terminal.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

