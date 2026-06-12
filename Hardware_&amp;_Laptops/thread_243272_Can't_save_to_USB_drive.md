---
title: "Can't save to USB drive"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by wyth on 2006-08-24
I have a memorex USB drive that for some while now I've not been able to save anything to.   It's fat32, and works under Windows, but nothing will copy to it under Kubuntu.  It mounts fine, and I can read whats on it, and when I copy something to the drive it *looks* like the file copied, but when I remove the drive and plug it in again, the file is never there.

This is happening on my laptop and my desktop, both Kubuntu, so this must be some setting problem.  I don't think it's the drive, though, because it works fine under Windows.

Any ideas?

---

### Post by meng on 2006-08-24
Are you unmounting the drive before you remove it? Linux doesn't actually write disk changes until you unmount. This apparently reduces wear on the drive (I'm told). If you just pull out the stick without unmounting, then no changes will persist.

---

### Post by wyth on 2006-08-24
Now is there an icon for slapping oneself in the forehead?  Because that worked perfectly.  I never even checked into "remove safely," but found it in the menu.

Cheers.

---

### Post by meng on 2006-08-24
Not to rub it in, but I would advise you to "remove safely" when using windows also. Most of the time it doesn't matter, but the one time it does matter will be when you lose something irreplaceable.

---

