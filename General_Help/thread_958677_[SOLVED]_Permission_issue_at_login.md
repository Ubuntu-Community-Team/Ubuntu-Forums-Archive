---
title: "[SOLVED] Permission issue at login"
date: 2008-10-25
forum: General Help
---

### Post by Amazona aestiva on 2008-10-25
Hi!

The matter is that the system thinks that $HOME/.dmrc is not mine, but it is!

It says I need to have 644 permission so I did:
```
chmod 644 /home/nandor/.dmrc
```
The command seemed to have no errors, but I still get that annoying message.

I renamed the file, if it creates a new one, but I got the same message again.

I checked my permissions by right click->properties and permissions. They are all right.

Any idea?

Thanks in advance

---

### Post by geirha on 2008-10-25
Someone else here had this problem recently as well, though the error message also said that the homedir need to be writeable to only yourself. Check the permissions on your homedir, and make sure it's only writeable to you. chmod 755 $HOME should do the trick.

---

### Post by NilsE on 2008-10-25
I had the same problem and my permissions are correct.  Just go into System > Administration > Login Window - Security tab and change the permissions to allow login to group write.........

---

### Post by Amazona aestiva on 2008-10-25
> **geirha said:**
> ... chmod 755 $HOME ...

That really solved it. Thanks

---

