---
title: "Moodle upgrade kills email"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by GSBoomer on 2009-11-05
I recently upgraded an Ubuntu server to 9.10. In the process it upgraded Moodle, but I was no longer able to send emails within Moodle.

There is an error in /usr/share/moodle/lib/weblib.php on about line 2274. The solution is to replace weblib.php with the CVS version that can be downloaded at [http://cvs.moodle.org/moodle/lib/weblib.php](http://cvs.moodle.org/moodle/lib/weblib.php).

My is to keep a backup of the original weblib.php just in case this causes a new error.

---

