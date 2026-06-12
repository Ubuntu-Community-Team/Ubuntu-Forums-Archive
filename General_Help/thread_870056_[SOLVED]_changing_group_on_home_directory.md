---
title: "[SOLVED] changing group on home directory"
date: 2008-07-25
forum: General Help
---

### Post by dave37 on 2008-07-25
Using Heron, after a crash am trying to restore my home directory which I extracted from a corrupt tgz.  I have most of my data, but now when I try copying the home/user folder over to my installation using sudo dbus-launch nautilus, it is copied over ok but has the group root on the directory and all subfolders & files.  I am also getting the .dmrc file is being ignored error, and found some cli to change permissions, the permissions change but show root as the group.  How can I recursively change the group on the directory to the username?

---

### Post by tamoneya on 2008-07-25
this changes the group on /home recursively to <username>.  Just insert your username and you should be set.```
sudo chgrp -R <username> /home/<username>
```

---

### Post by dave37 on 2008-07-25
That worked great, thanks so much!

---

### Post by DaleNewton on 2008-10-04
Thanks!

I was looking for this too.

---

