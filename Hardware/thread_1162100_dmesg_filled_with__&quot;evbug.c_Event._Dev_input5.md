---
title: "dmesg filled with  &quot;evbug.c: Event. Dev: input5, Type: 0, Code: 0, Value: 0&quot;"
date: 2009-05-17
forum: Hardware
---

### Post by toutanc on 2009-05-17
Hi everyone ;)

My log are filled with info like:

output of dmesg:
```
[ 2836.722627] evbug.c: Event. Dev: input5, Type: 4, Code: 4, Value: 156
[ 2836.722638] evbug.c: Event. Dev: input5, Type: 1, Code: 96, Value: 0
[ 2836.722645] evbug.c: Event. Dev: input5, Type: 0, Code: 0, Value: 0
```

It's updating all the time: here's the tail of dmesg 2 seconds after the first one:
```
jeremy@sj51-ubuntu:~$ echo "1:" && dmesg | tail -n 5 && sleep 2 && echo "2:" && dmesg | tail -n 5
1:
[ 2956.753511] evbug.c: Event. Dev: input5, Type: 1, Code: 103, Value: 0
[ 2956.753516] evbug.c: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[ 2958.774982] evbug.c: Event. Dev: input5, Type: 4, Code: 4, Value: 156
[ 2958.774995] evbug.c: Event. Dev: input5, Type: 1, Code: 96, Value: 1
[ 2958.775000] evbug.c: Event. Dev: input5, Type: 0, Code: 0, Value: 0
2:
[ 2958.774995] evbug.c: Event. Dev: input5, Type: 1, Code: 96, Value: 1
[ 2958.775000] evbug.c: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[ 2958.859445] evbug.c: Event. Dev: input5, Type: 4, Code: 4, Value: 156
[ 2958.859457] evbug.c: Event. Dev: input5, Type: 1, Code: 96, Value: 0
[ 2958.859461] evbug.c: Event. Dev: input5, Type: 0, Code: 0, Value: 0
```

It seems to come for the input management but I can't find where the problem is. Any ideas?

I'm under jaunty gnome minimal (gnome-core + a few extras)

Thanks,

---

### Post by toutanc on 2009-05-19
OK,

I'll answer to myself in case someone has the same issue.
I just blacklisted the evbug module.

```
jeremy@sj51-ubuntu:~$ tail -n2 /etc/modprobe.d/blacklist.conf
#evbug
blacklist evbug
```

---

### Post by bishop__ on 2011-07-13
amazing, this problem was posted 2009 and yet still useful until now! :) your solution really works! 









[Preserved Thoughts]("http://www.rommellaranjo.com")

---

### Post by kakila on 2012-10-18
Happens again on 12.04

Related bug reports
[https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/240553](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/240553)

My blacklist.conf is empty.

---

