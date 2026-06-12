---
title: "Terminal title?"
date: 2008-08-17
forum: General Help
---

### Post by Skofo on 2008-08-17
Hey guys,

I set up a launcher to run the command "telnet nethack.alt.org", which then runs a game in the terminal. Is there a way to extend that command to change the title of the terminal? Maybe even the icon? Thanks

---

### Post by TyrosCenva on 2008-09-04
Well, one thing you can do is expand it with this command:
```
export PROMPT_COMMAND='echo -ne "\033]0;Nethack@alt.org\007"'
```

so you'd get
```
export PROMPT_COMMAND='echo -ne "\033]0;Nethack@alt.org\007"' && telnet nethack.alt.org
```

I don't know of any way to make that shorter (except for putting the command in a script or alias..).

Changing the icon can probably only be done in the terminal emulator's settings, but maybe your emulator has a command for it, check it's man page. :)

---

