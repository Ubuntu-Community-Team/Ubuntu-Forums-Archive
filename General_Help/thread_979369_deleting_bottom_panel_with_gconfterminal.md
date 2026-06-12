---
title: "deleting bottom panel with gconf/terminal"
date: 2008-11-11
forum: General Help
---

### Post by LinuxRules1 on 2008-11-11
i'm working on a script that will make ubuntu look like a mac but i need to delete the bottom panel through terminal. does anybody know how to do that? i deleted the folder bottom_panel_screen0 in /home/jason/.gconf/apps/panel/toplevels but when i restart the system the bottom panel is at the top and the file i deleted came back. any help will be appreciated. thanks  :)

---

### Post by eternalnewbee on 2008-11-11
After you've deleted the panel go to: **Main Menu > System > Administration > Preferences > Sessions > Options**, and click **Remember Currently Running Application**

---

### Post by LinuxRules1 on 2008-12-03
That worked but now the only problem is i don't know how to do that in terminal. I'm hoping to have the script install the mac theme automatically.

---

### Post by loomsen on 2008-12-03
Either edit the file ~/.gconf/desktop/gnome/session/%gconf.xml and change/remove the entry where panel is specified, or just make a .gz out of your gnome-panel.

sudo gzip /usr/bin/gnome-panel

To restore simply run 

sudo gunzip /usr/bin/gnome-panel.gz

---

