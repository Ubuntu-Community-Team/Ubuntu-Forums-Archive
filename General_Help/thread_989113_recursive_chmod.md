---
title: "recursive chmod"
date: 2008-11-21
forum: General Help
---

### Post by michiedo on 2008-11-21
I've put a blank in the wrong place ...while issuing 

sudo chmod -R 777 /opt/somedir...and then something awful, that i dont write here because of the (very reasonable) "policy zero" about malicous/dangerous commands

the result is that now each and every file in my system has permission 777 
lovely i would say 
:-(((

any suggestion ?
i've already "fixed" /etc/sudoers"
the best thing i can imagine for now is "chmod" every system folder to more restrictive permissions: very annoying, to say the least.
Or maybe: save my foders and reinstall (i would HATE it);
or, probably better restore the backup of may partition, it' one week old.
It could be a choice, but i'll be grateful for every suggestion... some clever shell script .... 

Thank you in advance

---

### Post by drs305 on 2008-11-21
> **michiedo said:**
> 
or, probably better restore the backup of may partition, it' one week old.


That would be my suggestion. Once the / partition's permissions are universally changed it's hard to get them all back to the proper settings.  Backup your recent data if it's on the same partition, restore the old partition, and recopy your newer data files back.

Good for you on having a backup!

---

