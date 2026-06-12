---
title: "windows crashed with ifs driver running now i cant see my HDDs"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by bmwerks on 2007-11-03
i was running windows when it crashed, then i booted into linux and it force checked the disk then started fine, 

well i thought so at least, it didn't automount the disks to the desktop so i went into "/media/" to mount them manually, i double-click on the drives and they don't show any content.

they displayed 1.7gb free which is wrong it says this for all of them which is the actual free space of the drive ubuntu is installed on.

in computer:/// it actually shows my third hdd but when i try to access it it say unable to mount and gives an error saying: $mftmirr does not match $mft (record 0)...

I tried restarting and that made my desktop resize but a couple more restarts fixed that problem but i still cant get into anything plz help [-o<

---

### Post by bmwerks on 2007-11-04
i solved the problem the logfiles on the HDDs had them as in use so i had to force mount them and i have windows running again

needed to use the livecd to see that what the problem actually was and it proved the solution too.

---

