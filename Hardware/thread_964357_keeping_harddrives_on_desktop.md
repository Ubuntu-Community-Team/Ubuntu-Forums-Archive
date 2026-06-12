---
title: "keeping harddrives on desktop"
date: 2008-10-30
forum: Hardware
---

### Post by relaxedcrazyman on 2008-10-30
hey guys, noober question, but is there i way i can keep my other harddrives showing up on my desktop after restarting and such?

---

### Post by mkarnicki on 2008-10-31
Here you go :)
```

sudo apt-get install pysdm
```

It's a Storage Device Manager available also from Applications->Add/Remove->System tools category. After installation you'll find it in System->Admin. Once you mount the partitions from that app, they'll get mounted automatically after the boot (the checkbox is ticked in the Assistant (you'll find it). If you want to write to them also, uncheck the option "Mount file system in read-only mode".

Works for me, and you've got GUI, no need for editing fstab :)

---

### Post by relaxedcrazyman on 2008-10-31
worked like a charm, thanks a bundle!

---

### Post by mkarnicki on 2008-11-01
Your welcome :) You can mark this thead as SOLVED by chosing this option from "Thread tools" at the top right side of the thread.

---

### Post by relaxedcrazyman on 2008-12-02
i bought a new external drive, and when i plug it in, "Cannot Mount Volume, You are not privileged to mount the volume 'My Book'." and when i go through storage device manager, i set the options for the assistant, but when i click on mount, nothing happens, i have tried a couple of times, but still nothing

---

### Post by mkarnicki on 2009-03-11
I didn't see your post before, probably you have solved your problem already..

You could try this: Alt+F2, type:
```
gksudo pysdm
```
..and it should work.

---

