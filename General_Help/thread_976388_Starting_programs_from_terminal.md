---
title: "Starting programs from terminal"
date: 2008-11-09
forum: General Help
---

### Post by entaroadun on 2008-11-09
Here is my problem i wanted to start some programs from terminal and I opend a terminal i typed " firefox & " and it told me " Error: no display specified

[3]-  Exit 1                  firefox" what must i do to be able to open programs from terminal?
Is the command i used wrong ?

---

### Post by fooman on 2008-11-09
did you try just "firefox" (no quotes of course)?

```
firefox
```

---

### Post by sdennie on 2008-11-09
If you are getting "no display" type errors when trying to open GUI apps from the terminal, it's likely you are running in a shell that doesn't have the DISPLAY variable set properly.  This can happen if you are logged in as root (with a login shell) or if you've done something to break $DISPLAY in ~/.bashrc.  The output of the following when you get the error might be able to determine the problem:

```

echo $USER $DISPLAY

```

---

