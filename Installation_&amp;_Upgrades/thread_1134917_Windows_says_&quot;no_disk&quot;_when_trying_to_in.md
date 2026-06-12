---
title: "Windows says &quot;no disk&quot; when trying to install 9.04 inside windows"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by webdunce on 2009-04-24
The issue i'm having is with the initial installation.

I run Windows XP Home Edition on an HP Pavilion a656x with an added video card and an added stick of memory. It has two optical drives, drive E (a DVD/CD drive) and drive F (a CD drive).

Here is what happens...

1. I boot into Windows XP
2. I insert the Ubuntu 9.04 CD into drive E
3. I get a pop-up message window (from pyrun.exe) telling me that there is no disk in drive F
4. My options are Cancel, Try Again, and Continue and the "X" to close the little window
5. no matter what i click, the error message just pops back up.

if I put the CD in the Drive F, then everything happens exactly the same except that in step 3, the message informs me there is no disk in drive E.

So, whichever of my two drives i insert the CD into, the installer complains that i don't have a disk in the OTHER drive.

With the Ubuntu 8.10 CD, after I insert the CD, I simply get a pop-up that presents 3 installation options (and I want to choose the 2nd one: install inside windows). With the 9.04 CD, sometimes, if i keep clicking the various buttons on the error message window randomly like 50 times (Cancel, Try Again, Continue, and the little close "X")...I will eventually get the installation options.

I have reported this as a bug (Bug #365881), but was wondering if anyone else has experienced it and, hopefully, knew of a workaround.

---

### Post by lisati on 2009-04-24
Are you able to boot from the CD? I had another error message when trying to install 9.04 via wubi on one machine, and ended up doing a regular install into its own partition.

---

### Post by webdunce on 2009-04-24
i just checked and i am able to use the CD as a Live CD, but i must be able to use the "install inside windows" option, i do not wish to install it on a partition, as i fear losing the data on my windows C drive, and i have only one PC and it has only one hard drive.

---

### Post by webdunce on 2009-04-24
no prob...i restarted computer...the error message changed somewhat and then i needed to click cancel on the error message only 8 times and got the installation options and it installed fine.

---

