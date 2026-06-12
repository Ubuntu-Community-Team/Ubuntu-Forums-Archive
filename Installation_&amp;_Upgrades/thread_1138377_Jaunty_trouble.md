---
title: "Jaunty trouble"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by goldencako on 2009-04-26
Helloy everyone,

As it was with most people, my transition to Jaunty has been less than smooth. I had a some trouble with CPU frequency scaling, which was solved by installing **cpufrequtils** as said here: [http://ubuntuforums.org/showthread.php?t=1136696]("http://ubuntuforums.org/showthread.php?t=1136696"). I also had network problems. Again, the new plasma widget and the death of Knetworkmanager threw me off. But a little messing around here and there, coupled with a healthy restart did the trick. Well, now I have just one more problem. And this time with Gnome. Turns out I have both Gnome and KDE, and I'm still not sure which one of them I'm keeping. I made the upgrade from KDE, and ever since, the program windows in Gnome have no borders. I'm including a screenshot. I am actually considering doing a fresh install of (K)Ubuntu 9.04, but I'm afraid I'll lose application preferences etc. I also have a Windows partition that I can't mount (validation problems I can't fix now) that I'm thinking of freshly reinstalling. Is there a way that I can install Windows again without messing up my boot section? And is there a straightforward way of removing Gnome or KDE without having to do it package by package? Well, thanks for all the help. Any suggestions are welcome.

---

### Post by Triptol on 2009-04-26
You might be able to fix it by reinstalling metacity:
```
aptitude purge metacity
aptitude install metacity
```

---

### Post by goldencako on 2009-04-26
Tried it. Didn't work. I had previously tried reinstalling **ubuntu-desktop**, also to no avail. I just noticed I'm not able to use Alt-F2 anymore. I think it might be related.

---

### Post by Triptol on 2009-04-27
Seems your windows manager is not starting (which should be metacity IIRC in Gnome). You could try starting it from your terminal by just entering **metacity**. If your lucky the session manager will pick it up and automatically start it again once you logon.

Now to your other questions:
[LIST]
[*]If you do a reinstall, you will not load your settings as long as you don't delete your homedrive. That is actual the reason why I keep my home on a single partition. If your homedrive is not on a single partition, you need to back it up. You must of course install all applications that are not part of the standard, but then again, installing in Ubuntu is easy compared to other OS-es.
[*]If you reinstall Windows you will probably overwrite your MBR and thus lose Grub. Booting from a Live CD and reinstalling GRUB in the MBR will fix that problem.
[*]Yes you can remove Gnome or KDE to save some disk space. There are descriptions in the forum.[/LIST]

---

### Post by goldencako on 2009-04-27
Thank you Triptol for the comprehensive reply. It really was **metacity** failing to run. I started it automatically from the terminal and then added it to the startup programs. That solved it.
On another note, I managed to mount my Windows partition without forcing it. I think I'll back it up, reinstall it, reintall Grub and then install either Kubuntu or Ubuntu. Whichever I'm happier with at the end of the week. But before I'll make sure to create a new partition for my home folder (never knew why people did that!)

---

### Post by Triptol on 2009-04-29
Glad to hear it worked.

---

