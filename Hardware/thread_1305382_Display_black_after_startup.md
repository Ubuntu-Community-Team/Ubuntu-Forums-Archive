---
title: "Display black after startup"
date: 2009-10-29
forum: Hardware
---

### Post by c0mput3r_n3rD on 2009-10-29
Hello all,

I've had this problem for a while now, and still have not found a solution.  For some reason after changing my display rotation, the screen is completely black after I log in.  I've tried the command:
```

xrandr -o normal

```

(I can do that because the terminal is hot-keyed to my F2 button), but nothing happens.  I've tried restarting my display by pressing ctr+alt+f1 (the display is fine when I drop to the tty1) and stoping gdm with:
```

sudo /etc/init.d/gdm stop

```

And the "startx".  How ever it has not worked.  

Any suggestions would be greatly appreciated.

---

