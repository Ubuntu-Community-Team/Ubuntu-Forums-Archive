---
title: "Installing Ubuntu, Keep /home"
date: 2008-11-05
forum: General Help
---

### Post by change_mode on 2008-11-05
I'm running openSUSE right now, but I really wanna change to Ubuntu, because with openSUSE anything that involves packet management takes ages and it's annoying.

I want to keep my /home though and it's on a seperate partition.

Now, when I:

- start with the ubuntu live cd
- put all the stuff I wanna keep in a seperate folder with a name not used by the ubuntu installation
- delete the rest of the stuff in /home (config files etc)
- install ubuntu and mount /home on that partition

Will my data be safe?

---

### Post by Monotoko on 2008-11-05
If /home is a seperate partition, it will be safe without the need to do all that.

All you need to do is ensure you install ubuntu to OpenSUSE partition and not the home one, then manually partition it so it mounts the other partition at /home

---

### Post by change_mode on 2008-11-05
Thanks for your reply.
The user name does not matter, right? Just to re-confirm.

Ubuntu will make a /home/ubuntu-user on the partition, depending on my user name and I'll find my old files in /home/old-user?

---

### Post by sancho panza on 2008-11-05
I'm not too sure about the user name issue. I will NOT be surprised if you have problems accessing the old files using the new user name. Do more research till you get a definite answer.

---

### Post by Monotoko on 2008-11-05
Yepp thats right, just be sure not to make a user with the names already in the /home, im unsure what that would do

(i shall try it on a VM later i think, it will be interesting)

Edit: i did this from MINT, it worked flawlessly, just be sure to use 
```

sudo nautilus

```
to access the old users files, and not the current user (sudo will give you root permissions, nautilus will open the file manager, you will be asked for a password, put your accounts password in)

---

### Post by change_mode on 2008-11-05
I installed with a new user name and it all worked :)

---

