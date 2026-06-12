---
title: "BB Storm 9530 and USB connection to Ubuntu"
date: 2010-06-25
forum: Hardware
---

### Post by Younguns on 2010-06-25
Greetings all.

I recently installed Ubuntu__ (Lucid Lynx) onto my laptop,  and have read all of the postings in the Ubuntu forums and have not  found a solution to a problem I am having. Whenever I try to connect my Storm 9530 via  USB to my laptop a white screen comes up on my Storm with a tiny error  message that flashes very quickly away and my Storm stays black screened  with the little red indicator light constantly lit until I disconnect  from the laptop. The OS on the Storm  is ver 5 ending with .328 (I think that is it). Does anybody know what  the problem is, or if there is a way to fix this problem.

Thanks!

---

### Post by ieee488 on 2010-06-25
[http://forums.crackberry.com/showthread.php?t=114019](http://forums.crackberry.com/showthread.php?t=114019)

---

### Post by Younguns on 2010-06-26
Thanks for the link, but that does not correct the issue of connecting my BB Storm to my laptop. No bluetooth capability on laptop.

---

### Post by Younguns on 2010-06-30
Any ideas on this matter?

Thanks

---

### Post by erbey on 2010-07-27
hi i have the exact same problem, mine charges for a few seconds but when Ubuntu realizes its been attached, the blackberry (storm 9500) resets, i have also been keeping an eye on this  thread, with the same problem, [http://ubuntuforums.org/showthread.php?t=1534069&highlight=blackberry+storm](http://ubuntuforums.org/showthread.php?t=1534069&highlight=blackberry+storm)

---

### Post by erbey on 2010-07-27
[http://ubuntuforums.org/showthread.php?t=1431784&highlight=blackberry+storm&page=2](http://ubuntuforums.org/showthread.php?t=1431784&highlight=blackberry+storm&page=2)
this thread has apparently found a temporary fix 
sudo mv /lib/udev/rules.d/85-hdparm.rules  /lib/udev/rules.d/85-hdparm.rules.disabled
although this hasn't worked for everyone (me)
although hopefully it helps you

---

### Post by jmverner on 2010-11-18
My Blackberry Storm 9530 is doing exactly the same thing on 10.10
The "fix" described above does not do anything to help.  When looking at the defect comments on the developer site it appears this fix was for attached hard disks using USB and firewire.  So not helping for USB blackberry devices.

---

