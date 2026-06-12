---
title: "Thumbnail but no image"
date: 2008-11-17
forum: General Help
---

### Post by gmalac on 2008-11-17
Hi everyone,
An annoying thing that have bugged me for awhile. I connect to a share, say via Samba or just plain nfs, to browse an image directory located on another machine on my home network.
All boxes are Ubuntu 8.04 or 8.10
But all I see are thumbnails, I cannot see the images themselves (see screenshoot attached). Which is totally useless.
Would you know how I could display the images?
Thanks in advance
Guy

---

### Post by OldGrey on 2008-11-17
I notice that all the thumbnails are of jpeg images. It could be that the files are too large to have the thumbnails displayed. I am not in front of my Ubuntu PC at the moment, but if you look in Nautilus preferences there is an option to change the minimum size. I think the default is 5MB which is too small for most of my photos, but a change to 10 fixes the problem.

---

### Post by mgmiller on 2008-11-17
Open your home folder and then click on Edit > Preferences.
Go to the "Preview" tab and make sure that not only are the file sizes in "Other Previewable Files"  is set to an appropriate size, but that the "Show Thumbnails" drop down is set to "Always" instead of "Local Files Only".

---

### Post by gmalac on 2008-11-18
Yeah! the trick on the preferences did it!
Thanks to both of you, you're great!
Guy

---

