---
title: "Problems with flash drive and external HDD"
date: 2008-11-04
forum: General Help
---

### Post by Shay Guy on 2008-11-04
Okay, my flash drive normally shows up as /media/STORE'N'GO. However, currently, that seems to refer to an empty folder which I can't unmount, and which remains there even when I remove the drive. The drive itself is being recognized as /media/STORE'N'GO_, with an underscore. My external hard drive is doing the same thing. This is causing a variety of annoyances; what should I do?

---

### Post by Halfling Rogue on 2008-11-04
Did you try making a new mount point and trying to mount it there specifically?

I had a similar issue with my external hard drive showing up in my file system in Nautilus even after I'd unmounted and removed it; I had to right-click the drive and click "Unmount" there to get it to disappear, and even then it wouldn't always go away. I can't remember the exact details on how I fixed it, but it had something to do with my not having ejected the drive properly on a previous occasion, and Ubuntu subsequently trying to remount it in read-only mode.

If all else fails, you could try forcefully removing the empty folder and mounting it again?

---

### Post by Shay Guy on 2008-11-04
Well, my /media directory includes:

EXTHDD
STORE'N'GO
EXTHDD_
STORE'N'GO_

The first two are apparently empty, but read as having about the normal amounts of free space. Clicking "Unmount volume" does absolutely zilch. The latter two are acting normal, save for the wrong directory name.

---

### Post by Halfling Rogue on 2008-11-04
As far as I can tell, the folders are just persisting for some reason. They're only mount points created by the system, and since they're empty, it *should* be okay to use rm -rf to get rid of them... (Make sure you unmount the devices first, though, just in case your system is confusing them; and be careful using rm.) Then try mounting them again.

---

### Post by Shay Guy on 2008-11-04
Unmounted what I could and unplugged the drives. Then...

```
shaye@navi:/media$ rm -rf STORE\'N\'GO/
rm: cannot remove directory `STORE\'N\'GO': Permission denied
shaye@navi:/media$ sudo rm -rf STORE\'N\'GO/
[sudo] password for shaye: 
rm: cannot remove directory `STORE\'N\'GO': Device or resource busy
```

---

### Post by Shay Guy on 2008-11-05
Oh, lovely. I just came home and plugged the drives back into my laptop, and now there's also an EXTHDD__. Neither EXTHDD_ nor EXTHDD are working, but __ is.

---

### Post by Halfling Rogue on 2008-11-06
Yeah, sounds like what my drive was doing. Argh, I should have written down how I fixed it. I remember it having something to do with getting it out of read-only mode and then unmounting it properly (it was also having issues writing out stuff I'd taken off the drive and put in the trash).

Well, the next best bets I can think of are trying fuser to see if whatever is using the 'device' is a killable process, or try and see if fsck will fix things.

Sorry I'm not much more help.

---

### Post by Shay Guy on 2008-12-27
All right, the problems are still occurring. The only thing I've found that removes the fake drives is rebooting. I don't really know how to properly use fsck or fuser or a lot of the other tools -- can anyone lend some advice?

---

