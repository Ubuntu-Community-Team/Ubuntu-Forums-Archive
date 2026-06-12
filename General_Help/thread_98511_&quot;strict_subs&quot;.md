---
title: "&quot;strict subs&quot;"
date: 2005-12-03
forum: General Help
---

### Post by WebDrake on 2005-12-03
Hello all,

In my code library I have a file called RAN.h.  Or at any rate it *was* called RAN.h when I was working under Windows; now it has lost the capital letters and is just ran.h.

I'd like to rename it to get back the capitals, but when I try (rename ran.h RAN.h) I get the message:

Bareword "ran" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "h" not allowed while "strict subs" in use at (eval 1) line 1.

What's wrong? :rolleyes: 

Many thanks,

     -- Joe

---

### Post by cgjones on 2005-12-03
Try this.

mv ran.h RAN.h

---

### Post by WebDrake on 2005-12-03
[QUOTE=cgjones]Try this.

mv ran.h RAN.h[/QUOTE]

I already tried that, and it didn't work ("File already exists") but moving it to another directory, then back, but with the change of name, did.  Thanks! :smile:

---

### Post by WebDrake on 2005-12-03
... however.... I'm having similar problems with a directory meant to be called RAN, but actually called ran.

mkdir RAN, for example, is converted to lowercase letters.

Anyway of fixing this?

---

