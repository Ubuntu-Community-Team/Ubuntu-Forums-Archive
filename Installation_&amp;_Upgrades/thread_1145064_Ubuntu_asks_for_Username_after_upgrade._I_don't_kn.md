---
title: "Ubuntu asks for Username after upgrade. I don't know it."
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by urbanpot on 2009-05-01
I just upgrade to the latest version of Ubuntu. Previously I always logged in with my password only. Now it asks for my Username which I have no idea what is. Is there a way around this or do I just have to guess?
Thanks
H

---

### Post by zigga15 on 2009-05-01
At the login screen press ctrl+alt+f2

with any luck it will be in there somewhere.

If you can get into a terminal type "who"

I also know that the default is your first name in lowercase - first name being the actual name you entered in the setup screen.

Otherwise try leaving it blank

---

### Post by x33a on 2009-05-01
there may be some other methods for this, but you can try loading a live cd. go to /home, the foldername there is the username.

---

### Post by urbanpot on 2009-05-01
Thanks, guys. Quick replies! I will try your suggestions.

---

### Post by BugFixBug on 2009-05-01
start your computer in recovery mode (in grub loading fase your presented a bootlist. choose recovery). in the recovery mode menu choose netroot(or something like that). this will give you a cmd line interface with root access.

do 
```

ls /home

```
this will give you a list with the users.
now restart your computer and boot it in normal mode and use the username that you found in /home/

---

