---
title: "command &quot;export&quot;"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by maltje on 2005-12-01
I need the command "export" to install vmware but I can't find it.
Not with synaptic and not with apt-get.
Can anyone help please?

---

### Post by wrtrdood on 2005-12-01
Uhmm... **export** is a Bash builtin command.  Since you don't say what you need it for, I assume this is the one you're talking about.  It's used to make shell environment variables available to child processes of that shell.

---

### Post by maltje on 2005-12-01
As i said,I need it to install vmware.
"export" CC=/usr/bin/gcc-3.4 gives an error 
 export: command not found

---

### Post by vyruss on 2005-12-05
[QUOTE=maltje]As i said,I need it to install vmware.
"export" CC=/usr/bin/gcc-3.4 gives an error 
 export: command not found[/QUOTE]

Well if you try typing it without the quotes, such as this:```
vyruss@gremlin:~$ export CC=/usr/bin/gcc-3.4
vyruss@gremlin:~$
```
you will see that it works:```

vyruss@gremlin:~$ set | grep CC
CC=/usr/bin/gcc-3.4
_=CC
vyruss@gremlin:~$

```
What possessed you to use quotes? :D

---

