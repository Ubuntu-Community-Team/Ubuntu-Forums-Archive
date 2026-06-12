---
title: "bluetooth allways off"
date: 2010-10-31
forum: Hardware
---

### Post by Argonisius on 2010-10-31
Is possible to disable bluetooth on startup?

---

### Post by P4man on 2010-10-31
If you mean turn the radio off by default (but keep the applet and software loading so you can reenable it), try this:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10005133](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10005133)

---

### Post by Argonisius on 2010-10-31
Thanks, that was it. Do you know, how to change cpu frequency to powersave mode when running on battery?

---

### Post by P4man on 2010-10-31
That functionality existed in the past but it has been removed as it was deemed pointless and contraproductive. You can find the rationale here:
[http://www.advogato.org/person/mjg59/diary.html?start=123](http://www.advogato.org/person/mjg59/diary.html?start=123)

Basically, you want to have it to "on demand" all the time. Contrary to what you may think, to save battery its better to have the cpu speed up for a short period of time to complete a task as fast as possible, and then go to sleep again, rather then running longer periods of time at high cpu load but low frequency. Intel call this "hurry up and go to sleep".

---

