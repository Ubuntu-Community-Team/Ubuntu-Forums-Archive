---
title: "Reinstalling overtop previous ubuntu installation"
date: 2008-10-05
forum: General Help
---

### Post by Adelio on 2008-10-05
Hi
I installed Ubuntu 8.04 through Windows. It no longer boots up correctly after i login. It just hangs. Is there any way to re-install over top of it through windows? I've tried using disk and it does nothing and of course windows can't uninstall it.
I may have to uninstall it using gpart etc but the problem is i have GRUB loader for PCLinuxos and when i click on windows it give me the option for Windows and Ubuntu. So if i do a fixmbr, it will wipe out my PClinuxos grub and Ubuntu selection option. Is that not correct? Any help appreciated.
Thanks
Del

---

### Post by Adelio on 2008-10-05
Hi
Maybe Ubuntu can incorporate an proper uninstaller for windows when situations such as mine occur in future releases.
Thanks
Del

---

### Post by Sef on 2008-10-05
Moved to wubi forums.

---

### Post by ago on 2008-10-06
What is exactly the problem? Can you boot from rescue mode?
Also if you want to uninstall, and used wubi rev 505, see [https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu)

---

### Post by davidryder on 2008-10-06
I tried Wubi also and it didn't last long. Most of my problems were unique to Wubi so I setup a dual-boot system and all my problems went away!

Wubi should come with a disclaimer before installing.

---

### Post by Adelio on 2008-10-11
Hi 
Sorry for my unclear question. I'll be a little more detailed about my situation.
I have a dual boot machine, WinXp and PClinuxos. I installed Ubuntu through windows. For some reason it will not bring up the desktop after logging in using Gnome Window Manager. It will however start up in KDE Window Manager. Problem is KDE Ubuntu has some glitches and I prefer to use Gnome desktop.
So I would like to to re-install or remove Ub. all together. But before i do this i need to know a few things:
1/ If i reinstall Ub. will it use the same partition that it created from the 1st install in windows?
2/If i do a "fixmbr", will i lose GRUB interface and not be able to login to PClinuxos?
Hopefully this sheds a little more light on my problem.
Thanks
del

---

### Post by ago on 2008-10-12
1 should be ok
2 fixmbr will overwrite the mbr so the primary bootloader will revert to the windows one.

---

