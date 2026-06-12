---
title: "Audacity claims to already be running"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by LobbyDizzle on 2009-04-02
I got some info from another thread, but it was not exactly my case.

[http://ubuntuforums.org/archive/index.php/t-655264.html](http://ubuntuforums.org/archive/index.php/t-655264.html)

But in my case, when I run Audacity in the terminal, I get the error:

jared@jared-laptop:~$ audacity
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkMessageDialog::use-separator' of type `gboolean' from rc file value "((GString*) 0x9716090)" of type `GString'

I uninstalled and reinstalled Audacity with no luck.

I hope I provided enough information for one to assist me.

---

### Post by LobbyDizzle on 2009-04-03
d

---

### Post by WIREHEAD on 2009-04-18
Please BACKUP your Audacity files before you do this !
Be sure to include the .aup data files etc.


This worked for me : 

Use synaptic to uninstall audacity ( you have done this )

Open a terminal : 
type in the following commands ( > enter means press the enter key )

sudo updatedb           > enter ( updates database )

locate audacity         > enter ( lists all files with audacity in name )

gksudo nautilus         > enter

This will open a new file navigation window .
( At this point you are operating with ROOT authority ! )

Navigate to the files listed in the terminal window and send the audacity folders to the trash .

This file :
/home/yourusername/.audacity1.3-yourusername/audacity-lock-yourusername

Is the most likely suspect , but I trashed both folders just to be on the safe side .

***( you do NOT need to trash the files in  /var/lib/dpkg/info/  ! )

Reinstall Audacity with Synaptic .

Record some stuff ...

---

