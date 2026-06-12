---
title: "Deleting user files and folder"
date: 2008-08-12
forum: General Help
---

### Post by botokely on 2008-08-12
Hello Everybody,

I've Xubuntu installed on my laptop (ASUS EEE PC series). I've created some users on it and I've deleted them after. Now, I want to delete the home directory and all documents of those deleted users but I can't. How can I do it?

I want to delete those files and folder because I have just 4 Go of hard disk :lolflag: .

Thank you for help.

Botokely

---

### Post by houbysoft.xf.cz on 2008-08-12
go to a terminal, and then do a sudo rm -rf /home/<username>.
Replace username by the user you want to delete ;)

---

### Post by houbysoft.xf.cz on 2008-08-12
Btw, can I ask you, does xubuntu work well on the EEE's? I'm thinking of buying one EEE... :)

---

### Post by null byte on 2008-08-12
If you are sure this is what you want to do:
```
sudo rmdir --ignore-fail-on-non-empty /home/user
```

---

### Post by botokely on 2008-08-13
I've just got my EEE's (it was a gift and xubuntu has been already installed there) and I'm new user of this OS. But up to now it works well. Despite sometimes it doesn't shut down (I think it crashes).

Thanks for help

---

### Post by botokely on 2008-08-13
> **null byte said:**
> If you are sure this is what you want to do:
```
sudo rmdir --ignore-fail-on-non-empty /home/user
```

What may be the risk if I delete those folders? I've remarked that there was many hidden files (maybe used by the system :confused: ) in those diectories.

---

### Post by null byte on 2008-08-13
> Now, I want to delete the home directory and all documents of those deleted users but I can't.

That's how you do it. My command, or houbysoft.xf.cz's command does the same thing.

That's why I asked if you are sure.

---

