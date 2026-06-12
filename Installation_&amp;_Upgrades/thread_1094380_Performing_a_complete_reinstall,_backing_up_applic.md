---
title: "Performing a complete reinstall, backing up applications and preferences"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by dep01 on 2009-03-12
Hello. I've been running Ubuntu in parallel with Vista (via dual boot) for a couple weeks now and I am ready to make the dive in to full-on Ubuntu.  I'd like to take advantage of all the space I have allocated for the Vista partition since all I use it for is a couple pieces of software dependencies.  I figure once I rebuild Ubuntu, I can get VMWare running for when I need to drop in to Windows for anything.

The thing I'm wanting most to do is to back up my entire Ubuntu system, the installed applications and user preferences (look and feel, software preferences, etc).

I just want to make sure I've thought of everything.  For backing up the applications, I'm going the route of this thread here:
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

and for backing up my user preference, I'll be booting to the Live CD and just simply archiving up my entire home/user folder (with all hidden/system files as therein). ([http://brainstorm.ubuntu.com/idea/10847/](http://brainstorm.ubuntu.com/idea/10847/))

once I do the fresh install, I can follow the steps outlined in the first link ([http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)) and then, back on the live CD, copy my home folder over the fresh install home folder.

Will I be home free at that point?  Anything I'm missing?

Thanks for any guidance. These forums are terrific.

dep

---

### Post by dannyboy79 on 2009-03-12
well, any modifications to config files you made will also need to be backed up. If you use ssh, samba, etc. All those files are stored within there respective /etc/ folder. Example: you would want a backup copy of your /etc/samba/smb.conf for samba and you would want a backup of /etc/ssh/sshd_config

good luck

---

### Post by dep01 on 2009-03-12
> **dannyboy79 said:**
> well, any modifications to config files you made will also need to be backed up. If you use ssh, samba, etc. All those files are stored within there respective /etc/ folder. Example: you would want a backup copy of your /etc/samba/smb.conf for samba and you would want a backup of /etc/ssh/sshd_config

good luck

Thanks.  Should I pick and choose individual files from the folder or can I backup/restore the entire thing?

dep

---

