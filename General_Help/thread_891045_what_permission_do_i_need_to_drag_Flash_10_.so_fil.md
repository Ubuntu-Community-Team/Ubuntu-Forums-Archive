---
title: "what permission do i need to drag Flash 10 .so file to the Mozilla/plugins folder?"
date: 2008-08-15
forum: General Help
---

### Post by eival on 2008-08-15
im trying to drag the .so file to the lib/mozilla/plugins folder to complete the install but its saying i dont have authorization.

i was able to do it before i reinstalled ubuntu but i dont remember what authorizations i granted myself, and i never had to sign in as root either.

the only things i could think of was System changes and User changes, but neither worked after i granted myself permission.


or if someone knows of a terminal code to put the so file in that folder, that would be fine aswell.

---

### Post by Too Late on 2008-08-15
The easiest way of doing such things is to use Nautilus as root. In terminal, type:
```
gksudo nautilus
```

Of course, you can also use mv command:
```
sudo mv filename /lib/mozilla/plugins/
```

---

### Post by sdennie on 2008-08-15
If you are the only user of your system, you can just install it locally for yourself by putting it in ~/.mozilla/plugins.  Otherwise, you'd need root permissions so, try using the nautilus window you get with:

```

gksudo nautilus

```

---

