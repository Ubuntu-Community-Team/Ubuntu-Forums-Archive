---
title: "how do u hide desktop icons"
date: 2008-08-11
forum: General Help
---

### Post by chrismitt2002 on 2008-08-11
like the title says how do u hide desktop icons ive never tryed this so i relly have not clue how to do it any help would be great

---

### Post by asphixmx on 2008-08-11
Press ALT-F2. Then write gconf-editor and press ENTER. Go to apps/nautilus/desktop. Then check/uncheck what you want to see on desktop.

---

### Post by coffeecat on 2008-08-11
Open a terminal, and type:

```
gconf-editor
```

Now go to apps > nautilus > desktop. Tick or untick the ones you want on or off. I guess you meant the 'volumes_visible' (mounted drives) because, as far as I remember, these are the only ones switched on by default in Ubuntu.

---

### Post by Vivaldi Gloria on 2008-08-11
Press ALT+F2 and start gconf-editor and look at the keys in

```
/apps/nautilus/desktop/
```

If you are talking about hard drive icons only then the better way to do it is to mount your filesystems (partitions) in /mnt/mountpoint using fstab. This will stop desktop icons.

Then you can put symlinks to where ever you want. Also you can add it to places menu by opening a nautilus window and dragging the folder icon to the places pane on the left.

---

### Post by adityavpratap on 2010-04-02
Probably the simplest way would be to create a backup directory to move all the items in your Desktop folder into -
$ mkdir desktop_backup
$ mv Desktop/* desktop_backup
Then you can start gconf-editor proceed to apps->nautilus->desktop and uncheck those items you don't want to be visible on the desktop, like mounted volumes, etc.
If you want them back -
$ mv desktop_backup/* Desktop

And yes, this isn't probably a neat way to do it, but it gets the thing done. ;-)

---

