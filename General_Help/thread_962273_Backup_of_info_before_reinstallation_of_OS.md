---
title: "Backup of info before reinstallation of OS"
date: 2008-10-29
forum: General Help
---

### Post by GabrielWolff on 2008-10-29
Hey, I want to reinstall Ubuntu but keep my passwords, configurations etc.

I do NOT want to keep all the applications I have installed.

Is there a comprehensive list of all the folders I should backup? Or maybe a script?

I found a few threads about it, but it seems like everyone has such different ideas about what should be backed up...

---

### Post by TeXtonyx on 2008-10-29
[https://launchpad.net/sysres/trunk/1.0](https://launchpad.net/sysres/trunk/1.0)
Sysres is a system restore program for Debian GNU/Linux based 
systems (especially Ubuntu). It can create named restore points 
and be customized to include user defined settings. It backs up 
grub settings, repository settings, video settings [xorg.conf],
and fstab by default. These areas seem quite important. 

[https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)
This works for the (great) Firefox browser and stores passwords also.

---------------------------------------------------

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backups+include](http://ubuntuforums.org/showthread.php?t=35087&highlight=backups+include)
A kitchen sink method and lots of discussion.

---

### Post by peter_brewer on 2008-10-29
If you go to your home folder and show all hidden folders, then copy everything.

Most settings are stored in those hidden folders.

---

### Post by GabrielWolff on 2008-10-29
> **TeXtonyx said:**
> [https://launchpad.net/sysres/trunk/1.0](https://launchpad.net/sysres/trunk/1.0)
Sysres is a system restore program for Debian GNU/Linux based 
systems (especially Ubuntu). It can create named restore points 
and be customized to include user defined settings. It backs up 
grub settings, repository settings, video settings [xorg.conf],
and fstab by default. These areas seem quite important. 

[https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)
This works for the (great) Firefox browser and stores passwords also.

---------------------------------------------------

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backups+include](http://ubuntuforums.org/showthread.php?t=35087&highlight=backups+include)
A kitchen sink method and lots of discussion.

So basically all I really need, are those:
1) My personal files like odt's videos, music etc
2) My bookmarks and passwords from my browser
-
3) /etc/fstab
4) /boot/grub/menu.lst
5) /etc/X11/xorg.conf 
6) /etc/apt/sources.lis

With these 6 backups and an installation CD I can restore my OS as it is now (excluding the programs)?

---

### Post by sdennie on 2008-10-29
What I've done in the past is backup /home and /etc.  Actually, I don't backup /home but instead create it on a separate partition from the rest of the OS so I can re-install without having to wipe it (if I'm not mistaken the Hardy installer may know how to do this without having to manually create a /home partition).  For /etc, I create a .tar of the whole thing and later drop in files that contain things I've modified.  The reason I do /etc this way is because it's small and I never remember what files I've edited so it's nice to at least have a reference point of how your system was previously configured.

---

### Post by GabrielWolff on 2008-10-29
> **vor said:**
> What I've done in the past is backup /home and /etc.  Actually, I don't backup /home but instead create it on a separate partition from the rest of the OS so I can re-install without having to wipe it (if I'm not mistaken the Hardy installer may know how to do this without having to manually create a /home partition).  For /etc, I create a .tar of the whole thing and later drop in files that contain things I've modified.  The reason I do /etc this way is because it's small and I never remember what files I've edited so it's nice to at least have a reference point of how your system was previously configured.

1) In that case /boot/grub/menu.lst would not be backed up. How important is that?

2) Would this work even if I created the back up in 8.04, install 8.10 ad then copy /etc into the newly installed OS?

---

### Post by sdennie on 2008-10-29
> **GabrielWolff said:**
> 1) In that case /boot/grub/menu.lst would not be backed up. How important is that?


Unless you've modified that file by hand, the interesting bits are automatically generated whenever a new kernel is installed.  Also, if you are changing your partition layout during the new install, the UUIDs of the partition won't be the same so menu.lst won't be valid anyway.

> 
2) Would this work even if I created the back up in 8.04, install 8.10 ad then copy /etc into the newly installed OS?

Do *not* do that.  You've probably changed very few files in /etc so I would recommend accepting the default /etc you get after an install and then copying over individual files from your /etc or copy/paste snippets of files to the new /etc.  You may not even need your /etc backup but, it's nice to have a reference point of something you know was working.  Blindly untarring a new /etc ontop of a clean one will probably break your machine.

---

### Post by TeXtonyx on 2008-10-29
I think that if you've downloaded any drivers, that it would be 
more efficient to back them up, than to download them again, if one
knows they will nearly always be needed. Applications aren't quite
like that unless there are crucial ones you always want to install.
I mean those from a manufacturer website rather than a repository.

---

### Post by GabrielWolff on 2008-10-29
> **TeXtonyx said:**
> I think that if you've downloaded any drivers, that it would be 
more efficient to back them up, than to download them again, if one
knows they will nearly always be needed. Applications aren't quite
like that unless there are crucial ones you always want to install.
I mean those from a manufacturer website rather than a repository.

So if I don't remember which drivers I installed - is there a way of finding them conveniently?

I HAVE installed a few - but I can hardly remember which...

---

### Post by GabrielWolff on 2008-10-29
> **vor said:**
> Do *not* do that.  You've probably changed very few files in /etc so I would recommend accepting the default /etc you get after an install and then copying over individual files from your /etc or copy/paste snippets of files to the new /etc.  You may not even need your /etc backup but, it's nice to have a reference point of something you know was working.  Blindly untarring a new /etc ontop of a clean one will probably break your machine.

So how do I take my configurations with me to 8.10?
Is the list of files I posted previously, minus the /boot/grub/menu.lst right?

---

