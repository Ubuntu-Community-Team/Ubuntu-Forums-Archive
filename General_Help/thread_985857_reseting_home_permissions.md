---
title: "reseting home permissions"
date: 2008-11-18
forum: General Help
---

### Post by calvimm on 2008-11-18
Is there anyway i can reset permissions on a user accounts home directory? i changed the permission on accident and now i can no longer log into my user account, the directory cannot be found.

help!

---

### Post by Yellow Pasque on 2008-11-18
Boot to the recovery mode and select root terminal/prompt. What all did you change, just the /home/<user> directory perms, or other files in there too?
```
cd /home
chown <user-name>
chgrp <user-name>
chmod 755 <user-name>
```

---

### Post by easoukenka on 2008-11-18
Previous post good advice one thing too with all those commands you may need to do -R for recursive so like 

sudo chgrp -R eric:eric /home/eric

that really should do it but without knowing what you did I recommend giving some details or investigating yourself using midnight commander install it with 
sudo apt-get install mc
then type mc

now navigate to your folders/files where your having problems and do ctrl +x +o and ctrl +x +c  

this will give you easy prompt with the permissions on the files and you can also change from there. Only thing I can't figure out is how to make changes recursive there but its nice for single files or figuring out what has what permissions.

---

