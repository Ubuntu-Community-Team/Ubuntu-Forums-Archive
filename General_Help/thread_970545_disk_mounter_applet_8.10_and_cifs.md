---
title: "disk mounter applet 8.10 and cifs"
date: 2008-11-04
forum: General Help
---

### Post by fiercefinn on 2008-11-04
Tabletubuntus question from a week ago from Intrepid Ibex Testing and Discussion (closed) that was not answered.

>I upgraded my toshiba satellite R25 tablet to intrepid today. Works great! >I now have sleep and suspend, which is awesome. Eveything else works fine >except the behavior of disk mounter applet has apparently changed. It use >to show all of the noauto network mounts that I have in /etc/fstab, so I >could easily right click and mount them. Instead, it now only appears to >show local drives. Does anyone know if I can get the applet to show the >unmounted cifs shares listed in /etc/fstab, or has this functionality been >deleted.

>Thanks much.

I have the same problem, I cannot find any settings to modify this behavior. Would someone know where to change it so that I can mount my cifs shares in 8.10 with the mounter applet.

---

### Post by W. Irving on 2008-11-05
I second this. The 2.24.1 version in Ibex does not display CIFS volumes defined in fstab. It ignores these 2 lines:

```
//engels/dokument /mnt/engels/dokument cifs dirsync,sync,user,noauto,credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0660,dir_mode=0770,auto,rw,noexec,uid=elias,gid=elias 0 0
//engels/trotsky-backup /mnt/engels/trotsky-backup cifs dirsync,sync,user,credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0660,dir_mode=0770,auto,rw,noexec,uid=elias,gid=elias 0 0

```

This appears to be a Gnome bug.
See bug reports:
[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/282922](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/282922)
[*][http://bugzilla.gnome.org/show_bug.cgi?id=555067](http://bugzilla.gnome.org/show_bug.cgi?id=555067)
[/LIST]
So not only is it still impossible to browse SMB shares through Nautilus, drivemount_applet2 is now of little use too.

Wasn't Ubuntu meant to be a better alternative than Windows?
Perhaps we should all go back to using the CLI - at least mount still works!

---

