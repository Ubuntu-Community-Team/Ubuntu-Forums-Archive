---
title: "Script that runs when user is created"
date: 2008-07-21
forum: General Help
---

### Post by william5271 on 2008-07-21
I am running an Ubuntu LTSP server and want to be able to make a script that runs when ever a user is created on the system so I can put config files in their home directories. Any ideas?

---

### Post by Tim Sharitt on 2008-07-21
Maybe something like this will work
```
#!/usr/bin/env bash
useradd -d /home/$1 -s /bin/bash -g users $1
cp /dir_with_configs/* /home/$1/
```
Just run the script with the user name as an option.

---

### Post by mcduck on 2008-07-21
If you want things to be added to new user's home directories just put them into /etc/skel. Everything in there will be copied to new user's homes.

---

