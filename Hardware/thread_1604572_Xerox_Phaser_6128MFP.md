---
title: "Xerox Phaser 6128MFP"
date: 2010-10-24
forum: Hardware
---

### Post by tharpa on 2010-10-24
This is actually a solution, rather than a question, in case someone else has this same problem.  The printer was either not printing, or was printing codes.  

What finally worked was disabling             apparmor:

sudo aa-complain cupsd 

[http://www.lycheesoftware.com/lychee/devnotesblog.php](http://www.lycheesoftware.com/lychee/devnotesblog.php)


Why didn't I think of that!  ;)

---

### Post by smartysid on 2013-04-11
Thank you very much! This worked !!! :) :)

---

