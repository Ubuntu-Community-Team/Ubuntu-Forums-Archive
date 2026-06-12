---
title: "Rhythmbox library"
date: 2005-11-16
forum: General Help
---

### Post by cbudden on 2005-11-16
For some unknown reason, some songs in Rhythmbox are coming up twice, there locations being /media/hda6 and /media/mydocs/ .  I do not have anything mounted under /media/hda6, and want to delete my current library and start afresh.  How can I completely remove the references in the library?

---

### Post by matthew on 2005-11-16
This will delete everything in the library.

Open rhythmbox and select "library" from the source list on the left.
Highlight any song in your songs list.
Click <ctrl><a> to select all the songs.
Rght click on the selected songs and select "delete" from the popup menu.

Then go to Music->Import Folder
Select the folder containing all your music (and music sub folders) and it will repopulate your library list with an accurate list of the contents of that (those) folders

---

### Post by cbudden on 2005-11-16
Ok, I found what I was looking for.  I looked for a folder named .rhythmbox in my home dir, but couldn't find it, then realised it is in .gnome2 folder!  Deleted the rhythmdb.xml file and all fixed.  Thanks.

---

### Post by phillipbeynon on 2008-01-07
Application:Rhythmbox 0.11.2
System:Ubuntu 7.10

Issue: Imported folders cannot be un-imported and continue to scan for new files.

TS: Highlighting all tracks (Ctrl - a) right click, remove. Removes tracks temporarily.  All imported folders are rescanned and tracks are added once again.

Resolution:

Warning: Other settings may be permanently lost using this method. This is blunt force trauma!

open home filder
Hit Ctrl + H to show hidden files/folders
open .gnome2
delete .rhythmdb.xml

All "import folder" entries are removed.  Only tracks in your "Library Location" will be scanned.

Prevention: Don't use "Import folder"! :)

---

