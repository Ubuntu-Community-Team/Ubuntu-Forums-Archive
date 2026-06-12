---
title: "Eclipse 3.4 installation?"
date: 2008-09-01
forum: General Help
---

### Post by usfish on 2008-09-01
Eclipse 3.4 is still not in Ubuntu repository, so I download eclipse 3.4 from the official website. But in this way, I can't boot it by typing "eclipse" in terminal. Is there any way I can solve this problem?

Thanks!

---

### Post by MindFlayer on 2008-09-01
Unzip the archive and then run eclipse either by clicking the icon in Nautilus or typing ./eclipse in terminal in the directory it resides.

edit: If you want to add eclipse executable in the path, open up ~/.bashrc in your favourite text editor, then add this line somewhere:
export PATH=$PATH:$HOME/eclipse/

---

### Post by usfish on 2008-09-01
> **MindFlayer said:**
> Unzip the archive and then run eclipse either by clicking the icon in Nautilus or typing ./eclipse in terminal in the directory it resides.

is there any way to let me run the new version of eclipse by building a new terminal command, so I can run it by typing "eclipse" in anywhere?

Thanks!

---

### Post by MindFlayer on 2008-09-01
Yeah, look at my above post (I edited it just a minute ago ;))

---

### Post by atinsood on 2008-09-01
or you can set an alias called eclipse in your bash profile

vi ~/.bash_profile

alias eclipse=<location of eclipse dir>/eclipse <optional arguments for memory allocation for eclipse>


save the file.

run this command in terminal

. ~/.bash_profile

and u are good to go. 
Word of advice : please make a back up copy of your bash profile before making nay changes. And please mind the spaces.

---

### Post by usfish on 2008-09-01
Thank you guys!

---

