---
title: "PAsswords and special characters gone"
date: 2008-10-04
forum: General Help
---

### Post by DaleNewton on 2008-10-04
Hi all,

I have a file saving/opening problem which I have been unable to fix and I am transferring my files,shortcuts, bookmarks, etc to a new user.

Does anyone know if there is a way to transfer the saved passwords in Firefox passwords manager to my new user?

Also, I sometimes need to write in Spanish, and I used to be able to press ALT and different letters to get latin characters with the accents. Now though I just get normal letters with ALT. DOes anyone know how I can get this function back?  I tried changing keyboard to 'SPain'.

Thanks for any help.

---

### Post by taladan on 2008-10-04
You should just be able to:

```
 cp ~/.mozilla /home/<newuser> 
chown -R <user>:<user> /home/<newuser>/.mozilla

```

as for the ALT+Specials you may need to look at changing your locale.  You can figure out what your locale is by typing at the CLI:

```
 locale 
```

Tal

---

### Post by DaleNewton on 2008-10-05
Thanks taladan.

---

