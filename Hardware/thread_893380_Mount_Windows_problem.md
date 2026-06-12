---
title: "Mount Windows problem"
date: 2008-08-18
forum: Hardware
---

### Post by detroit/zero on 2008-08-18
I screwed up.

I have a Vista partition on my laptop. I was just screwing around and gave it a fancy windows icon, and I got to looking around in the Properties dialog, and I saw the option to specify a mount point. I thought, "Yeah, cool - why have it come up as SQ004286V02 when I can label it 'Vista'?"

So I set the mount point to /media/Vista, unmounted the drive, and when I try to remount it I get an error message saying that "the mount point cannot contain the following characters: newline_G_DIR_SEPARATOR (usually /)".

Since I can't mount this drive now, where can I go to erase that change I made and let the drive mount again?

---

### Post by fogster74 on 2008-08-22
I'm no expert, but I have a feeling I can guess what may be going on...

Possible when you entered the mount point as 'Vista', you hit 'enter' and then clicked 'ok' when enter didn't work. Possibly Ubuntu appended the 'enter' as a 'carriage return' ('Newline_G_Dir_Seperator') into the mount point.

I'd take a look at fstab and see if this is stored there...?

Hope this helps and apologies if I'm miles off!

---

