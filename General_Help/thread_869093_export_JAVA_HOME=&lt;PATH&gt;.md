---
title: "export JAVA_HOME=&lt;PATH&gt;"
date: 2008-07-24
forum: General Help
---

### Post by oohwewubi on 2008-07-24
How do I figure out <path>:confused:

---

### Post by andrewc6l on 2008-07-25
It depends which Java you have installed. If you have Sun Java 6 installed, it will be /usr/lib/jvm/java-6-sun/.

However, most Java implementations will run without JAVA_HOME set - are you sure you need it? (It will make your life harder if you decide to have multiple Java implementations installed.)

---

### Post by kpkeerthi on 2008-07-25
> **oohwewubi said:**
> How do I figure out <path>:confused:

Find where Java is using
```

which java

```

Now do a long listing of the output from the above command
For e.g.
```
ls -l /usr/bin/java
```

It will usually be symlinked to /usr/lib/<blah> or /opt/<blah>/<blah>

---

