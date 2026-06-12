---
title: "windows removed grub..."
date: 2008-08-22
forum: General Help
---

### Post by ricky_cullen on 2008-08-22
i have just installed windows on another hard drive seperate from the one that runs ubuntu and i went to boot ubuntu only to find that it went to windows... is there anything that can be done or do i need to reinstall ubuntu to get everything to work again.

PS.
I only installed windows for games. my main os will still be ubuntu i personly like it more for many reasons.

---

### Post by Dr Small on 2008-08-22
Windows bootloader overwrote GRUB on the MBR of the harddrive. To avoid this problem, you should have unplugged the ubuntu hard drive, installed Windows on the second hard drive. Plugged the ubuntu hard drive back in. You could have then added an entry for Windows hard drive in GRUB to load off the second hard drive.

So basically, I guess you will have to just reinstall GRUB again.

Here is a guide by Bodhi.Zazen on Multibooting:
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

