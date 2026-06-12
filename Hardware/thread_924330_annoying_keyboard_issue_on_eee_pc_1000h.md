---
title: "annoying keyboard issue on eee pc 1000h"
date: 2008-09-19
forum: Hardware
---

### Post by tehschulman on 2008-09-19
so i've noticed this behavior recently and it's really starting to get on my nerves. i'm not really sure of the back end side of what's going on, but basically at some point, i believe it happens after my screen saver engages, my eee pc's keyboard will malfunction and it will not receive shift-key inputs [guess why this post is all lower cased] and in certain programs [rhythmbox, pidgin, terminals, etc] any keyboard input i give it will crash the program. it also prevents me from typing in my password when my screensaver is active [i'm using electricsheep]. this persists until i reboot

i'd express more rage over this issue, but i can't currently type exclamation points. helpppp

---

### Post by adamm on 2008-09-20
I haven't had this problem specifically on my eeepc 900, but I do get similar symptoms with VMware 5.5.6 workstation on my Dell Latitude D830 where my left shift and control keys get locked.

One method that I use to fix this is the command:
```
setxkbmap -rules xorg -layout us
```

You may also validate what's going on by running this command before and after the problem occurs:
```
setxkbmap -print
```

If the -print command returns the same thing in both instances, ignore my post as I'm probably way off solving your problem ;)

---

### Post by tehschulman on 2008-09-21
I will try this out next time I come across the problem. I also use VMware and to my knowledge VMware has been used/is running during the sessions when this issue occurs, so maybe it's VMware that's really to blame. This hasn't been patched or fixed at all in VMware?

---

