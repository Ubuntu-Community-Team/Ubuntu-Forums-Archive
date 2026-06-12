---
title: "how to change default program association for certain mime types from terminal"
date: 2008-08-23
forum: General Help
---

### Post by linuxed on 2008-08-23
How can I change the default program that's associated with a specific mime type from the terminal?  I'm currently using KDE so if I were to use the gui I would right click on a file, select "Open with", then select "Other".  I would then select the new program to associate with the file type and then check the "Remember application association" box.  I know there has to be a way to do this from the command line, but I've been searching for a couple of hours now and the closest command I've found is the update-alternatives command.  Is there a command in ubuntu similar to the one below?

set-mime application/x-zip /path/to/newProgram

---

### Post by aloshbennett on 2008-08-23
The settings are basically in the /etc/mailcap and /etc/mime.types folder.

man run-mailcap would be a starting point, I guess.

---

### Post by mb_webguy on 2008-08-23
I can't answer your question, but maybe I can point you in the right direction...

The terminal (or rather the shell) is lower-level than the desktop manager, and what you're talking about is, I believe, at the desktop manager level.  So you need to change a KDE configuration file somewhere.  In Gnome, you would need to edit the /etc/gnome/defaults.list file.  I'm sure there's a similar file for KDE, but I'm not familiar enough with KDE to tell you.

---

### Post by linuxed on 2008-08-23
Thanks for your responses.  Unfortunately I still can't seem to find the configuration file in KDE.  I've searched for the defaults.list file but apparently KDE doesn't use it.  I also checked the mailcap and mime.types files, but they don't specify the default applications.  They only define the mime types.  I did find a mimeapps.list file in the /home/username/.local/share/applications folder, but after changing a few of the entries in that file it didn't seem to have any effect.  I seem to be out of ideas.  Any other ideas where the KDE configuration file might be stored?

---

