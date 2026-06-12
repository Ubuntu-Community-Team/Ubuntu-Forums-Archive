---
title: "[SOLVED] Cannot get Wine fully removed from Ubuntu"
date: 2008-10-27
forum: General Help
---

### Post by JC0124 on 2008-10-27
I used wine for a while but I have a dual boot so at the moment I see no need for it.  I went to add/remove applications and followed the steps there, but when it was done Wine was still under applications and not fully removed.  I tried restarting but still there.  Any ideas?

Also why is it when I try to delete files such as I had installed eclipse once and unistalled it and a folder was left behind I can't remove it.  I always get a permissions error.

Sorry very new to Linux and Ubuntu both.

---

### Post by qpieus on 2008-10-27
> **JC0124 said:**
> I used wine for a while but I have a dual boot so at the moment I see no need for it.  I went to add/remove applications and followed the steps there, but when it was done Wine was still under applications and not fully removed.  I tried restarting but still there.  Any ideas?

Also why is it when I try to delete files such as I had installed eclipse once and unistalled it and a folder was left behind I can't remove it.  I always get a permissions error.

Sorry very new to Linux and Ubuntu both.
Regarding the deleting of the leftover folder - Where is this folder located? You can only (normally) delete files and folders that are in your /home directory. Files and folders outside your home CAN be deleted if you use the sudo command. Sudo gives you what is called superuser powers, so you could then delete stuff outside your /home.

Regarding the wine leftover - do you mean there is a wine entry in a menu? If that's the case you can edit the menu manually and remove the wine entry. I don't use gnome, so I don't know the exact way for you to edit the menu, but I'm sure someone else can jump in here and tell you...

---

### Post by JC0124 on 2008-10-27
Thank you for the help.  Your suggestions worked.

---

### Post by qpieus on 2008-10-28
You're welcome - I'm glad you solved it.

---

