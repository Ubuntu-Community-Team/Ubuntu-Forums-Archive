---
title: "dpkg"
date: 2005-11-15
forum: General Help
---

### Post by Noelinho on 2005-11-15
I'm trying to install skype, and I get the following in the root terminal:

```
root@dyn224143:/home/noel# sudo dpkg -i
dpkg: status database area is locked by another process
```

I'm not doing anything else, what's the problem I'm having with the dpkg command?

---

### Post by frodon on 2005-11-15
I think you had synaptic opened when you ran your command. And only one install process is allowed at the same time.

---

### Post by Noelinho on 2005-11-15
Ah, yes, so I do have it opne on another desktop. What an oversight!

Thanks :)

---

### Post by Synt4x_3rr0r on 2005-11-15
[QUOTE=Noelinho]Ah, yes, so I do have it opne on another desktop. What an oversight!

Thanks :)[/QUOTE]

No you simply close synaptic or whatever it was that was running.
Then you install it.

---

