---
title: "Does anyone know where the pidgin folder ran off to in 8.10?"
date: 2008-11-06
forum: General Help
---

### Post by Les Oeufs on 2008-11-06
I was just wondering where the pidgin folder was in 8.10. It used to be .purple before in the home folder, but it seems to have run off some place. Anyone know where it is now?

---

### Post by ww711 on 2008-11-06
It should be still there in /home/someuser, well mine is after doing

```
ls -a
```

it shows .purple 

After cd-ing and ls-ing into .purple it shows xml and other files.

---

### Post by Les Oeufs on 2008-11-06
Oh, nm. It seems that it creates the folder after you run the program for the first time

---

### Post by sdennie on 2008-11-06
It's normal to not have config files for apps if you've never run them.  If you are running a system with lots of users and want them all to receive a default config, have a look in /etc/skel.  You will notice that those are the exact files that you got when you first logged in.  Adding things there will automatically add them to new users that are created (so, don't put user specific account/password information there).

---

### Post by Rainstride on 2008-11-06
> **Les Oeufs said:**
> I was just wondering where the pidgin folder was in 8.10. It used to be .purple before in the home folder, but it seems to have run off some place. Anyone know where it is now?

same place. open the program first.

---

