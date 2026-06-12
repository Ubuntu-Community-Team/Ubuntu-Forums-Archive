---
title: "Advance Bash Script help"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by abovenewbi on 2009-02-04
Hi, I'm a teacher and I need to add users( the students) however I was reading about scripting and realized that there might be a better way to add users than to do them one at a time, can you please help me, I want the script to check at first if the administrator is trying to run it( if it isn't the administrator then exit) 

I want the following parameters to be passed in:
usercreate -a/n/ -c "GECOS" username
-a indicates an administrative account
-n indicates a normal account
-c GECOS 
*the username must be unique.
If I'm adding an administrative account then the home directory will be created under /home/admin and the user will be added to the admin group
however, if its a normal account let the home directory be created under /home/users

thanks

---

