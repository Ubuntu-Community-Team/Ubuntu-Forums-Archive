---
title: "[SOLVED] [BASH] alias not working"
date: 2008-08-17
forum: General Help
---

### Post by British0zzy on 2008-08-17
In my bash profile I have this written:
```
PS1='|\u|\w \$ '
alias verbose='PS1=\"|\u|\w \$ \"'
alias concise='PS1=\"|\u|\W \$ \"'
```
For some reason, when I type these commands I get this error:
```
-bash: u: command not found
 1:17  up 6 days, 10:35, 2 users, load averages: 0.29 0.19 0.31
USER     TTY      FROM              LOGIN@  IDLE WHAT

```
Can anyone figure out why this isn't working?
Thanks.

---

### Post by bingoUV on 2008-08-17
```

alias verbose='PS1="|\u|\w \$ "'
alias concise='PS1="|\u|\W \$ "'

```

Why? Read [http://floyd-n-milan.blogspot.com/2006/11/bash-quoting.html](http://floyd-n-milan.blogspot.com/2006/11/bash-quoting.html)

---

