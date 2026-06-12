---
title: "Exabyte VXA-3/VXA-320 tape drive drivers"
date: 2014-10-14
forum: Hardware
---

### Post by Michael_McKenney on 2014-10-14
I am trying to find better drivers for my Exabyte tape drives for Ubuntu.  I have been searching Google.  I am trying to post to bacula.org but they have e-mail forums only.  Any ideas on getting better drivers?

---

### Post by hndrcks on 2014-10-14
Unfortunately, Tandberg pretty much gave up on that format 9 years ago. The last version of the VXATools for Linux was released in April of 2006. 

It's too bad, that was a pretty reliable technology in its day.

---

### Post by Michael_McKenney on 2014-10-14
VXATools are not drivers.  They are testing tools only.  I have it working.  Ubuntu 14.04.1 found all three tape drives.  HP LTO 3 and both VXA-320.  The issue is performance on the VXA-320s.   I was going to try backing up to the HP LTO 3 tonight.  I contacted Tandberg for help. They said to find drivers on the Ubuntu forums.

---

### Post by Michael_McKenney on 2014-10-15
Ubuntu tech forum recommended block size = 0.  Tandberg does not have much on VXA support.  Most of the engineers that worked on it are retired.

---

### Post by Michael_McKenney on 2014-10-15
set the device block size to 0.  Bacula block size 65536 and buffer size 65536.  Any other suggestions?

---

