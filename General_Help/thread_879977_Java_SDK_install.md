---
title: "Java SDK install"
date: 2008-08-04
forum: General Help
---

### Post by nelmo on 2008-08-04
Hi,

Downloaded Java SDK from the SUN website (choosing LINUX version?) and I've got a BIN file but I can't seem to install it.

When I try to, I get 'Couldn't display <nnn>.bin - there is no app installed for this file type'.

Any ideas?

---

### Post by squaregoldfish on 2008-08-04
In a terminal, make the file executable:
```

chmod u+x <nnn>.bin
```

then run it:

```
./<nnn>.bin
```

This will unpack the JDK into the current directory, then you can move it to wherever you want.

Steve.

---

### Post by tinny on 2008-08-05
Are you using Ubuntu Hardy???

If so...

Enable the "universe" and "multiverse" repositories.

[https://help.ubuntu.com/8.04/add-app...es-adding.html](https://help.ubuntu.com/8.04/add-app...es-adding.html)

then...

```

sudo apt-get update
sudo apt-get install sun-java6*

```

Sun Java 6 runtime and JDK, Done.

---

