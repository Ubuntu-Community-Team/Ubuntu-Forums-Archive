---
title: "terminal"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by r0k on 2009-03-08
how do i run a program through a terminal?

---

### Post by r0k on 2009-03-08
or where is a good referance to linux commands?

---

### Post by taurus on 2009-03-08
Most of the time, you just type the name of the program that you want to run.

```
firefox
```

[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by Sorivenul on 2009-03-08
The advice above is correct.

Also, to learn about commands available on a related topic, such as networking, use the "apropos" command in the terminal, like:
```
apropos networking
```
This will return a list of manpages related to networking.

When you find a manpage (short for manual page) you are interested in looking at for more information about the specific command (i.e. "ifconfig"), use the "man" command to view it, like:
```
man ifconfig
```

Some manpages are more easy to understand than others, but after spending some time with them, you'll probably learn to understand them better and appreciate them more. 

Good luck! Cheers!

---

