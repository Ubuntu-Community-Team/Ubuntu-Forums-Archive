---
title: "File saved in ubuntu invisible in windows partition"
date: 2008-07-21
forum: General Help
---

### Post by adipradana on 2008-07-21
Hi guys,

I've downloaded a few files and saved it to different folders in my windows partition (fat32). When i logged in to my windows os, some but not all of the files that i've downloaded are missing. When i checked back to ubuntu, the files are still there. This has happened to me several times. Some files have no problem but some do. I can't figure out what i'm doing wrong.
What's going on? (I'm using hardy)

---

### Post by Polygon on 2008-07-21
have you tried enabling 'show hidden files and folders' in windows, and seeing if that makes the files appear?

---

### Post by adipradana on 2008-07-21
Yeah, tried showing hidden and system files already.
A friend said that it has something to do with hibernation in windows. If you hibernate in windows, then login to ubuntu and save a file to the windows partition, then the file is invisible. Haven't tried it out myself, but if i remember correctly, i saved a few files in sepereate folders. In folder "A" everything is normal but in folder "B" the files i saved in ubuntu is missing. So i'm not so sure it has anything to do with hibernation.

---

### Post by coffeecat on 2008-07-21
Two suggestions. Did you try clicking refresh in Windows Explorer? It's not a button as in Nautlius. It's in a menu somewhere - the one where you can re-order the way files appear in the browser Window. Sorry to be vague - I'm going from memory here.

The other suggestion is to reboot Windows - the cure-all for Windows problems! But if it's to do with hibernation I should imagine it is to do with the need to refresh. After a hibernation Windows is 'remembering' the state of the folder the last time it looked at it. With a reboot it will have to reread the contents of the folder. At least that's my theory. :)

---

### Post by vanadium on 2008-07-21
To refresh in Windows explorer, you can hit "F5" just as in nautilus. coffeecat explained the issue very well. You 'd better not hibernate Windows and then access the drive from within Linux.

---

