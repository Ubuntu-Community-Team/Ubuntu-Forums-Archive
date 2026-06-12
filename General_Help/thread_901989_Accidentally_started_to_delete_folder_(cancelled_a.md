---
title: "Accidentally started to delete folder (cancelled almost immediately)/"
date: 2008-08-26
forum: General Help
---

### Post by emid on 2008-08-26
So I made an unfortunate mistake.  My finger slipped when I was browsing in nautilus, and I started to delete (**not move to trash**) a folder with somewhere between 80-100 GB of data on it.  I canceled the file operation almost immediately, but the folder still disappeared.  The interesting thing is that the amount of free space on my drive hasn't changed at all.

I'm basically left with a situation where my data appears to be gone, but I didn't get any of that 80-100 GB returned back as free space.  This makes me somewhat hopeful that my stuff is still technically on the disk.

If anyone can help me out I would really appreciate it!

---

### Post by iaculallad on 2008-08-26
Try using [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") if it could still recover those deleted files.

---

### Post by emid on 2008-08-26
> **iaculallad said:**
> Try using [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") if it could still recover those deleted files.

I'm trying what you recommended right now.  That being said I'm not feeling too confident.  The folder I deleted was basically all video files.  PhotoRec seems to be finding something, but it looks like it is putting it all together as one gigantic mpg.  I really don't think I had any mpg files that were 15 GB in that folder.  Maybe I'm speaking too soon.

It is just strange that canceling a delete operation would result in the folder disappearing, but the space that folder inhabited not being relinquished.

---

### Post by -Zeus- on 2008-08-26
are you sure it's not in trash???  please post the output of these commands

```
ls ~/.local/share/Trash
ls ~root/.local/share/Trash
```

---

### Post by emid on 2008-08-27
OK, I found most of it.  Apparently, in my spastic jump to cancel the accidental deletion, I somehow managed to drag the folder into another folder on the same drive.  :)

Thanks for the help anyways guys, I always appreciate it.

---

