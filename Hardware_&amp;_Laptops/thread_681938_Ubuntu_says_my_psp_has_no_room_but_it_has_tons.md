---
title: "Ubuntu says my psp has no room but it has tons"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by shanesgc on 2008-01-29
Im trying to put a 400mb movie on my psp and it keeps telling me theres no room on the drive when i have almost 2gb's of free space! Anyone have any clue why?

EDIT: Im going to try to backup everything on the memory stick, format it, put everything back and try again..

EDIT2: Okay that worked. Before I did it I checked the properties of the PSP with ubuntu and it said it only has 363mb of free space. Any idea what cause a loss of 1700mb's?

---

### Post by Deived on 2008-02-01
Take a look at the root folder of the PSP and show hidden files (Ctrl +H).  If you deleted a bunch of stuff, sometimes Ubuntu doesn't remove them when you eject it.  If you have a folder named " .username_trash " that's the stuff that was deleted.  It's still on the PSP.  Just delete that folder and its contents and you'll free up the space.  
It used to prompt me to delete them when I ejected the drive, but it doesnt anymore so I have to manually delete the folder.  I'm sure there is a way to fix it, but I'm still a bit of a newb.

I hope that made sense.

---

### Post by shanesgc on 2008-02-04
I thought thats what it was too but there was barely anything in there. Its doing again now too! Psp say 1400mb's and ubuntu says 346? lol

---

### Post by mangurt on 2008-02-04
Did you send anything from the disk to trash?  If that's the case, empty the trash...that's usually what I do.
Hope it helps.

---

### Post by shanesgc on 2008-02-04
> **mangurt said:**
> Did you send anything from the disk to trash?  If that's the case, empty the trash...that's usually what I do.
Hope it helps.

Yeah I emptied the disks trash and that took care of 300mb's. What about the rest?

---

### Post by Foxray on 2008-02-04
You might want to try to take all the data off the card, reformat it and put it all back. My psp memory card was doing the same thing and that fixed it. It might work for you.

---

### Post by shanesgc on 2008-02-04
> **Foxray said:**
> You might want to try to take all the data off the card, reformat it and put it all back. My psp memory card was doing the same thing and that fixed it. It might work for you.

Lol done it twice. Just had to do it again and that fixes it but it always happens again.

---

### Post by ibanez on 2008-02-04
My sons did it as well, but I checked every game /iso folder and there was a hidden trash in one of them I think it depends on the location that you actually deleted the file.
Anyway now he knows to check the folders now he doesn't bother me anymore..

---

### Post by shanesgc on 2008-02-04
> **ibanez said:**
> My sons did it as well, but I checked every game /iso folder and there was a hidden trash in one of them I think it depends on the location that you actually deleted the file.
Anyway now he knows to check the folders now he doesn't bother me anymore..

Hmm next time i'll try that. Thanks for all the help guys!

---

### Post by Arlanthir on 2008-02-07
I have this problem too.
It always happens when I delete/download files with the PSP itself. It's like the free space doesn't update. Windows can read it good, nonetheless :S So what I do is open it on windows, write or delete something there and it's good to go on Ubuntu.

---

