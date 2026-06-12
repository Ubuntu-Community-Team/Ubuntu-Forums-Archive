---
title: "how to output EVTEST result to a log txt?"
date: 2024-05-19
forum: Hardware
---

### Post by fox8171 on 2024-05-19
Hi there,
i'm using evtest to checking multitouch action. 
but it is diificult to looking detail in command line window.
how can i output the result to a log.txt?

thanks for help.

---

### Post by TheFu on 2024-05-19
Learn about file redirection. It is a basic Unix skill.  Output to the terminal can be either stdout or stderr.  These are 2 different output devices, so you may need only 1 of them or you might need both.  The commands are different.

Some references:
[LIST]
[*][https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)
[*][https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)
[/LIST]

Look for redirection is both references for examples.  There are times when we want to dump stdout completely and only forward stderr to an admin for action/consideration.
To get both stdout AND stderr:
```
some-command >logfile 2>&1 
```
or 
```
some-command &>logfile
```

These are bash specific.  Other shells might have different ways.

---

