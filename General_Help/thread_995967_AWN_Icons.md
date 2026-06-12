---
title: "AWN Icons"
date: 2008-11-28
forum: General Help
---

### Post by Bylund951 on 2008-11-28
im new to ubuntu,

with the avant window manager, i can add applets to it. then if reboot, all the applets i had added during my last session are gone. how can i make them permanently stay on the awn...

thanks.

---

### Post by joe74 on 2008-11-28
I had similar problems. All you have to do is go to /home/user/.gconf/apps and delete the **avant-window-navigator** folder, then log out an re-log in, it should reset the configuration directory of this.

An advice: don't remove the AWN Manager Icon... it seems it keeps configuration uptodate.

Good Luck!!

---

### Post by eternalnewbee on 2008-11-28
> im new to ubuntu,

with the avant window manager, i can add applets to it. then if reboot, all the applets i had added during my last session are gone. how can i make them permanently stay on the awn...

thanks.
 Hi there, and welcome to the Ubuntu Community.
Go to: **Main Menu > System > Preferences > Sessions > Options** tab, and click on **Remember Currently Running Application**.

---

