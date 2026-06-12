---
title: "An empty desktop without icons"
date: 2008-07-23
forum: General Help
---

### Post by yootje on 2008-07-23
I have a pretty simple question: How can I disable all the icons on my desktop without actually deleting them? I still want the directory, I just don't want to have any icons on my desktop.

Thanks in advance!

---

### Post by tuxxy on 2008-07-23
Move the icon to another folder, or just delete it?

If you mean at the the taskbar then right clcik the icon and select remove

---

### Post by suarez.duek on 2008-07-23
I did this some weeks ago, first of the aplication throw them at the panels, they can be very useful if you set them at your will. Then the folders try to locate them at other folders beyond Desktop. Remember that nautilus can give a very good help organicing your files, it is very simple.

---

### Post by suarez.duek on 2008-07-23
Ho! and if you want it a little nicer try out Avant Window Navigator, it gives you more space in your desktop for sure!

---

### Post by jkyahoo101 on 2008-07-23
> **suarez.duek said:**
> Ho! and if you want it a little nicer try out Avant Window Navigator, it gives you more space in your desktop for sure!

...or the Cairo dock. It is a little bit more customizable in terms of location on your desktop.

---

### Post by yootje on 2008-07-24
It's not possible to just make all the icons on the desktop "invisible"? I don't want to delete or remove icons. Come on people, even in Windows XP this is possible within a few clicks.

---

### Post by aomlives on 2008-07-24
>  Open a terminal and enter

gconf-editor

Then when Configuration Editor opens up click apps then nautilus then desktop then volumes_visible.

Set it to false by unticking it. Then close it.Found this here: [http://ubuntuforums.org/showthread.php?t=249489](http://ubuntuforums.org/showthread.php?t=249489)

you were right that wasn't more difficult than XP :D

cheers

---

### Post by yootje on 2008-07-25
> **aomlives said:**
> Found this here: [http://ubuntuforums.org/showthread.php?t=249489](http://ubuntuforums.org/showthread.php?t=249489)

you were right that wasn't more difficult than XP :D

cheers

Unfortunately this isn't really what I asked for, but it helped me one step in the right direction :) If I would delete all the files in the Desktop folder this would do the trick, but I don't want that :) Thanks anyway!

---

### Post by Archmage on 2008-07-25
Xubuntu has a icon-less desktop.

---

### Post by northern lights on 2008-07-25
"nautilus" is not only the standard gnome file-manager, but it also draws the desktop.
Run ```
gconf-editor
``` and navigate to "/apps/nautilus/" under "/apps/nautilus/desktop" you can disable standard icons. Under 
"/apps/nautilus/preferences" you can uncheck "show desktop" to prevent nautilus from drawing one at all.

If you're running compiz, you can set the wallpaper(s) there.

---

### Post by yootje on 2008-07-25
> **northern lights said:**
> "nautilus" is not only the standard gnome file-manager, but it also draws the desktop.
Run ```
gconf-editor
``` and navigate to "/apps/nautilus/" under "/apps/nautilus/desktop" you can disable standard icons. Under 
"/apps/nautilus/preferences" you can uncheck "show desktop" to prevent nautilus from drawing one at all.

If you're running compiz, you can set the wallpaper(s) there.

Thanks!

---

