---
title: "while starting apache i am getting error as &quot;Illegal Instruction&quot;"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by sathiyadasan on 2009-01-28
I have installed apache, and while trying to run it am getting error as Illegal Instruction.
the following print comes..
sathiya@sathiya:~/apache$ ./bin/apachectl start
Illegal instruction.

Wat to do. Please reply to this as soon as possible.

---

### Post by sathiyadasan on 2010-10-12
great response guys....

---

### Post by mikechant on 2010-10-12
> great response guys.... 

If you don't get a response in 24 hours it's acceptable to 'bump' the thread by posting to it yourself. If you don't do this, the thread will pretty much disappear (most people only look at the recent stuff) and you're unlikely to get a reply.

If you're still getting this problem and still interested in fixing it after all this time, one thing I have seen mentioned is that you should start apache with 'sudo', i.e. typically
```
sudo apachectl start
```

---

