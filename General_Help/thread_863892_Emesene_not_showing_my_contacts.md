---
title: "Emesene not showing my contacts?"
date: 2008-07-18
forum: General Help
---

### Post by smalss on 2008-07-18
I installed emesene, signed in and it doesn't show any of my contacts. How do i fix?

---

### Post by smalss on 2008-07-19
bump...

---

### Post by Sef on 2008-07-19
1) Don't bump your thread unless 24 hours have gone by.  Otherwise you could be given an infraction.

2) Offline buddies are not shown by default.  If you want to see them, then View > Show Offline Buddies.

---

### Post by smalss on 2008-07-19
It still won't show any contacts. Everything is blank, the nickname and contacts are all blank. just white.

---

### Post by affouneh on 2008-07-19
I have the same problem
any suggestions ?

---

### Post by leveliv on 2008-07-19
yah this is screwed I have the same problem, what gives?

---

### Post by tonatiuh on 2008-07-19
I have the same problem, any suggestion? thanks

---

### Post by mbarak on 2008-07-20
From the emesene website:
> **Important:** Some of the MSN contact list servers started to reject old clients, which unfortunately includes emesene 1.0. If you are experiencing problems, [update to SVN]("http://emesene.org/trac/wiki/SVN") (either trunk or stable). We will release emesene 1.0.1 along with some bugfixes soon

---

### Post by myle on 2008-07-22
I have been experiencing the same problem. For the time being, I use amsn.  I am looking forward for the emesene 1.0.1 in the repositories.

Bug fix:

```
sudo sed -i.bak 's/09607671-1C32-421F-A6A6-CBFAA51AB5F4/CFE80F9D-180F-4399-82AB-413F33A1FA11/g' /usr/share/emesene/emesenelib/XmlTemplates.py
```

[source](http://emesene.org/smf/index.php?PHPSESSID=jamqqpn7ca2hjjl6tlialuepp5&/topic,1357.0.html)

---

### Post by WeKnowBetter on 2008-07-27
The bug fix works for me. 32-bit Hardy. Pure ubuntu.

---

### Post by BlackDragonBE on 2008-07-29
Thanks a lot Myle!
I've been searching how to fix this for days!

---

### Post by djbon2112 on 2008-08-04
Bux fix also works fine in Ubuntu Hardy x86_64.

---

### Post by padlefot on 2008-08-04
sweet, thanx alot! the bugfix worked. brilliant :)

---

### Post by SureStandar on 2008-08-09
thank you so much Myle:guitar:, and all you guys at the ubuntu forums. i am new to ubuntu ( second month now) so if it wasnt for your help i d be still probably using windows xp right now.. which is not bad, but faaaar less fun

---

### Post by Zeusz3 on 2008-10-18
it also worked just fine for me to :)
debian 4.0, emesene 1.0
thanks a lot

---

### Post by tifereth on 2009-02-07
Fine on Xubuntu 8.04.2 too, thx!

---

### Post by thenickrulz on 2011-06-20
> **Sef said:**
> 1) Don't bump your thread unless 24 hours have gone by.  Otherwise you could be given an infraction.

2) Offline buddies are not shown by default.  If you want to see them, then View > Show Offline Buddies.
This worked for me thx :):guitar:

---

