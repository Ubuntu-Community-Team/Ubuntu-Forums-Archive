---
title: "X includes problems"
date: 2005-11-25
forum: General Help
---

### Post by spyke01 on 2005-11-25
ive tried installing 2 programs now, and each one say cannot find X includes please check your installation, what does this mean?

---

### Post by kairu0 on 2005-11-25
I think that means you need to install the libx11-dev package.

---

### Post by spyke01 on 2005-11-25
hmm still not working, i installed some other libx dev packages too u.u

---

### Post by kairu0 on 2005-11-25
I assume that you are compiling a program using ./configure.

Read the end of the config.log file to see what file it couldn't find.

---

### Post by spyke01 on 2005-11-25
from what i can see, X11/Intrinsic.h

---

