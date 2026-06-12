---
title: "killing a PID in bash"
date: 2008-09-21
forum: General Help
---

### Post by linux8654 on 2008-09-21
I use sshfs, and to end my sshfs session I kill the PID associated with it.

```
 $ ps -aef | pgrep -n sshfs
21804
       $ kill 21804

```

I want to know if there is a way to find and  kill the process in one statement.  Maybe even have a script which will do this.

Thanks for any help.

---

### Post by boblemur on 2008-09-21
try:

```
kill `(ps -aef | pgrep -n sshfs)`
```

or if u dont mind killing all sshfs run killall

```
killall sshfs
```

---

### Post by pieoncar on 2008-09-21
Probably the command

```
kill `pidof sshfs`
```

would do what you need.

---

### Post by Yannick Le Saint kyncani on 2008-09-21
Or "pkill processname", would work too (along with pidof and killall).

---

### Post by linux8654 on 2008-09-21
Thanks for all of the help!

$ kill `(ps -aef | pgrep -n sshfs)`

This accomplished exactly what I wanted.

---

