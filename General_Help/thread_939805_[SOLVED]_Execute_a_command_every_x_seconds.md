---
title: "[SOLVED] Execute a command every x seconds"
date: 2008-10-06
forum: General Help
---

### Post by martin_legion on 2008-10-06
Hello. Anybody knoes how can I execute a certain command every, let's say, 30 seconds?

For example, I want to monitor the temperature of a PC with the command 'sensors'. The command itself doesn't have an option to let me do that (like -s in the 'free' command). So, is there a way to execute that or any other command every x seconds?

I thought about putting something like:
```
sensors >> somelog.txt
```
in crontab, and then use
```
tail -f somelog.txt
```
but there must be a way of doing it more easily (I guess).

Thanks in advance!

M.

---

### Post by tCarls on 2008-10-06
The simplest way would probably be either "watch -n30 sensors" or "while true; do clear; sensors; sleep 30; done".

---

### Post by martin_legion on 2008-10-07
> **tCarls said:**
> The simplest way would probably be either "watch -n30 sensors" or "while true; do clear; sensors; sleep 30; done".

Great! That's it.
Thank you!

---

