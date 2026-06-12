---
title: "Menus are messed up"
date: 2008-07-20
forum: General Help
---

### Post by suicidejack on 2008-07-20
So something wierd happened when I started up Ubuntu involving inodes which Ubuntu apeared to have fixed.  However, when my computer restarted and I got back to the gui I discovered that my menus are all messed.  From the System menu I am missing the administration item and the perferences item and from the Applications menu I am missing everything.  If anyone knows how to fix this please let me know since I have no clue how else to access administation or perferences.  Thanks in advance!

---

### Post by suicidejack on 2008-07-22
Anybody? Help?

---

### Post by Het Irv on 2008-07-22
If you can get to the terminal, try ```
alacarte
``` that should bring you up to the menu editor.  You may be able to fix it there.

---

### Post by iaculallad on 2008-07-22
Try to reset it to it's default setting: On your terminal:

```
sudo rm -fr .gconf/ .gconfd/ .gnome2/ .gnome2_private/
```

And logout from your account then log back in.

---

### Post by suicidejack on 2008-07-22
Neither worked although, iaculallad's suggestion set everything back to the default although my the menus...

---

### Post by iaculallad on 2008-07-22
What about deleting the Top panel menus and replacing it with a new Menu:

Right-click on the "Applications" menu, select "Remove from Panel". Then right-click again on the top panel and select "Add to Panel", select "Menu Bar" under "Utilities" section and click on Add button.

---

### Post by suicidejack on 2008-07-22
Still nothing.  This is the weirdest problem...

---

### Post by Het Irv on 2008-07-22
Did you get the gui application for the menus when you typed that command?  If so was everything checked?

I *may* have miss typed the command  :oops:

---

### Post by suicidejack on 2008-07-22
Yea, the command I think is actually alacarte but I did't get a gui still but synaptic is telling me I have it installed.  Is there a folder that holds the menu choices by any chance?  I haven't found anything online like that but does anyone know of this?

I also can't figure out how to access my terminal now since the reset got rid of all my quick launch icons :(

---

### Post by Het Irv on 2008-07-22
Yup that is the command I meant to type, and the folder you are looking for is what iacuallad told you to delete.  At least that is your copy, I don't know where it gets created from

---

### Post by suicidejack on 2008-07-22
In that case...I'll probably end up reinstalling Ubuntu then.  Slightly annoying but at least I backed up the home folder so shouldn't be too bad.  Thanks for trying to help.  I think when the inodes problem started it somehow messed up my menu connections.

---

