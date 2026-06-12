---
title: "[SOLVED] creating shortcuts for command line commands"
date: 2008-11-29
forum: General Help
---

### Post by dckirba on 2008-11-29
Hello all,

Hope you are doing well. I've recently taken up running after my doctor told me I needed to lose 10 kilos if I didn't want to end up with diabetes in 5 years and I was looking for software to track my progress. A search of the forums came up with several alternatives and the best one for me was SportsTracker. It is a java program and I run it from the command line with the command:

```
java -jar SportsTracker.jar
```

I tried creating a shortcut in the applications menu and I entered

```
~/SportsTracker-3.5.0/java -jar SportsTracker.jar
```

However, this doesn't work and I get this error:

```
Failed to execute child process "/home/david/SportsTracker-3.5.0-bin/java -jar SportsTracker.jar" (No such file or directory)
```

How can I get this command to run with a click from the menu?

Thanks in advance for your help.

Have a great weekend,
Cheers,
David K

---

### Post by lswb on 2008-11-29
Just change it to

java -jar SportsTracker.jar

If that doesn't work try

/usr/bin/java -jar /home/david/SportsTracker.jar

---

### Post by binbash on 2008-11-29
you dont need /usr/bin just java -jar will do the trick.

---

### Post by dckirba on 2008-12-01
Thanks guys. I was making a silly mistake and placing the path to the jar file before the command instead of before the file. Thanks a lot for your help :)

---

