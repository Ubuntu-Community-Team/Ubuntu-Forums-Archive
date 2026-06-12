---
title: "triple boot uninstall question"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by nmatheis on 2006-02-04
hello

i''ve got winxp pro 64bit and ubuntu 64bit that i want to keep.  i've also got kanotix.  i installed kanotix last, so it's got the active grub.  i want to get rid of kanotix and just stick with the x/k/ubuntu flavors, so i've installed kubuntu-desktop and will use some coding from [http://www.ubuntuforums.org/showthread.php?t=59455]("http://www.ubuntuforums.org/showthread.php?t=59455") to clean up menus in for the gnome/kde log-ins.  

so, i was thinking of reformatting the partition containing kanotix and resizing the ntfs format with windows to incorporate the freed hd space.  if i do this, will i still be able to get to winxp and k/ubuntu?  i mean, will the grub default to the old ubuntu grub once the kanotix grub is gone?  any help/reassurances would be appreciated!!!

thanks :)
nikolaus

---

### Post by taurus on 2006-02-04
I recommand you boot your Ubuntu and install it own version of GRUB!  Then, wipe out kanotic once you know you can boot both Ubuntu and XP with it...  Probably the safest way to go about.

---

### Post by nmatheis on 2006-02-04
[QUOTE=taurus]I recommand you boot your Ubuntu and install it own version of GRUB!  Then, wipe out kanotic once you know you can boot both Ubuntu and XP with it...  Probably the safest way to go about.[/QUOTE]

thanks for the reply!  so how would i go about this?  in ubuntu's /boot/grub/ i can see /boot/grub/menu.list  i can see one in the kanotix /boot/grub, as well  in the ubuntu file, i only see the ubuntu linux kernels and winxp listed.  what do i do to make that the default file for the grub?

thanks!
nikolaus

---

### Post by lha on 2006-02-04
[QUOTE=nmatheis]thanks for the reply!  so how would i go about this?  in ubuntu's /boot/grub/ i can see /boot/grub/menu.list  i can see one in the kanotix /boot/grub, as well  in the ubuntu file, i only see the ubuntu linux kernels and winxp listed.  what do i do to make that the default file for the grub?

thanks!
nikolaus[/QUOTE]
See [this thread for instructions to re-install grub]("http://ubuntuforums.org/showthread.php?t=76652").

---

### Post by nmatheis on 2006-02-04
thanks, i'll give it a try if i can resolve my gmenu/kmenu issues described here: [http://www.ubuntuforums.org/showthread.php?t=123969&page=2](http://www.ubuntuforums.org/showthread.php?t=123969&page=2)

---

### Post by nmatheis on 2006-02-05
performed a reinstall of ubuntu to quickly get my menu mess straighteed out.  no more boot problems.  thanks!
nikolaus

---

