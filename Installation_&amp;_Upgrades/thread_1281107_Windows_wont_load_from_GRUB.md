---
title: "Windows wont load from GRUB"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by loseby on 2009-10-02
2 different physical drives. had Vista running on main drive and when I installed 9.04 I made the GRUB installer on the actual Ubuntu drive and then changed the BIOS so that was the first boot hard drive. Ok, it booted and GRUB showed the normal stuff + Vista but when I selected Vista it wouldnt boot to Vista.

Anyway ended up  changing BIOS  back to Vista drive as primary boot  and deleted everything on the Ubuntu hard drive and reinstalled Ubuntu with the default settings ie. boot manager on Vista hard drive 

Now I would like to have the GRUB on the Ubuntu drive and get Vista to boot . Is that possible or a waste of time ?

---

### Post by presence1960 on 2009-10-03
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by loseby on 2009-10-05
at the moment I have decided to leave it the way it is


thanks for the reply

---

