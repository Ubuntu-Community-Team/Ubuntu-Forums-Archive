---
title: "why cant I change the root user password?"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by leeper on 2005-12-28
Why is Ubuntu 5.10 shipd with a root password that cant be changed and is not given to the user? how can I get this password? sudo work's greaght in nome but isent any good for text based Linux commands.

---

### Post by ardchoille on 2005-12-28
[QUOTE=leeper]Why is Ubuntu 5.10 shipd with a root password that cant be changed and is not given to the user? how can I get this password? sudo work's greaght in nome but isent any good for text based Linux commands.[/QUOTE]
Because the root account is disabled. You can use sudo to do anything that root needs to do anyway.

---

### Post by lutrafobic on 2005-12-28
The 'root' account is disabled in ubuntu. and the 'first' user you created (in the installation program) is the 'administrator', so to say.

If you want to change things in the 'terminal' and don't have permissions you supposed to use the command: 'sudo'

e.g. to edit a file with 'root' rights:

```
sudo nano file.extention
```

---

### Post by Corvillus on 2005-12-28
Also, both of the following commands
```
sudo -s
sudo -i

```
will give you root shells...the first one being one in your user's environment, the second one being a root login shell.

---

### Post by tbg58 on 2005-12-28
sudo -s or -i give you the equivalent of root, as Corvillus already expressed quite succinctly.
Also if you must enable root, you can always:
sudo passwd root
(then enter the password for the root account).
When you're done you can
sudo passwd -l root
which will disable the root password.  I share your frustration sometimes, but I've gotten used to using sudo, which has the added advantage of reminding me (a fellow newbie) of what I can and can't do under a user account.
TBG

---

