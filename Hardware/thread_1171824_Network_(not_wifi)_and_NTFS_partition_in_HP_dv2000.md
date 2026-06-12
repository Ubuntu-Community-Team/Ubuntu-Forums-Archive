---
title: "Network (not wifi) and NTFS partition in HP dv2000"
date: 2009-05-27
forum: Hardware
---

### Post by el mariachi on 2009-05-27
Hey! I'm trying to install 9.04 on a DV2000. It had WinXp and I installed Ubuntu without resizing the NTFS partition, leaving few space for ubuntu, but it got installed nonetheless. All networking worked fine until this step.

Then I booted the liveCD and tried to resize the NTFS partition to make space for Ubuntu --- gparted exited silently without a warning, leaving me with a faulty NTFS partition that can't boot complaining about hal.dll (I already downloaded this dll but it still doesn't make windows boot). 

Then HP's software tried to "rescue" my system, erasing GRUB and not fixing anything besides that. So I installed Ubuntu again. Now networking doesn't work --- wireless networks are detected (they are my neighbour's though) but my cable connection can't establish a connection... I switched the cable to my desktop pc and it works there... the LiveCD can't connect either :S

I need to fix the Hal.dll (windows xp users, can you share it Please??)  and get internet...

I can mount that partition but gpartedcan't touch it and testdisk crashes if I try to "list directories"

---

### Post by Dark_Stang on 2009-05-27
If you already replaced hal.dll and it still isn't working you may have corrupted the windows registry or really hosed up the file system. I'd try running a "chkdsk /r" from the windows xp recovery environment to see if that fixes any filesystem errors.

As for why networking would stop, I'm not sure. I'd just reformat Ubuntu's partition (to ensure you get a fresh start) and try to reinstall. That network card should work "out of the box" under Ubuntu.

---

### Post by el mariachi on 2009-05-28
I already reformated and it still isn't connecting...

---

