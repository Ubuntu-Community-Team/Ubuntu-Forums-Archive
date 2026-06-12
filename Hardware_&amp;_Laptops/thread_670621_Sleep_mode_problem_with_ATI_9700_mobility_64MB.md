---
title: "Sleep mode problem with ATI 9700 mobility 64MB"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by Serpentinsek on 2008-01-17
I've searched the forum for the same kind a problem, and I didn't got much out of it.

I'm running Ubuntu 7.10 on Prestigio Nobile 157 with ATI radeon mobility 64MB and when I want to put it in sleep mode I can't *wake* it back up ...

Some nice folks from irc support told me that my problem has something to do with my g card.

Can someone please help me with a solution? Thank you very much in advance.

---

### Post by Serpentinsek on 2008-01-21
Still dealing with the same problem.

---

### Post by Serpentinsek on 2008-01-23
Anyone?

---

### Post by Serpentinsek on 2008-01-29
Bump

---

### Post by coskierken on 2008-02-01
Try this, as it worked for me!  II had the same problem with ATI 8.01 and X1700.  Many others having same problem with various ATI cards. n a root terminal paste this and enter:

/usr/sbin/update-rc.d -f atieventsd remove

Here is the link to explain:

[http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23](http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23)

Also, here is a link for Compiz Switch.  Video is still BAD when Compiz is active.  So, it turns it off/on so you can watch videos without choppiness.

---

### Post by coskierken on 2008-02-01
Sorry! Compiz Switch link:

[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)

---

### Post by Serpentinsek on 2008-02-02
Thank you for your reply. I will report back if it does any good.

---

