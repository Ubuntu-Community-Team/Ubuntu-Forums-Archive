---
title: "Permissions"
date: 2005-11-27
forum: General Help
---

### Post by Insane on 2005-11-27
Right, what i need is to copy a certain folder into my www directory, but i cannot because i am not the owner....

So, root is the owner, and how do I set myself as root? I need to do that...i need to be root all the time...no questions asked.

Is that possible?

---

### Post by Leif on 2005-11-27
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by peanut butter on 2005-11-27
[QUOTE=Insane]Right, what i need is to copy a certain folder into my www directory, but i cannot because i am not the owner....

So, root is the owner, and how do I set myself as root? I need to do that...i need to be root all the time...no questions asked.

Is that possible?[/QUOTE]

as your the user you created during installation go to terminal and type
```
sudo passwd root
```
then type your current password
what you want root's password to be 
then root's password for confirmation.

after this you must make it possible for him to login to gdm you do this by going to System>administration>login screen setup

and somewhere you will find a box that says allow root to login to gdm, check that then just login as root with the password you created.

this is not a recomended setup thoe i have it this way.

---

### Post by Insane on 2005-11-27
Yes, I just need it sometime..... for emergencies.

---

