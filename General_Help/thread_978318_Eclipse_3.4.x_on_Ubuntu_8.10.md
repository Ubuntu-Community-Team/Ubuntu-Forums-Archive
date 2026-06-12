---
title: "Eclipse 3.4.x on Ubuntu 8.10"
date: 2008-11-11
forum: General Help
---

### Post by howardgao on 2008-11-11
I have an issue using Eclipse 3.4.x with Ubuntu 8.10.

After importing an existing project from Eclipse, I tried to find classes using Eclipse find utility. So I pressed ctrl-shift-T to bring up the open type dialog and input the name of the class for search. Right after the first char has been inputed the dialog pop up an error saying 'Dialog refresh' has encountered a problem. Checking on the .log it seems that an ArrayIndexOutOfBoundsException -1 from swt classes.

Is it a real problem or I have used something wrong?

---

### Post by thorsten.vitt on 2008-11-11
It's a bug, see: [https://bugs.eclipse.org/bugs/show_bug.cgi?id=240033](https://bugs.eclipse.org/bugs/show_bug.cgi?id=240033)

The problem does not occur if you turn the assistive technologies off (if this is an option for you).

---

### Post by howardgao on 2008-11-12
Thank you very much!

---

### Post by 7588 on 2008-11-16
I updated ubuntu in 9th November, this error was happened.
Then, I deleted all .* config directory => it's not happenning. U should try it. Good luck. :)

---

### Post by welsch.stefan on 2009-03-18
Hello, where can I find this .*config directory?

---

