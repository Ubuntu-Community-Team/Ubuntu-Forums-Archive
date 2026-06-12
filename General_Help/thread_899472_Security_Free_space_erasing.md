---
title: "Security: Free space erasing"
date: 2008-08-24
forum: General Help
---

### Post by sstecken on 2008-08-24
I had some sensitive financial data on my laptop before I migrated from Windows to Ubuntu.  I did not do a Darik's Boot and Nuke prior to moving over as I wasn't sure this setup was going to be permanent.  Some time has passed and I now have all my Ubuntu settings perfect so I don't want to do a fresh reinstall and set it up again.  I have a large drive and I'm concerned that data is still lurking in the depths of it somewhere.  Is there a program for linux equivalent to Eraser 5.3 ([http://www.tolvanen.com/eraser/](http://www.tolvanen.com/eraser/)) that accomplishes the same goal of erasing all free space on a given drive?

---

### Post by benny bronx on 2008-08-24
You could install secure-delete from the repos, or install bcwipe using these instructions:
[http://ubuntuforums.org/showthread.php?t=281480&highlight=bcwipe]("http://ubuntuforums.org/showthread.php?t=281480&highlight=bcwipe")

I personally find bcwipe to be a lot faster than secure-delete, and less buggy.

To to a 2 pass wipe of free space on your home directory with the progress being displayed in the terminal:

sudo bcwipe -F -m 2 -v /home

the 2 represents the number of passes.  Although some suggest up to 35 passes to securely wipe, it is really slow and probably unnecessary.

---

