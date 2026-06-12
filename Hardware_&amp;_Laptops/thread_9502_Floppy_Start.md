---
title: "Floppy Start"
date: 2004-12-29
forum: Hardware &amp; Laptops
---

### Post by Sapper2ID on 2004-12-29
How do I access my floppy drive/what command and where to input that. I can format a floppy but don't know how to get it to show contents. I've gone into desktop prefs and checked all boxes next to removable storage but still no joy. Device manager says it's there and calls it a legacy floppy (it's a generic one).
 Will floppies made in windows be read in Linux?

---

### Post by nemin on 2004-12-29
[QUOTE=Sapper2ID]How do I access my floppy drive/what command and where to input that. I can format a floppy but don't know how to get it to show contents.[/QUOTE]
'mount /media/floppy0' is all you need. Just type that into the terminal. Then you can browse the floppy with your filemanager or do with it whatever you like.
I don't really like GUIs so I can't tell you how to do it that way :)
[QUOTE=Sapper2ID]
Will floppies made in windows be read in Linux?
[/QUOTE]
Yes, usually they are read without problems :)

---

### Post by Sapper2ID on 2004-12-29
Got it, thanks. 
 Shouldn't I have an icon under computer--disks section for easy access?
 Can I do this?

---

### Post by nemin on 2004-12-30
[QUOTE=Sapper2ID]Got it, thanks. 
 Shouldn't I have an icon under computer--disks section for easy access?
 Can I do this?[/QUOTE]
This icon appears when the floppy is mounted. I think it's possible to make some sort of "automount" icon, but I don't know how. Anyone?

---

### Post by Sapper2ID on 2004-12-30
I didn't realize I had diabled usb and floppy for installation of this OS. I screwed something up and had to reload ubuntu, I made sure floppy was enabled. Now I have an icon in disks that works just by double clicking it. No mount or unm. I guess I had a fortunate accident this time. Thanks

---

