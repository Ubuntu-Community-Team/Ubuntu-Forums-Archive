---
title: "BIG Cairo dock problem. please help"
date: 2008-10-19
forum: General Help
---

### Post by xwat17x on 2008-10-19
okay, i did: sudo apt-get install cairo-dock.

then did alt+f2, it opens up but i have no themes except the default one.

i did the same thing on my other computer, and i got all the themes. 

Why didnt it work this time?

---

### Post by loomsen on 2008-10-19
Cause you didn't download them? Just guessing ;)

```

sudo apt-get install cairo-dock-data cairo-dock-dev

```

And make sure they don't get installed to your root directory, used to be a bug a while ago.

---

### Post by xwat17x on 2008-10-19
okay...so i just put that in the terminal?

---

### Post by loomsen on 2008-10-19
Yep, and then, when you are prompted ok, open up nautilus, if you're in a terminal anyway, type:
```

nautilus /

```

and watch there, only there, if there are 5 or 6 folder named, in contrast to any other folder there, sth like

_BLABLABLA_

This was a bug before as I said, just make sure they are not there and everything should be fine :)

---

### Post by xwat17x on 2008-10-19
tried it, there wasn't any folders like that but i still don't have any themes...

---

### Post by loomsen on 2008-10-19
Well, but the cmd line returned that installation finished without any errors?

Then open up synaptic and take a look where they've been installed.

---

### Post by fabounet on 2008-10-20
I recommend using the Cairo-Dock's repository, since the version present in Ubuntu is currently quite old.
there are 3 packages to install.

---

