---
title: "The mysterious Deleted Items Folder is back again... Why?"
date: 2008-07-26
forum: General Help
---

### Post by indiworks on 2008-07-26
After having some (minor?) problems with the 64-Bit 8.04 Ubuntu version I started over again with the 32-Bit version about three weeks ago. This one seems much more stable on my system, but again after a while the "Deleted Items Folder" replaced my Trash. Why is this happening and how can I get the real Trash back? (I already asked once, but this solution via Nautilus only seems to get the icon back on the desktop. I still had to rename the icon from "Deleted Items Folder" to Trash by hand.)

This is a bit confusing since now it is called "Wastebasket - File Browser", "Empty Deleted Items" and the path is "trash:///". In the About information it says: "A GNOME Deleted Items folder that lives in your panel. You can use it to view the waste or drag and drop items into the Deleted Items folder." Unfortunately it does not say how-to remove it... I also keep wondering what "Deleted Items Folder" really means: how can I move something to a folder that has items in it that are already deleted...? Or is it meant for items that you don't really want to delete and recover later...? Only the warning message when deleting the items suggests this is just like the Trash...

Any ideas how the Deleted Items Folder gets there and how I can get the real Trash back? There are a couple of system updates I want to install but I'd like to make sure that nothing is broken before I do that. Thanks.

---

### Post by Jack Harkness on 2009-03-06
This same thing just happened to me.  Judging by the age of your post, I guess no one's figured out why?

---

### Post by dcstar on 2009-03-06
> **Jack Harkness said:**
> This same thing just happened to me.  Judging by the age of your post, I guess no one's figured out why?

Applications-System Tools-Configuration Editor:

```
/apps/panel/default_setup/applets/trashapplet
/apps/panel/applets/trashapplet_screen0
```

---

