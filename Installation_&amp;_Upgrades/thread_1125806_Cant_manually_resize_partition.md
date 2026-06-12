---
title: "Cant manually resize partition"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by ghanagareth on 2009-04-14
When I try to install ubuntu on pc, I want to install it as a partition side by side windows, however the only options I get are to install over the entire hard drive.  How to I get to adjust partitions option to show up?

---

### Post by inobe on 2009-04-14
you have to use gparted to resize the windows drive, defrag your hard drive first or windows will moan a groan about it's partition being shrunken.

here's an example video, enjoy [http://www.youtube.com/watch?v=JBfl3oViny8&feature=related](http://www.youtube.com/watch?v=JBfl3oViny8&feature=related)

---

### Post by ghanagareth on 2009-04-14
When I put in the ubuntu live cd, and go to the GParted, each time I alter the "free space following" as the video does, the resize/move option goes grey.

---

### Post by Mark Phelps on 2009-04-15
> **ghanagareth said:**
> When I try to install ubuntu on pc, I want to install it as a partition side by side windows, however the only options I get are to install over the entire hard drive.  How to I get to adjust partitions option to show up?

If you're using Vista, do NOT use GParted to shrink your Vista OS unless you have a Vista DVD handy.  Doing this risks corrupting your Vista OS which will then require you to reboot using the Vista DVD and run Startup Repair.

If you need some tips on shrinking the Vista OS, see the following link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

### Post by tamas305 on 2009-04-15
> **inobe said:**
> you have to use gparted to resize the windows drive, defrag your hard drive first or windows will moan a groan about it's partition being shrunken.

here's an example video, enjoy [http://www.youtube.com/watch?v=JBfl3oViny8&feature=related](http://www.youtube.com/watch?v=JBfl3oViny8&feature=related)

Sometimes using gParted to resize the Windows partition is fine but other times windows will vomit all over the place. I managed to use gParted and nothing bad happened but I cannot guarantee that windows is not going to randomly complain.

Also, defragging is good.

-tamas

---

### Post by lindsay7 on 2009-04-15
Be sure to unmount the drive. Right click on it and choose unmount or click on partition in the menu and click on unmount.

---

### Post by inobe on 2009-04-15
> **tamas305 said:**
> Sometimes using gParted to resize the Windows partition is fine but other times windows will vomit all over the place. I managed to use gParted and nothing bad happened but I cannot guarantee that windows is not going to randomly complain.

Also, defragging is good.

-tamas

yes you are correct, it's never a sure thing resizing anything that's why we assume most of everyone doing these things backup their personal data first.

---

### Post by ktechman on 2009-04-23
If you double tick on the partition gparted may tell you that the NTFS volume needs a chkdsk c: /r I believe the message read that some of the contents of the volume were unreadable when I encountered the same situation.

---

