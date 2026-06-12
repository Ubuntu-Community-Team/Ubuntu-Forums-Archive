---
title: "How to delete a folder in /media?"
date: 2008-07-16
forum: General Help
---

### Post by badaveil on 2008-07-16
Newbie me had been flumbing my way trying to mount a device(sec.hard disk) and eventually succeeded. However, I ended creating 2 unnecessary folders i.e. /media/disk-1 and /media/disk-2. I tried GUI way to delete them but not possible. Anyone knows how to get rid of them??

---

### Post by scragar on 2008-07-16
```
sudo rmdir /media/disk-1 /media/disk-2
```

---

### Post by iaculallad on 2008-07-16
> **badaveil said:**
> Newbie me had been flumbing my way trying to mount a device(sec.hard disk) and eventually succeeded. However, I ended creating 2 unnecessary folders i.e. /media/disk-1 and /media/disk-2. I tried GUI way to delete them but not possible. Anyone knows how to get rid of them??

On your terminal:

```
 sudo rm -rf /media/disk-1
 sudo rm -rf /media/disk-2

```

---

### Post by scragar on 2008-07-16
> **iaculallad said:**
> On your terminal:

```
 sudo rm -rf /media/disk-1
 sudo rm -rf /media/disk-2

```

:( empty folders should never be deleted with rm -f, and since they are empty the -r is useless(remember, they were created by mounting things to them, since the contents are no longer mounted it's empty). That is not to say your code is worthless, it's just that it should not be used for empty folders(great if it's a full folder without dangerous links though).

---

### Post by jonian_g on 2008-07-16
Open a terminal and type:

sudo nautilus

It will open the file manager with root permissions.

Navigate to the /media folder and you will be able to delete them.

PS: If you want a GUI way to mount partitions, go to add/remove and install Storage Device Manager.

---

### Post by badaveil on 2008-07-16
God, you guys are fast in reply. I'm still in the office and now I can't wait to get home. Gee thanks

---

### Post by jonian_g on 2008-07-16
> Open a terminal and type:

sudo nautilus

Forgot to tell you:

To do it faster, press Alt+F2 and type

gksudo nautilus

---

### Post by badaveil on 2008-07-17
> **scragar said:**
> ```
sudo rmdir /media/disk-1 /media/disk-2
```

Works like a charm

---

### Post by ujohntu on 2012-07-09
I don't recommend using Device Manager because it's too easy to screw something up and make your attached devices unbootable - I uninstalled mine.  It's better to just run the sudo commands, nautilus or Rmdir '[path/foldername]' from a terminal window. Note that path and folder names are case-sensitive and should be enclosed in apostrophies.

---

### Post by oldos2er on 2012-07-09
Old thread closed.

---

