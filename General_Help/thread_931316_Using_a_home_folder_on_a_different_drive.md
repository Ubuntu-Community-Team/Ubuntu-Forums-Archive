---
title: "Using a home folder on a different drive"
date: 2008-09-27
forum: General Help
---

### Post by avanrens on 2008-09-27
I have a different /home folder on another drive and would like to use it on boot. I have set my home folder on a different drive so that I don't loose everything each time I do an new install, but how can I set my new install to use this /home folder.

---

### Post by amauk on 2008-09-27
edit /etc/fstab

add entry
```
/dev/sdb1   /home   ext3   relatime   0  2
```

obviously you need to alter to suit
(change the h/s disk letter & partition num, also if it's not ext3 then change to suit)

*edit*
also, make sure this entry is below the main / entry

---

### Post by avanrens on 2008-09-27
Yes that worked thank you.
Now when I do the new install do I manually select the home folder on the other dive during the install or do it the way you have just explained.
:lolflag:

---

### Post by reality1011 on 2008-09-27
using fstab automounts the home folder to the /dev/sdb1 drive

---

### Post by amauk on 2008-09-27
> **avanrens said:**
> Yes that worked thank you.
Now when I do the new install do I manually select the home folder on the other dive during the install or do it the way you have just explained.
:lolflag:

you can either just do a guided install on the main partition and re-do the fstab entry,
just as you've done now

(you run a risk of losing some config settings setup by the ubuntu installer if you do this
especially if you're installing a new distro version and then setting the home partition to that created by a previous version)

or, when installing, choose the "manual" partition option
(I'd recomend this, as I beleive it's safer)

choose to format your existing root partition
mount point = /

choose NOT to format your home partition
mount point = /home

[IMG]http://www.snoopy.force9.co.uk/sep-home-part/01.png[/IMG]

[IMG]http://www.snoopy.force9.co.uk/sep-home-part/02.png[/IMG]

[IMG]http://www.snoopy.force9.co.uk/sep-home-part/03.png[/IMG]

[IMG]http://www.snoopy.force9.co.uk/sep-home-part/04.png[/IMG]

[IMG]http://www.snoopy.force9.co.uk/sep-home-part/05.png[/IMG]

---

### Post by avanrens on 2008-09-28
Thank you so much for that, I thought that was the way to do it but was not absolutely sure. Thanks again.

:guitar:

---

