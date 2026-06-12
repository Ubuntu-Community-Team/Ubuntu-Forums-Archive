---
title: "[SOLVED] changes in sudoers file take no effect"
date: 2008-11-03
forum: General Help
---

### Post by adieb on 2008-11-03
Hello,

I wanted to add permissions to myself to start a script that invokes a vpn connection without beeing asked to type in my password.

So i started visudo (my default editor is nano,so it came up with nano, but that should not be a problem).

No i added a line like:

```
%users ALL = NOPASSWD: /path/to/script
```

After saving the changes (STRG-O; STRG-X) the visudo-wrapper didn´t complain about any errors, but still I was asked fot my password.
So I tried different ways of telling sudoers-file what I want, like throgh User_Aliases, Cmnd_Aliases and whatever, 
I even rebooted.

No effect...

Any Ideas?


Thanks a lot

---

### Post by geirha on 2008-11-03
The order of the lines are important. It should be below the %admin-line, or else the %admin line will override your NOPASSWD-line. Also, if only you need to be able to run that command without password, use your username instead of %users.
```
...
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

*yourusername* ALL=NOPASSWD: /path/to/script
```

---

### Post by adieb on 2008-11-03
thanks a lot! so easy.... and all without annoying reboot or whatever....

---

