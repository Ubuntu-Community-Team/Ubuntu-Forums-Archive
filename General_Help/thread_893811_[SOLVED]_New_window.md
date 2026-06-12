---
title: "[SOLVED] New window"
date: 2008-08-18
forum: General Help
---

### Post by WallyWest on 2008-08-18
Hello,
How do I spawn a new window in bash so that the process runs in the new window while a script could continue working in the original window?
I am writing a telnet script and using expect but cannot figure out the problem above. I tried typing "spawn telnet *IP*" but recieved the message
bash:spawn:command not found.
Is this a package I have to download?
THanks

---

### Post by sdennie on 2008-08-18
Try using:

```

gnome-terminal -e "whatever your command is" &

```

---

### Post by WallyWest on 2008-08-18
.

---

