---
title: "user-admin in gnome unable to create users"
date: 2008-09-17
forum: General Help
---

### Post by hammad1337 on 2008-09-17
I am using the gnome user-admin utility (administration>users and groups), to create a new user in my pc.
This is what happens: I press the unlock button and successfully authenticate myself. then proceed to create a limited user account. It is created successfully (apparently), but whenever i try to use it, it seems it does not exist. also if i start user-admin again, the account i just created mysteriously disappeared.
Any ideas what might be happening? :S

---

### Post by Pro-reason on 2008-09-17
Yeah, I had that bug before, but I thought they fixed it.

Try creating a user from the command line.  Do:

```

sudo adduser *fred*
```

---

