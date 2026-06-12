---
title: "turn off system bell in boot/shutdown"
date: 2005-11-24
forum: General Help
---

### Post by RikoW on 2005-11-24
Hi everyone,

if I boot up my laptop in a meeting or during a conference, I don't want to disturb people by having the laptop beep, when it boots up ot shutsdown.

Can someone tell me how to stop the beep? I suppose it's somewhere in the start-up scripts under /etc/init.d or somewhere else in /etc ....

Thanks a bunch!

          Riko

---

### Post by Xian on 2005-11-24
Just a guess, but try this:

Edit the /etc/inputrc file.
Uncomment this line:

```
# set bell-style none
```

---

### Post by RikoW on 2005-11-25
Nope, that's not it!

Thanks anyway!

---

