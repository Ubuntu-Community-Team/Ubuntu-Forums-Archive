---
title: "Dual Boot Help"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by wildarmsx on 2006-01-30
First off I would like to thank everyone for there help and appolgize if this was already covered. 

Current Config.
Processor: AMD 64 3000+
mobo: Asus A8V Deluxe
Ram: 1 GB
Video: ATI x850 Pro PLT
HDD - 2x Western Digital Raptor SATA 36GB hdd raid 0 - Windows XP Currently installed
HDD - 1x Western Digital Caviar SATA 80GB - would like to load Ubuntu

First off I would like to to be able to Dual Boot Windows XP and Ubuntu. but i don't want to install it on the same physical drive. As you see I have a Windows Installed on my computer. I would like ubuntu to be installed on the 80gb and keep the existing windows setup but when I install Ubuntu it just goes into windows xp. If i can get any input that would be great and i don't want to have to switch hdd boot sequence. 

Thanks
Wildarmsx

---

### Post by mtron on 2006-01-30
not necesarry. install grub (a advanced boot loader) in the Master boot record of the first hd (hda1 un GNU Linux or hd0(0) in grub style) 

tutorial [here ]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub") and [here]("https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29")

---

### Post by DaBruGo on 2006-01-30
[QUOTE=wildarmsx]First off I would like to thank everyone for there help and appolgize if this was already covered. 

Current Config.
Processor: AMD 64 3000+
mobo: Asus A8V Deluxe
Ram: 1 GB
Video: ATI x850 Pro PLT
HDD - 2x Western Digital Raptor SATA 36GB hdd raid 0 - Windows XP Currently installed
HDD - 1x Western Digital Caviar SATA 80GB - would like to load Ubuntu

First off I would like to to be able to Dual Boot Windows XP and Ubuntu. but i don't want to install it on the same physical drive. As you see I have a Windows Installed on my computer. I would like ubuntu to be installed on the 80gb and keep the existing windows setup but when I install Ubuntu it just goes into windows xp. If i can get any input that would be great and i don't want to have to switch hdd boot sequence. 

Thanks
Wildarmsx[/QUOTE]

wildarmsx,

I don't know if this helps, but I have a thread dealing with dual booting XP and Ubuntu that might be of interest to you.

[http://www.ubuntuforums.org/showthread.php?t=80811]("http://www.ubuntuforums.org/showthread.php?t=80811")

Hope it helps,
DAVE

---

### Post by wildarmsx on 2006-01-31
thanks.

---

