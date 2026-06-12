---
title: "Can Not Copy To iPod Nano"
date: 2008-10-30
forum: General Help
---

### Post by Rodney9 on 2008-10-30
Hello,
I have gpodder, gtkpod, hfsplus and hfsutils installed,I can mount and see all the files on the ipod, but I can not copy podcasts to my original nano ipod, what am I doing wrong ?

Rodney.

PS, I have searched, everyone seems to suggest to use windows to format, I only have a old mac machine.

---

### Post by Wayne_V on 2008-10-30
For the nano you need to make sure libgpod is a fairly recent version -- at least 0.6.0 I think (wouldn't swear to that but mine is 0.6.0-3ubuntu3.  

The nano should show up in the left pane in gtkpod.  Right-click and Edit iPod Properties and make sure the model number is correct.

Then you can do File->check iPod files or File->create iPods directories.  Then there should be no problem copying podcasts.   Might also try amarok or rhythmbox -- they both work well (and both use libgpod).

---

### Post by Rodney9 on 2008-10-30
**> SOLVED** Songbird told me I had to turn off 'Journaling'on the iPod by using 'Disk Ultilty' on a Mac, luckily my old mac still works and I turned off journaling. Now I can copy to the ipod with gpodder.

Rodney.

---

### Post by Rodney9 on 2008-10-30
**> SOLVED** Songbird told me I had to turn off 'Journaling'on the iPod by using 'Disk Ultilty' on a Mac, luckily my old mac still works and I turned off journaling. Now I can copy to the ipod with gpodder.:)

Rodney.

---

