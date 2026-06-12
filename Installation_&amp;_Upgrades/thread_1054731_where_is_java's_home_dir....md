---
title: "where is java's home dir?..."
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by zander1013 on 2009-01-30
hi,

how do i find the home dir of java on my machine?
i am using 8.10.
thank you,

zander

---

### Post by EnGorDiaz on 2009-01-30
goto home

and then
ctrl H

---

### Post by zander1013 on 2009-01-30
> **EnGorDiaz said:**
> goto home

and then
ctrl H

thank you; but i am not in a java environment. i would like to determine the path to the java 1.6 sdk installed on my machine.


please advise.

---

### Post by darco on 2009-01-30
type ```
whereis java
```

daro

---

### Post by zander1013 on 2009-01-30
> **darco said:**
> type ```
whereis java
```

daro

thank you darco...

:popcorn:

---

### Post by gtdaqua on 2009-01-30
```

$ whereis java
java: /usr/bin/java /etc/java /usr/share/java

```
That tells the command java resides in /usr/bin/java.

Dig again:

```

$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2009-01-15 18:34 /usr/bin/java -> /etc/alternatives/java

```
So, now we know that /usr/bin/java is actually a symbolic link to /etc/alternatives/java.

Dig deeper using the same method above:
```

$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 31 2009-01-15 18:34 /etc/alternatives/java -> /usr/local/jre1.6.0_07/bin/java

```

So, thats the actual location of java: /usr/local/jre.....
You could still dig deeper to find other symbolic links.

---

### Post by Coldhearth on 2009-05-11
Thx your post helped me out very good =)

---

