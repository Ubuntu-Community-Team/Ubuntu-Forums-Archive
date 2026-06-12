---
title: "Where to place manually installed apps?"
date: 2008-07-31
forum: General Help
---

### Post by mrmorris on 2008-07-31
Let's say I have a simple binary executable stuff from tar.gz. Where is the common/de-facto location of Ubuntu to place this so that it's available to all users just as if it had been a package based install?

---

### Post by loboc on 2008-07-31
/usr/local/bin

---

### Post by mrmorris on 2008-07-31
Thanks, I suspected that but then again much seems to be placed in various other places as well. 

Follow up question, when copying to these out-of-home places you need to have write access. Is there a way to have Gnome file manager (Nautilus) pop-up a su dialog rather than having to drop to a console all the time for these things? After all, many other programs (i.e. Synaptic) simply pop-up such a dialog.

---

### Post by estyles on 2008-07-31
> Follow up question, when copying to these out-of-home places you need to have write access. Is there a way to have Gnome file manager (Nautilus) pop-up a su dialog rather than having to drop to a console all the time for these things? After all, many other programs (i.e. Synaptic) simply pop-up such a dialog.

Make a launcher on the Desktop with commandline "gksudo nautilus".  Also, you could create a Nautilus-Action to do it by right-clicking on a folder, but as I'm not at home, I can't give you the exact syntax.

a) It requires nautilus-actions to be installed.  If you don't see it in your System->Preferences, then you might need to install it from Synaptic.

b) The action you want to set up would be called something like "Open As Root", the "path" would be "gksudo nautilus", and the other text box (parameters?) would be %d, or %d/%f... or something like that...   I can't recall the exact syntax.  You want to set it to work on "folders only", and do not allow multiple selections.  Mint uses a nautilus-action like this  in the default install, but it opens xfe instead of nautilus for the root window - this is to make sure that your root windows look different from your regular windows, so you're aware you're browsing as root.  You don't want to forget that you've done this and leave a root window open on your desktop.

The "gksudo nautilus" launcher is much simpler, although creating a nautilus action can be more flexible.

---

