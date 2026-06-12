---
title: "[SOLVED] Commandline messaging"
date: 2008-11-06
forum: General Help
---

### Post by zeronothing on 2008-11-06
My question is, is their a way to message someone logged into the same system as me. I know you can use the command "finger" to find out information about users logged into the same system or remote system. I then want to be able to send a message to that user. is this possible?

---

### Post by the yawner on 2008-11-06
Using apropos I got two matches, *wall* and *write*. But I think write is what you're looking for.

```

write user [ttyname]

```

---

### Post by sisco311 on 2008-11-06
```
write *usermane*
text
text
Ctrl+D
```
[http://linux.byexamples.com/archives/233/write-a-message-to-login-users-through-terminal/]("http://linux.byexamples.com/archives/233/write-a-message-to-login-users-through-terminal/")

---

### Post by zeronothing on 2008-11-06
thanks guys, just what I was looking for....

---

