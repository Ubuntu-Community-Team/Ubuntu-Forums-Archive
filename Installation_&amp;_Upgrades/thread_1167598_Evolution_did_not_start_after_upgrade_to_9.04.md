---
title: "Evolution did not start after upgrade to 9.04"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by imlek on 2009-05-23
Hello,

I'm using Ubuntu 8.04 before and today I install 9.04 on my computer.

Installation success and I immediately use Update Manager to update all the software to the current state.

The issue is Evolution.

At first time, I start evolution, everything is okay.

But as soon as I restore my Evolution backup (I backup my Evolution data when on 8.04), the Evolution did not start.

I click many times, but nothing. No error message or anything. It just nothing.

Please help me.

Thank you and warm regards

---

### Post by imlek on 2009-05-23
Got the solution from here:
[http://ubuntuforums.org/showthread.php?t=1134069](http://ubuntuforums.org/showthread.php?t=1134069)

> 
Remove the corresponding files with the file ending ".ev-summary" and
".ibex.index", in this example you should remove the file
"~/.evolution/mail/local/Inbox.ev-summary" and
"~/.evolution/mail/local/Inbox.idex.index".
* Restart evolution, it will be slow to come up because it recreates
the indexes.


It is work perfect. :)

Thanks. :)

---

