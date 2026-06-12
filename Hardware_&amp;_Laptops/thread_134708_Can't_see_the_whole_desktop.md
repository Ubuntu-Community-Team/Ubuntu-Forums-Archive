---
title: "Can't see the whole desktop"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by ntetreau on 2006-02-22
Hi,
my problem is that the desktop image is off-centered on my LCD monitor (XIOD IM15BB).  It is stuck in the upper left corner and I can only see about 25% of the screen. I have been trying for a while now to reconfigure X but to no avail.  When I exit X (sudo /etc/init.d/gdm stop) I can see the whole screen though.  I have X.org setup using i810 driver and 1024x768@anyHz.  I have changed the frequency but could not fix the problem.  Let me know if you have a solution.  Thanks. 

Nic
Dapper alpha 4

---

### Post by heimo on 2006-02-22
Check the 855resolution part on this page:
[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

---

### Post by zachtib on 2006-02-22
im not sure what the problem is, but id post this in the dapper forum, as this forum is technically for breezy.  the people in the dapper forum will probably be able to help you better

---

### Post by ntetreau on 2006-02-23
Thanks Heimo for your help.  I've tried with the new 915resolution package following the instruction from the link you provided but it didn't work.  However, when I switched my LCD monitor with a coworker who uses an LG LCD monitor and it worked fine with his so there is hope.  Any idea?

Nic

---

### Post by heimo on 2006-02-23
[quote=ntetreau]Thanks Heimo for your help.  I've tried with the new 915resolution package following the instruction from the link you provided but it didn't work.  However, when I switched my LCD monitor with a coworker who uses an LG LCD monitor and it worked fine with his so there is hope.  Any idea?

Nic[/quote]

Check your Xorg-logfile for errors/warnings and if possible, attach it and your xorg.conf files so we can have a look.
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

