---
title: "Evolution password at startup"
date: 2008-08-09
forum: General Help
---

### Post by Kolmogorov on 2008-08-09
Hi everyone,

I wonder if i can set up a password to open Evolution ? 
I have a laptop with one user (me) with everything set-up for me but my brother sometimes use my computer, and I don't want him to be able to read my emails...is there anything i can do ? I know that i can set-up another account for him but i prefer to be able to put a password on evolution start.

Thanks

---

### Post by pytheas22 on 2008-08-09
One solution is to make Evolution only executable by root.  This command would do that (I think):
```

sudo chmod o=r /usr/bin/evolution
```

After that, the normal user would not be able to start Evolution anymore; you'd have to launch it by pressing alt-F2 and entering:
```

gksudo evolution
```

which would prompt you for your password before launching Evolution.  You could change the launcher in the Applications menu to use gksudo to make it easier to launch.

If the chmod command doesn't prevent users other than root from launching Evolution, let me know; I think that that command would do it, but it's been a while since my introduction-to-Unix class at the university and the command-line permission stuff isn't as clear in my head as it used to be.

EDIT: I was thinking about this more and realized that if you launch Evolution as root, all of your settings and mail will be lost (because you won't be launching it as the same user who originally configured it) and you'll have to start from the beginning.  Maybe that doesn't matter to you, but if it does, let me know and maybe we can think of a better solution.

---

