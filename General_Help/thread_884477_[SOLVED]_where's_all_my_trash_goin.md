---
title: "[SOLVED] where's all my trash goin?"
date: 2008-08-09
forum: General Help
---

### Post by Kain000 on 2008-08-09
hey everyone, 
 as of late my trash can icon on my bottom pannel has been disparaging randomly.    I replace it with a quick right click and add to panel, but it's annoying and well my trash shouldn't be running out on me.

---

### Post by WRDN on 2008-08-09
The Trash is stored in /home/[username]/.local/share/Trash (for Ubuntu 8.04).
If the mentioned issue keeps occuring, you may want to reset the Desktop settings using the following command in your home directory:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

For this to take effect, you will need to logout and in again.

---

### Post by Kain000 on 2008-08-09
thanks, will that reset my entire desktop to a fresh install look?

---

### Post by WRDN on 2008-08-09
Yep. If you want to reset the panels only however, use the command:

```
rm -ri ~/.gconf/apps/panel
```

Again, you will need to log out and in again for the changes to take affect. Rather than any theme(s) etc, this will only reset the panels.

---

### Post by Kain000 on 2008-08-09
> **WRDN said:**
> Yep. If you want to reset the panels only however, use the command:

```
rm -ri /home/[username]/.gconf/apps/panel
```

Again, you will need to log out and in again for the changes to take affect. Rather than any theme(s) etc, this will only reset the panels.

sweet, thanks buddy.


any clue why the trash and workspace switcher would just decide to remove themselves?

---

### Post by WRDN on 2008-08-09
I'm guessing its just a bug. The trash vanished on my PC before (though I could right click on it!), as well as some IM icons. To solve this I just ran the command to delete the panel folder.

---

### Post by Kain000 on 2008-08-09
alright well I will keep that in mind.  Thankyou for your help.

---

