---
title: "Adding WinXP to Grub"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by jbeukema on 2009-09-07
The layout:

two hard drives. One has Windows XP, the other has Ubuntu (swap partition, then then Ubuntu on ext3) and an NTFS partition for storage. Re-installing Grub gives me a grub loader with only Ubuntu and [this]("http://www.tipstrs.com/tip/84/Add-windows-to-grub-menu") added a non-functional windows option.

As is, I can only boot windows by booting from the other hard drive. How do i fix this and why can't Grub detect and add Windows like it's supposed to?

---

### Post by running_rabbit07 on 2009-09-07
> **jbeukema said:**
> The layout:

two hard drives. One has Windows XP, the other has Ubuntu (swap partition, then then Ubuntu on ext3) and an NTFS partition for storage. Re-installing Grub gives me a grub loader with only Ubuntu and [this]("http://www.tipstrs.com/tip/84/Add-windows-to-grub-menu") added a non-functional windows option.

As is, I can only boot windows by booting from the other hard drive. How do i fix this and why can't Grub detect and add Windows like it's supposed to?

You have to install grub into the MBR, you can't add the MS bootloader to grub.

---

### Post by presence1960 on 2009-09-08
This should be a very easy fix, first I need some info about your setup & boot process. Do this:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Then I can give you the command to run so you can edit the GRUB menu by placing proper code in there for windows.

---

