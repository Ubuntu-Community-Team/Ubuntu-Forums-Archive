---
title: "failure running a .jar application in Ubuntu Hardy"
date: 2008-08-21
forum: General Help
---

### Post by hoangbv15 on 2008-08-21
I tried to run the application Multiclicker
which can be found here: [http://autoclickers.uni.cc/index.php/multiclicker/]("http://autoclickers.uni.cc/index.php/multiclicker/")

by entering "java -jar Multiclicker.jar" (without quotes)
but then it returned with this error message:
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

and nothing happened next.

Is there any suggestion? This app runs with no problem in Windows, and i'm totally new at Ubuntu.

---

### Post by EMCGFX on 2008-08-21
Looks like by updating your kernel solves this problem for some people.

---

### Post by hoangbv15 on 2008-08-23
well, i just figured out that the error message
> 
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

was not related to the Java Runtime Environment installed in Ubuntu, so stupid x.x
So it turned out to be like this: When i tried to open a .jar application by entering 
> java -jar Multiclicker.jar
nothing happened.
I must state that i installed Java Runtime Environment 6 into Ubuntu 8.04
And I heard that Updating the kernel is a pretty complicated work...

---

