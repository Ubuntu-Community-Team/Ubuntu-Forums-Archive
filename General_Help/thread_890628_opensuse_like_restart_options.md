---
title: "opensuse like restart options"
date: 2008-08-15
forum: General Help
---

### Post by davebell on 2008-08-15
Hey!
i was just wondering if it is possible to set this up in ubuntu.

about a year ago i tried opensuse and about the only good thing about it was that upon selecting restart it was possible to select which system to boot upon restarting so if i wanted to reboot into windows(heaven forbid) i could do this without having to mash the keyboard to stop grub from booting ubuntu.

just wondering...

thanks!

---

### Post by iaculallad on 2008-08-15
> **davebell said:**
> Hey!
i was just wondering if it is possible to set this up in ubuntu.

about a year ago i tried opensuse and about the only good thing about it was that upon selecting restart it was possible to select which system to boot upon restarting so if i wanted to reboot into windows(heaven forbid) i could do this without having to mash the keyboard to stop grub from booting ubuntu.

just wondering...

thanks!

Sorry to mention it but there's no way or option that you could let Ubuntu have that option of choosing other OS to boot from after reboot. I think it's all about GRUB compatibility so Ubuntu has not yet included it in its feature. You have to stick on choosing it from the GRUB menu.

---

### Post by davebell on 2008-08-16
k thanks for that! hopefully they include it in 8.10!!

---

### Post by cariboo on 2008-08-16
You could also change the wait time in grub to 10 seconds, that way you wouldn't have to:

> mash the keyboard to stop grub from booting ubuntu 

Jim

---

### Post by iaculallad on 2008-08-16
> **davebell said:**
> k thanks for that! hopefully they include it in 8.10!!

I doubt it, having Ubuntu the option of loading windoze after reboot? Heh, that option would only be for OpenSuse since Ubuntu can live even w/o giving windoze the option (of planting itself on GRUB) to boot after a warm reboot.

---

### Post by bingoUV on 2008-08-16
> **davebell said:**
> Hey!
i was just wondering if it is possible to set this up in ubuntu.

about a year ago i tried opensuse and about the only good thing about it was that upon selecting restart it was possible to select which system to boot upon restarting so if i wanted to reboot into windows(heaven forbid) i could do this without having to mash the keyboard to stop grub from booting ubuntu.

just wondering...

thanks!

But does windows give you the option to reboot into Ubuntu? I think not, and you cannot easily change menu.lst from windows.

So providing such option means "Bye Bye Forever, Ubuntu", at which point you might as well uninstall Ubuntu and save your disk space and boot time. Have I got it wrong?

---

### Post by mihas on 2008-09-13
This is radically simple to do: 

kdesudo systemsettings
Advanced tab 
System
Login manager
Halt (or something like that - tab 4)
Boot manager
Select GRUB or LILO (depends which one you use, default in Ubuntuis GRUB)
Apply
Exit SystemSettings
Logout
Restart KDM (Alt+E should work I think, othervise Ctrl+Alt+F1, login, sudo /etc/init.d/kdm restart)

Hope it helps!

---

