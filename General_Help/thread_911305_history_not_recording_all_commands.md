---
title: "history not recording all commands"
date: 2008-09-05
forum: General Help
---

### Post by mike-g2 on 2008-09-05
Hello,

I'm experiencing annoying behavior w/my history file.  If I issue a command that starts with a space or a command that returns an error, it is not added to the history file.

eg. if I issue 

[INDENT]$ ls[/INDENT]
 it is added to my history file.

but if I issue
[INDENT]$  ls -ltrha[/INDENT]

it is not.

Or if I issue the command,

[INDENT]$ unknowncommand
[/INDENT]
it is not added either.



The only thing I have in my .bash_profile for history is the command
[INDENT]export HISTCONTROL=ignoreboth
[/INDENT]

I suspect this might somehow be 'standard' behavior, but its driving me nuts and would be interested to know if anyone else has similar behavior and a solution.

Many thanks.

Mike

---

### Post by jerome1232 on 2008-09-05
All seems to work for me my .bashrc contains

export HISTCONTROL=ignoredups
export HISTCONTROL=ignoreboth

```
511  unknowncommand
512  history | tail
513  man shanty
514  nslookup google.com
515  ping -c 4 64.233.167.99
516  vim /etc/resolv.conf
517  ls
518  ls -lah
519  unknown command
520  history | tail
```

---

### Post by Mister.Vash on 2008-09-05
For the issue with lines starting with spaces, change the
export HISTCONTROL=ignoreboth
to
export HISTCONTROL=ignoredups



ignorespace ignores lines that starts with a space and doesn't put that in the history
ignoredups doesn't put lines matches the previously issued command in history
ignoreboth sets both ignorespace and ignoredups

Not sure why the unknown command wouldn't show up in history unless it was preceded by a space?

---

### Post by mike-g2 on 2008-09-08
Dear Mr. Vash,

Thanks for the clarification b/w ignoreboth and ignoredups.

Given your explanation, it seems strange that the default .bash setting in Ubuntu would use both of these commands, since ignoreboth is redundant with the ignoredups.  

Thanks.

Mike

---

