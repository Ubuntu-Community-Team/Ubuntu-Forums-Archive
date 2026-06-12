---
title: "the command top"
date: 2008-10-20
forum: General Help
---

### Post by pariksakurikar on 2008-10-20
hey!! well this is a question more related to linux than ubuntu....
here it is:

when i run the "top" command...in the first line...i get the output as such:

top - 22:45:67 up  9:58, 3 users, load average: 0.4 0.56 0.2

now in this line im unable to figure out what the users refer to and i know how to extract the uptime and the load averages...only the no of users is a problem...anyone with ideas??


thanks.

---

### Post by Comhra on 2008-10-20
One of the users is 'Root'

---

### Post by Dr Small on 2008-10-20
The number of users is the current number of users logged in. You can run the following command to see a list of their usernames logged in:
```
who
```

Dr Small

---

### Post by sisco311 on 2008-10-20
you can run:
```
users
``` to print the user names of users currently logged in.
```
w
``` shows who is logged on and what they are doing.

example:
```
sisco@acme:~$ w
 21:17:28 up 5 days,  2:35,  4 users,  load average: 0.39, 0.44, 0.44
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
sisco    tty7     :0               Wed19    0.00s  5:41   0.34s x-session-manag
sisco    pts/0    :0.0             Wed19    0.00s  9.20s  7:04m xfce4-terminal
sisco    pts/1    :0.0             Wed20   18:57   2.92s  2.92s bash
sisco    pts/2    :0.0             Wed20    3:57m  0.56s  0.56s bash
```

my x session is running on tty7 and my user is logged on in 3 terminals(pts/0. pts/1 ...).

---

### Post by pariksakurikar on 2008-10-20
well actually the problem is not in which code i must run....
im trying to implement the 'top' command myself and i need to
find out in which file this information about the users lies...
something in /proc or somethin....

thanks for the quick replies anyway...
any ideas about this???

---

