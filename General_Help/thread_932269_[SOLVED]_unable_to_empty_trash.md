---
title: "[SOLVED] unable to empty trash"
date: 2008-09-28
forum: General Help
---

### Post by da.tiger on 2008-09-28
I have the files of my windows xp cd in trash, and they wont get deleted. Any idea how to get rid of them?

---

### Post by sisco311 on 2008-09-28
open a terminal and type:
```
sudo chown -R $USERNAME: ~/.local/share/Trash/
```
then empty the trash.

---

### Post by kokkus on 2008-09-28
You have them in trash on windows or ubuntu?
Do you use a dual boot solution (XP and Ubuntu) ?
What have you tried so far?
If this is in Ubuntu, I would delete the trash folder. I would use nautilus in root mode (gksudo nautilus).
And recreate the Trash folder again.
The trash folder is locaded under /root/.local/share/

---

### Post by da.tiger on 2008-09-28
> **sisco311 said:**
> open a terminal and type:
```
sudo chown -R $USERNAME: ~/.local/share/Trash/
```
then empty the trash.

That did the trick, thanks

can you please explain why it wasnt emptying before, and how that changed?

---

### Post by growingneeds on 2008-11-28
Personally, I would just fire up a nautilus windows with root privileges and navigate to the actual trash folder. Right-click the folders in question and select "Move to Trash". Voila! Permanently deleted. Note that location of the Trash folder has changed in Hardy Heron. It's /home/your_user_id/.local/share/Trash/ as compared to /home/your_user_id/.Trash in previous incarnations.

```
gksudo nautilus
```

---

