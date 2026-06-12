---
title: "can't unlock machine, can log in and sudo however"
date: 2008-10-24
forum: General Help
---

### Post by uschxc on 2008-10-24
a while back i recently made a big booboo.  while trying to change ownership of a user's home folder recursively to 'users'  i forgot one slash and i think i ran chgrp -R :users /home/*  which was a horrible idea to say the least.

i've recovered most of the snafu's from that, and what i haven't the upgrade to Intrepid has reinstalled/configured most things.  however this one is still a little beyond me.  i'm sure its a group ownership issue or something.  but whenever my machine gets locked via screensaver timeout or whatever, my password doesn't work.

i've tried resetting it from root and from the user level with no success.  any ideas?

on a side note, i've heard pretty stellar things from the JFS (i think?) file system format..but i have to do a fresh install though correct?  no conversion tool i'd imagine.

---

### Post by uschxc on 2008-10-25
bump

---

### Post by kevstar31 on 2008-10-25
Try
```
chgrp :root /home
chgrp -R :<username> /home/<username>
```

---

### Post by uschxc on 2008-10-28
> **kevstar31 said:**
> Try
```
chgrp :root /home
chgrp -R :<username> /home/<username>
```

thats how its currently set.  ran the commands to no avail

---

