---
title: "Virtual Box &amp;&amp; Mounting USB Drive"
date: 2008-08-31
forum: General Help
---

### Post by danbrownlow on 2008-08-31
Hey there, I've gotten Virtual Box installed on 8.04 and was wondering how do I enable my external USB drive?

After googling the problem,  I found I had to edit some lines in sudo gedit /etc/init.d/mountdevsubfs.sh under 'Magic', and I've done this, but the device still didn't show up.

Any other ideas?

Dan.

---

### Post by Sycron on 2008-08-31
Do you see the Shared Folders option in VirtualBox ?

---

### Post by danbrownlow on 2008-08-31
Yea', I tried sharing under 'Machine Folders', I added media/disk but it didn't show up in the virtual XP session.

---

### Post by danbrownlow on 2008-08-31
Oh, I think I know the problem. I'm using the Free Version (GPL) and apparently, this doesn't have support for USB. What a shame! I've heard other people using Ubuntu that this has worked though, so are they using the GPL or other version?

---

### Post by danbrownlow on 2008-08-31
Ok, I installed the non-free version and now I have this error:

[IMG]http://i35.tinypic.com/bjgarc.png[/IMG]

Any ideas?

---

