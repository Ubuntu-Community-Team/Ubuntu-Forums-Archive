---
title: "Accidently moved Home! HELP!"
date: 2008-09-12
forum: General Help
---

### Post by rbolio on 2008-09-12
Ok...here's the deal, i was trying to install yamipod and i think i accidently moved the home folder to somewhere else... i cant open ANYTHING... everthing says 

"Failed to change to directory "/home/rbolio" (no such file or directory)."


urgent! please help!

---

### Post by Zorael on 2008-09-12
Boot off a live cd and try to make sense of what happened. Find your home directory and move it in place. If you have a separate home partition, make sure your /etc/fstab entry for it is correct, and that the partition itself hasn't gone bananas.

---

### Post by rbolio on 2008-09-12
i think it is in the same partition... (i hope?) and id say it is my fault.. i mean i was "messing" around with sudo mv... the command i typed was something like this

sudo mv /rbolio/home (some file) /usr/lib

or this

sudo mv /home/rbolio (same file...lol?)   /usr/lib


Does this mean i have moved the home folder to /usr/lib? ..... 


ps.i find it Ironic that the actual file didn't move xD

---

### Post by sisco311 on 2008-09-12
type:
```
sudo find / -type d -name rbolio
```to find your home directory and:
```
sudo mv */path/returned/from/find*/rbolio /home/
```to move it back.

---

### Post by skullmunky on 2008-09-12
It was probably the 2nd command that you typed.  your home directory would've originally been /home/rbolio.

boot off the livecd, and look in /usr/lib.  'rbolio' will likely be there.

if so, then

```

sudo mv /usr/lib/rbolio /home

```

if it's not in /usr/lib, try the 'find' method above.

why'd that happen, you might wonder!  
maybe you meant to type this originally:

```

sudo mv /home/rbolio/somefile /usr/lib

```

to move 'somefile' into the /usr/lib directory, right?

but instead maybe you typed this

```

sudo mv /home/rbolio somefile /usr/lib

```

with the space, "/home/rbolio" and "somefile" are two different things, both of which will get moved to /usr/lib.

however, once "rbolio" gets moved, "somefile" has suddenly moved with it, so the 2nd part of the move doesn't work - that's why 'somefile' isn't in /usr/lib.

---

### Post by rbolio on 2008-09-12
Well i fixed it before i could read that.... 

i used find /usr/lib  and found the rbolio everywhere...

then used

sudo mv /usr/lib/rbolio /home


that helped me....  thanks for the help tho!

---

### Post by sisco311 on 2008-09-13
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thread Tools.**

---

