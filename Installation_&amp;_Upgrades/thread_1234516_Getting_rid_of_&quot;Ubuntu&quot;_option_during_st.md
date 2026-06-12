---
title: "Getting rid of &quot;Ubuntu&quot; option during start-up?"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by dpatel304 on 2009-08-08
I initially tried installing Ubuntu using the 'Install in Windows' option.  This would create a Ubuntu install on my Windows partition so that I can test it out.  Everytime I booted up, it would ask if I wanted to go to Windows XP or Ubuntu.

I recently uninstalled the "test drive" Ubuntu by going into the Ubuntu folder that appeared on my C:\ in Win XP and clicked the 'uninstall' icon.  It seems to have uninstalled, but, for some reason, when I boot up, I still have the option to either go into Windows XP or Ubuntu (when I click Ubuntu, I get an error and have to restart, since Ubuntu is no longer there).

I'd like to know how to get rid of that menu so that it goes straight into Windows XP

In case anyone cares: Although I did uninstall Ubuntu, it was only to get rid of the 'installed in windows' version of Ubuntu and replace it with a true dual-boot install (hoping it would run more smoothly).  I successfully completed the dual boot install, and am now prompted with the option to go to Ubuntu, Ubuntu recovery mode, memtest (I think), and Windows XP.  If I select Windows XP, I am taken to the screen where I have to choose either Windows XP or the non-existant "test drive" Ubuntu install that isn't there any more.  It's a minor hassle, but it'd be nice not to have that useless menu there any more.

---

### Post by amac777 on 2009-08-08
While booted into your working ubuntu, edit the boot menu using this command:

```
sudo nano /boot/grub/menu.lst
```

Just delete the section corresponding to the 'test drive' ubuntu.

---

### Post by presence1960 on 2009-08-08
you don't get GRUB if you installed via wubi. What you need to do is edit your boot.ini file by removing the line referencing Ubuntu. Be careful to only remove the Ubuntu line. do this: Control Panel > System > Advanced tab > Startup & Recovery options > click Edit. This will bring up boot.ini
Remove the line referring to wubi/Ubuntu ONLY

---

