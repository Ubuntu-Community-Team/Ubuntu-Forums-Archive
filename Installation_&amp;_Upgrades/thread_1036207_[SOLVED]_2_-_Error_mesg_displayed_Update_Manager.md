---
title: "[SOLVED] 2 - Error mesg displayed Update Manager"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by sandman3838 on 2009-01-10
Hello

I'm not sure if I should have but this question here or in the "General" category?  Still.... 

This issue isn't a problem or I should say it's not causing any, as far as I can tell.  It's just annoying!  Towards the end of "Update Manager" running I get this:

***********  
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


Some index files failed to download, they have been ignored, or old ones used instead.

*******************  

If this is a painless fix?  Great!
However if it's something crazy?  I'll just leave it!

Any ideas?

---

### Post by avtolle on 2009-01-10
Go to Software Sources (System-->Administration) and uncheck the cd.

---

### Post by sandman3838 on 2009-01-10
Thank you so much!
That did it!

And it was painless!  :)

---

### Post by avtolle on 2009-01-10
You are most welcome. Would you please use thread tools (at the top) to mark this thread "Solved" so others looking for a solution can review it? TIA.

---

