---
title: "Dual boot Ubuntu 9.10 and Windows XP"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by cellpunxer on 2009-11-06
I already have ubuntu 9.10 installed and wanted to install windows xp too. Can anyone point me to a link on how accomplish this? I have my grub.cfg backed up and gparted install just need to know what to do next? thanks!

---

### Post by cellpunxer on 2009-11-06
bump

---

### Post by gspolis on 2009-11-12
I have karmic installed too, and want to install win xp. But I didn't took any step forward to do this yet, coz I can't find anything. I think I'll go for some old docs and experiment. BRB.

---

### Post by audiomick on 2009-11-12
Can't help much, but as far as I know, if you install a windows after a linux, the windows writes over the boot loader. Look for info about grub, might help.

---

### Post by presence1960 on 2009-11-12
Using gparted from the Ubuntu live CD or gparted live CD create a **_primary NTFS partition or unallocated space for Windows._** Once that is accomplished boot the Windows installation CD and install Windows to the NTFS partition or unallocated space. When install is complete reboot & make sure you boot straight into windows. If you do then you need to restore GRUB. For restoring GRUB for karmic see [here]("https://help.ubuntu.com/community/Grub2"). There is a menu on right side of that page. look for #11- Reinstalling GRUB 2, subtitle 1- Reinstalling from Live CD for the instructions.

When you install windows after Linux, windows overwrites GRUB on the MBR with it's bootloader. That is why you must restore GRUB to MBR.

---

