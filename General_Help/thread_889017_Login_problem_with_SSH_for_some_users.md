---
title: "Login problem with SSH for some users"
date: 2008-08-13
forum: General Help
---

### Post by chunkyq on 2008-08-13
I have two computers, machina is set up as an SSH server, TheBoilingHell is just a client. There are two human accounts on machina, charlie and val.

What I can do:
 - Log in as charlie on machina.
 - Log in as charlie through SSH from anywhere (including TheBoilingHell).
 - Log in as val on machina.

What I cannot do:
 - Log in as val through SSH from TheBoilingHell.
 - Log in as val through SSH from machina.

SSH only says, "Permission denied, please try again." I have tried with verbosity level 3 enabled, but there is no error.

I know that I am entering the password correctly, as it works on machina. I've never had a problem with SSH before this. Does anyone have an idea what is going wrong?

---

### Post by finer recliner on 2008-08-13
probably a permissions issue. check to see if val is missing from any groups that charlie is part of (specifically the ssh group)

you can find out what groups a user belongs to using this commmand:
```
groups <user>
```

where <user> is the username you want to look up

---

### Post by chunkyq on 2008-08-13
Neither charlie nor val is in the ssh group, but I tried adding val anyway. I didn't work. The only group that charlie is in that val isn't is charlie. I tried adding val to charlie, but it didn't work either.

---

### Post by Iowan on 2008-08-13
Both users have similar files in **~/ssh** (on **machina**)? How does **~/.ssh/authorized_keys2** compare between the two?

---

