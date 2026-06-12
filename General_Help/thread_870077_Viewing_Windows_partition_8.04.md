---
title: "Viewing Windows partition 8.04"
date: 2008-07-25
forum: General Help
---

### Post by bholliday72 on 2008-07-25
I just installed Linux for the first time, so take it easy on me.  I installed inside Windows onto C: (C being the only partition on the hard drive) and now I just want to be able to access C: and take a look at my Windows folders, mainly so I can browse around in there and delete a few trojans.  Is this possible?  How? :confused:

EDIT:  If I boot from the LiveCD can I see my C Drive then?  This is all so confusing for a beginner like me.

---

### Post by bholliday72 on 2008-07-25
bump help!

---

### Post by lordadi on 2008-07-25
Hi,

Since you're looking to read and write stuff from a hardy install then go to the add/remove icon in applications and search for NTFS Configuration Tool. It will download and install the program.

After that, go to Applications > System Tools > NTFS Configuration Tool and mount your windows disk to (preferably) /media/windows/, after that when you click next, be sure to check the box marked "enable write support" or something.

Then you can browse your C: drive and also write to it but **BE CAREFUL!** you could seriously harm windows if you mess with the wrong things.



Hope you can clean your windows of trojans,


Lordadi.

---

