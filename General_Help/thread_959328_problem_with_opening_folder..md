---
title: "problem with opening folder."
date: 2008-10-26
forum: General Help
---

### Post by enemy@network on 2008-10-26
Sometimes (1 out of 3 times) when i open the folder.It freezes for no
reason.It even don't closes.Only solution i have is it to restart my system.
Anyone out there know how to fix it please help me out...

---

### Post by ghost_ryder35 on 2008-10-26
i do not have the solution but restarting the computer is unnecessary.
run a terminal and issue
```

ps -ef | grep nautil

```
then kill it using the pid number (example number 3082)
```

kill 3083

```

---

### Post by enemy@network on 2008-10-29
I tried the code:
[COLOR="SeaGreen"]ram@nOObs:~$ ps -ef | grep nautil
ram       6289  6281  0 06:55 pts/0    00:00:00 grep nautil
ram@nOObs:~$ kill 6281
[/COLOR]
but still problem isnot solved and also the process is not killed because when i run the code again the process (6281) is still there.

---

