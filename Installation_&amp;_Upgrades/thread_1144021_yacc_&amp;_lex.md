---
title: "yacc &amp; lex"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by vitaly87 on 2009-04-30
hello everyone,i am new in that area(ubuntu). i have ubuntu 9.04. i want to install lex and yacc how can i do that? i tried to write apt-get install bison flex but it isn't working.

---

### Post by mstpkr on 2009-05-27
even i have the same problem....as vitaly87...please help..

---

### Post by sedawk on 2009-05-27
First you need to "sudo" apt-get:
```

sudo apt-get install bison
sudo apt-get install flex

```

If you do not use sudo there will be an error message ("Could
not open lock file ...").
If it is already installed there will be a message "xyz is already
the newest version".

If you get another error post it here. If you do not get any error
try "aptitude search bison" or try to install with the GUI using
the "Synaptic Package Manager".

---

