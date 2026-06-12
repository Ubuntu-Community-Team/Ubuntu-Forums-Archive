---
title: "Completely removing cairo dock"
date: 2008-09-23
forum: General Help
---

### Post by alex199020 on 2008-09-23
How do i do this? I've gone into synaptic and done a complete removal. Restarted re-installed and was met by my previous configuration. 
I then did the same and deleted the cairo folder and contents (/usr/include/cairo) and (/home/user/.cairo-dock)
I have not tried re-installing yet but have searched for files containing "cairo-dock" and came back with this 

> /home/alex/.cairo-dock
/home/alex/.config/autostart/cairo-dock.desktop
/usr/bin/cairo-dock
/usr/bin/cairo-dock-update.sh
/usr/bin/launch-cairo-dock-after-beryl.sh
/usr/lib/cairo-dock
/usr/share/cairo-dock
/usr/share/applications/cairo-dock.desktop
/usr/share/locale/fr/LC_MESSAGES/cairo-dock.mo
/usr/share/locale/ja/LC_MESSAGES/cairo-dock.mo
/usr/share/locale/zh_CN/LC_MESSAGES/cairo-dock.mo
/usr/share/menu/cairo-dock
/usr/share/pixmaps/cairo-dock.svg
/var/cache/apt/archives/cairo-dock-plug-ins_1.6.0.2_all.deb
/var/cache/apt/archives/cairo-dock_1.6.0.2_all.deb
/var/lib/apt/lists/repository.cairo-dock.org_ubuntu_dists_hardy_cairo-dock_binary-amd64_Packages
/var/lib/dpkg/info/cairo-dock-plug-ins.list
/var/lib/dpkg/info/cairo-dock-plug-ins.postinst
/var/lib/dpkg/info/cairo-dock-plug-ins.postrm
/var/lib/dpkg/info/cairo-dock-plug-ins.prerm
/var/lib/dpkg/info/cairo-dock.list
/var/lib/dpkg/info/cairo-dock.postinst
/var/lib/dpkg/info/cairo-dock.postrm
/var/lib/dpkg/info/cairo-dock.prerm
 

Do any of these need to be deleted in order to return my system to a state in which cairo dock had never been on it?
Thanks for the help!

---

### Post by nkri on 2008-09-23
Are you trying to completely reinstall with the default configuration?  If so, deleting /home/alex/.cairo-dock should do the trick.  You could also take a look at [_this_]("http://www.cairo-dock.org/ww_page.php?p=Uninstall&lang=en") page for all the different ways of uninstalling.

Good luck!
-nkri

---

