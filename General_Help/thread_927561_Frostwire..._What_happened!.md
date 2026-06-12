---
title: "Frostwire... What happened!?"
date: 2008-09-23
forum: General Help
---

### Post by Nider on 2008-09-23
Hi, I installed Frostwire sometime ago, but I didn't use it that often. I tried to use it today and when I click it, nothing happened.

So, I tried to uninstall it, but when I seems as it never exist or as I never install it. What can I do to uninstall it!? And what program can I use to replaced it!?

Thanks.

---

### Post by kokkus on 2008-09-23
Seams like you do not have JRE (Java runtime) installed.
But run it from terminal for safety to see which errors you get.
JRE can be downloaded from synatic.

---

### Post by ju2wheels on 2008-09-23
Here are instructions from another thread I posted to: [http://ubuntuforums.org/showthread.php?t=925961](http://ubuntuforums.org/showthread.php?t=925961)

---

### Post by Nider on 2008-09-23
Thanks guys...

This is what it show me

# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

Is this correct!?

---

### Post by Nider on 2008-09-23
Hi... now frostwire is open fine, but after it open, it ask me to update, which so far, I don't. But later, when I used the program, I did one search, but after that I could write in the search box. I tried to close and open the program and the problem persist. Any ideas!?

---

### Post by ju2wheels on 2008-09-23
You need to change your /etc/jvm so it looks like the one I posted in the thread I linked to above. Its missing a line for sun java 6 which should be the first line.

---

