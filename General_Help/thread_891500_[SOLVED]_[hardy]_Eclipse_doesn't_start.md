---
title: "[SOLVED] [hardy] Eclipse doesn't start"
date: 2008-08-16
forum: General Help
---

### Post by svetylk0 on 2008-08-16
Hello,

I didn't have problems with this, till suddenly it came
in last few days.

I installed the common Eclipse package. When I run Eclipse in
terminal as normal user, I get this error message: 

> An error has occurred. See the log file
/home/hacx/workspace/.metadata/.log.


My version of JDK is:

```
hacx@localhost:~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
hacx@localhost:~$
```

**But, when I run it with sudo, it gets started well.**

Could be there some problems with permissions?

Thanks for help,

Regards, Tony B.

---

### Post by linux_tech on 2008-08-16
See these links 
How to install Eclipse in Ubuntu
[http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html)
[https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools)

---

### Post by svetylk0 on 2008-08-16
Oh man, I can't believe it :-) I had something wrong with my workspace directory :-) - that caused that problem. But thank You for Your reply :-)

I solved it by: 
1.) rename my workspace directory to e.g. workspace2
2.) run Eclipse [that created /home/hacx/workspace again]
3.) import all projects from workspace2 to workspace, and works! :-)

---

### Post by yurx cherio on 2010-10-20
I had a different scenario under which my eclipse stopped working.
I upgraded java. I am not sure what went wrong during the upgrade but it made my 32 bit java a primary alternative on the 64 bit system. Eclipse simply wouldn't start and quietly exit.

After I edited alternatives and made 64bit java a default eclipse came back to life like nothing happened.

I am assuming there may be many different causes for eclipse not to start. This is the scenario I had.

---

